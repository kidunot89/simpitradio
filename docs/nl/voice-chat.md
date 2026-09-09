# Stem op de radio

SimPitRadio typt wat je zei in de chatbox van het spel. Dit voegt de andere helft toe:
de mensen tegen wie je racet sturen je ook de *audio*, en je hoort die.

Het is met opzet geen Discord. Discord bestaat al, werkt, en iedereen zit er al in. Wat
Discord niet kan, is je in een ruimte zetten met **wie er ook maar in deze sessie zit**,
zonder dat vooraf te regelen, en degenen die vier kilometer verderop zitten stil te
houden.

## Wat er reist

**De push-to-talk-clip, bij het loslaten. Geen livestream.**

De triggercyclus neemt al een clip op terwijl de toets vastgehouden wordt en geeft die
bij het loslaten aan Whisper. Spraak hergebruikt precies die clip: bij het loslaten gaat
hij naar Whisper *en* naar het relay, en de anderen spelen hem af. Aan het opnamepad
verandert niets.

Een livestream zou een andere toepassing zijn. Die heeft frames van 20 ms nodig, een
jitterbuffer, een mixer en een afspeelklok, allemaal op het audiopad, en de beloning is
dat mensen je 1,5 seconde eerder horen. De clip is toch al wat een pitradio is: je houdt
de knop vast, je zegt iets, het komt aan.

Het gevolg dat de moeite waard is om te weten: **een clip is atomair.** Hij kan niet
onderbroken worden, hij komt heel aan of helemaal niet, en twee mensen die tegelijk
praten leveren twee clips op die in de rij gaan staan in plaats van door elkaar te
praten. Dat is beter dan een race, niet slechter.

## Wie het hoort

Het relay is dom. Het verspreidt een clip naar iedereen in de ruimte en beslist niet wie
hem zou moeten krijgen, want dat kan het niet — het heeft geen idee waar iemand op de
baan is, en het die informatie geven zou erger dan nutteloos zijn.

**Nabijheid wordt bepaald op de machine van de luisteraar.** Het gedeelde geheugen van
LMU draagt de wereldpositie van *elke* auto, niet alleen die van jou, dus elke client
weet al precies hoe ver elke andere rijder weg is. Er wordt nooit iets over posities aan
het relay gepubliceerd, en de functie werkt zelfs als de beheerder van het relay
vijandig is.

**Het beeld van de luisteraar over waar de spreker is, wint.** Een clip komt aan nadat de
spreker gestopt is, dus de positie die hij meedraagt is een seconde of twee oud — op
racesnelheid honderd meter, wat tegen een straal van 200 m de uitkomst bepaalt. Het
scoringsblok bevat elke auto zoals die *nu* is, en de vraag is wie er dicht bij de
doelauto is wanneer het bericht wordt afgespeeld.

De clip draagt de positie van de spreker toch mee, als terugval voor iemand die het blok
van de luisteraar nog niet heeft ingehaald: een rijder die net is binnengekomen, of van
wie de vermelding verdwenen is. Een verouderde positie is beter dan geen.

De lokale kijk verkiezen betekent ook dat een clip zich niet langs het filter kan praten.
Een client die beweert naast je te zitten terwijl hij een kilometer verderop is, wordt
gewoon gemeten waar hij werkelijk is. Dat is een gevolg van het gebruik van het verse
getal, geen beveiligingsmechanisme — een spreker die niemand kan plaatsen is nog steeds
hoorbaar, want stilte die niemand kan verklaren is de ergere storing.

`proximity_only` op de LMU-plug-in zet dit aan; `proximity_metres` stelt de straal in.
Uit hoor je de hele sessie, en dat is wat je wilt bij trainingen en op een formatieronde.

### Toekijken

Nabijheid hoort gemeten te worden vanaf de auto op het scherm: een gevecht volgen waar je
middenin zit, terwijl je de radio hoort vanaf vier kilometer verderop waar je eigen auto
geparkeerd staat, is nabijheid in geen enkele betekenis die een kijker zou herkennen.

Het moet **gedetecteerd** worden. Wie rijdt kan geen keuzelijst bereiken, en wie toekijkt
zou dat niet hoeven.

**Het gedeelde geheugenblok zegt het niet**, en drie plausibele bronnen zijn tegen een
live bekeken sessie getoetst en afgevallen — elk ziet er juist uit, en geen is het:

- `telemetry.playerVehicleIdx` is het voertuig van de *speler*. Terwijl er naar iemand
  anders werd gekeken, bleef het wijzen naar de geparkeerde auto van de kijker.
- `appInfo.mOptionsLocation` las de hele tijd 0.
- `$rFactor2SMMP_Graphics$` wordt gepubliceerd en zou zowel een camerapositie als het id
  van de bekeken plek dragen — maar LMU vult het nooit. De buffer bestaat volledig uit
  nullen op de versieteller na, omdat het spel de grafische callback niet aanroept
  waaruit de rF2-plug-in hem vult. Het naastgelegen Extended-blok was op datzelfde moment
  wél levend, dus dit is een keuze van LMU en geen kapotte installatie.

**LMU's eigen HTTP-API zegt het wél.** `http://127.0.0.1:6397/rest/watch/standings` is
wat de eigen overlays van het spel lezen, en elke vermelding draagt `hasFocus` — gezet op
de auto die bekeken wordt, onderscheiden van `player`, dat op die van jou blijft. De
`slotID` ervan is hetzelfde getal als `mID` in het gedeelde geheugen, dus de twee sluiten
direct op elkaar aan. Het hoort bij het spel en niet bij een plug-in, dus er hoeft niets
geïnstalleerd te worden.

Gelezen met een korte time-out en een seconde gecachet: dit draait op de triggercyclus,
het antwoord is ~16 KB, en een dicteerapp mag nooit wachten op een spel dat midden in het
laden zit. **Mislukkingen worden ook gecachet** — anders kost een gesloten spel bij elke
druk een time-out.

Elke mislukking levert None op, en `SessionInfo.listener()` valt dan terug op de gereden
auto en uiteindelijk op None, wat `audible` als hoorbaar leest. Stilzwijgend een
geparkeerde auto als referentie aanhouden zou de sessie filteren op een plek waar niemand
kijkt, en geen luisteraar zou dat kunnen onderscheiden van een kapotte functie.

**"Nabijheid" betekent op de baan en nergens anders.** Het zijn meters tussen twee auto's
in het spel, gelezen uit de sim, lokaal berekend. Het heeft niets te maken met waar
iemand woont, en er wordt geen fysieke locatie gelezen, afgeleid of verzonden. Het
*hosten* van relays hieronder heeft het ook over afstand, in netwerkzin — dat is een
routeringsvraag over servers en staat los van wie je kunt horen.

## Welke ruimte

Het sessie-id wordt afgeleid, nooit aangekondigd:

    sha256("pitradio/1:{mServerPublicIP}:{mServerPort}")[:32]

Iedereen op dezelfde spelserver berekent hetzelfde id zonder dat iemand publiceert welke
server dat is — het relay leert een hash en verder niets. Offline en singleplayer hebben
geen server, dus leveren geen id en geen ruimte op, en dat is het juiste gedrag, geen
speciaal geval.

Het circuit staat bewust *niet* in de sleutel. Het wisselt tussen sessies op dezelfde
server, en een ruimte die uiteenvalt zodra het evenement naar het volgende circuit gaat
is een slechtere ruimte.

Identiteit binnen een ruimte is de rijdersnaam uit het scoringsblok. `mSteamID` is in de
praktijk nul, dus er is niets beters beschikbaar.

## Het relay

**De code en configuratie van het relay staan niet in deze repository.** SimPitRadio is
openbaar; de server, de Terraform en de Ansible ervan zijn privé, samen met het
OAuth-clientgeheim dat ze nodig hebben. Terraform en Ansible bestaan daar voor één taak:
reproduceerbaar, vanaf een schoon image, een **door een racer geleverde** spraakhost
opzetten.

Het adres van het basisrelay staat evenmin in deze repository. Het wordt **tijdens de
build** in [endpoints.py](../src/pitradio/endpoints.py) geschreven, dus een checkout — of
een fork — heeft helemaal geen adres en spraak is simpelweg niet beschikbaar. Dat is een
werkende toestand, geen kapotte: beter dan dat elke kloon van de broncode een microfoon
richt op een server waarvan de eigenaar nooit heeft ingestemd hem te dragen.

Niets anders in de app mag een adres vastleggen. Eén plek om te overschrijven, één plek om
te kijken wanneer het fout is.

    wss://<relay>/chat/{sessie-id}

Eén WebSocket per client, TLS, clips als binaire frames met een kleine kop. Dat is het
hele protocol. TLS omdat een relay de machine van een vreemde is en audio van jouw stem
die niet in het klaar zou moeten oversteken; WebSocket omdat het elke NAT en
bedrijfsfirewall overleeft waar rauwe UDP op stukloopt, en omdat de audiobandbreedte voor
twintig racers die af en toe een knop indrukken niets voorstelt.

**Niet letterlijk peer-to-peer.** Echt P2P heeft ICE, STUN en een TURN-terugval nodig — en
TURN ís een relay, dus het terugvalpad is sowieso dit ontwerp, bereikt na het binnenhalen
van een WebRTC-stack in een Nuitka-build die al vecht met native afhankelijkheden. Het
relay is één klein kastje, en het is er eerlijk over er een te zijn.

### Hosts uit de gemeenschap

Relays bestaan om *dicht bij de sprekers* te zijn. Een grid uit drie continenten dat via
één kastje in Frankfurt loopt betaalt bij elke clip twee keer de Atlantische Oceaan; een
relay dat voor de groep gekozen is niet. Dat is de hele reden dat racers kunnen hosten:
niet kosten, en niet decentralisatie om zichzelf — geografie.

Terraform maakt de machine; Ansible installeert het relay, de systemd-unit en het
TLS-certificaat, zodat een host reproduceerbaar is vanaf een schoon Ubuntu-image zonder
handmatige stappen.

Eerst DigitalOcean OAuth, want dat is wat er vandaag bestaat. Linode heeft een echte
OAuth-app-flow en kan volgen. **AWS kan niet**: het heeft geen consumenten-OAuth voor
provisioning — het zijn IAM-sleutels of Identity Center SSO — dus het heeft een eigen pad
nodig en het is geen kwestie van een knop toevoegen.

#### Er een kiezen is een groepsbeslissing, geen persoonlijke

**Elke client in een sessie moet hetzelfde relay kiezen, of ze kiezen er geen.** Aan
zichzelf overgelaten zou elk de host kiezen die het dichtst bij *zichzelf* is, wat voor
een transatlantisch grid twee relays betekent, twee ruimtes, en beide helften van de
sessie in iets dat er precies uitziet als een werkende functie met verder niemand erin.
Dat is dezelfde stille storing als een niet-overeenkomende sessiesleutel, langs een andere
weg bereikt.

Dus is er één coördinator, op de vaste basishost, en die beslist:

1. Clients komen de ruimte binnen op het in de build ingestelde relay en melden hun
   gemeten heen-en-weertijd naar elk kandidaat-relay.
2. De coördinator kiest het relay met het beste slechtste geval over de hele ruimte — het
   minimaliseert de latentie van de *traagste* racer, niet het gemiddelde, want het gaat
   erom dat niemand gestrand is.
3. Hij zegt iedereen te migreren, en ze verbinden daar samen opnieuw.

De basishost is ook het terugvalrelay, en dat is wat dit betaalbaar maakt: de coördinator
moet toch altijd aan staan, dus kan hij net zo goed de audio dragen voor sessies die te
klein of te lokaal zijn om te verplaatsen.

#### Waarom niet alle hosts aan elkaar knopen

Het voor de hand liggende alternatief: elke client laten verbinden met het relay dat het
dichtst bij *hem* ligt, en de relays clips naar elkaar laten doorsturen. Het is een echt
ontwerp — Mumble koppelt servers zo — en het is op één punt werkelijk eleganter, want het
schrapt de groepsbeslissing hierboven. Er valt niets af te spreken als de ruimte alle
relays omspant, dus de gesplitste-ruimtestoring kan helemaal niet optreden.

Het is hier toch de verkeerde ruil, om één reden: **wij sturen clips, geen livestream.**
Een clip wordt verstuurd nadat de spreker gestopt is, dus het verschil tussen 90 ms en
250 ms routering is niets wat iemand kan waarnemen — en dat is het grootste deel van het
argument voor geografie, en het hele argument om twee extra hops te betalen om het te
verbeteren.

Wat bruggen kost zijn geen hops, het is toestand. Relays zouden lidmaatschap van ruimtes
moeten uitwisselen, elkaar authenticeren en zich wapenen tegen lussen en dubbele
aflevering, en een door een racer gehost relay dat zich bij dat weefsel voegt kan verkeer
zien van ruimtes waarin het geen leden heeft. Dat is een project over gedistribueerde
systemen, vastgeschroefd aan de zijkant van een dicteerapp, ten dienste van een
latentiebudget dat dit ontwerp niet heeft.

Als SimPitRadio ooit wél live gaat streamen, keert dit om en wordt bruggen het juiste
antwoord. De vorm om dan te bouwen: een volledige mesh met een gedeeld geheim,
ruimtelidmaatschap dat rondverteld wordt, en elke clip met een id en een limiet van **één
hop** tussen relays — geen transitief doorsturen, wat routeringslussen meteen doodt en de
fan-out begrenst in plaats van erop te vertrouwen.

#### Als een host verdwijnt

Een relay dat verdwijnt mag het gesprek niet beëindigen. De coördinator houdt de ruimte
vast, merkt dat het relay niet meer antwoordt, doet de keuze opnieuw over wat er over is
en migreert de resterende racers — hetzelfde mechanisme als de eerste keuze, dus er is geen
apart failoverpad dat fout kan gaan. Clients houden de verbinding met de coördinator open
precies hierom: dat is wat overleeft.

Een racer die de sessie verlaat neemt zijn relay niet middenin de race mee. Zijn machine is
niet het relay — een droplet die hij heeft aangemaakt is dat — en dat onder de voeten
vandaan trekken van wie nog rijdt zou het slechtst denkbare moment zijn.

#### Als de sessie eindigt

Ruimtes worden afgebroken, niet doorlopend gelaten. LMU meldt zijn spelfase, dus een client
die de sessie ziet eindigen zegt dat; wanneer de laatste client weggaat, of de ruimte
langer stil blijft dan een inactiviteitstime-out, sluit de coördinator hem. Een relay
zonder overgebleven ruimtes is een kandidaat voor `terraform destroy`, en dat is het
verschil tussen dat dit een racer een paar centen per evenement kost of hem voor altijd
een droplet kost.

De inactiviteitstime-out telt net zo zwaar als het uitdrukkelijke signaal. Een client die
crasht, wegklikt in het niets of zijn netwerk kwijtraakt stuurt nooit iets — er mag dus
niets afhangen van dat hij dat doet.

## Toestemming

Spraak staat **uit tot je hem aanzet**, per profiel, en het venster zegt wie je kan horen
voordat het iets anders zegt. Een dicteerapp die stilletjes de microfoon zou openen voor
twintig vreemden zou verraad zijn, hoe goed de functie ook is.

Alleen push-to-talk. Er is geen open-microfoonmodus en die zou er niet moeten zijn: de
toets is de toestemming.
