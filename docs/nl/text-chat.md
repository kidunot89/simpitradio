# Tekstchat

Waarvoor SimPitRadio gebouwd is. Houd een toets vast, zeg wat je wilt zeggen,
laat los — en het verschijnt getypt in de chatbox van het spel, zonder dat je
handen het stuur verlaten.

Al het andere in de app is hieruit gegroeid. De engineer, de coach en de
spraakchat delen dezelfde toets en dezelfde opname; tekstchat is wat er met de
woorden gebeurt wanneer niets anders ze heeft opgeëist.

## Wat er gebeurt terwijl je de toets vasthoudt

1. **De toets wordt opgeslokt.** Het spel ziet de trigger nooit, dus het mag een
   toets zijn die het spel zelf ook gebruikt.
2. **De opname begint meteen** — vóór de chatbox opengaat, niet erna. Openen
   duurt een paar honderd milliseconden, en alles wat in die tijd gezegd wordt
   zou anders verloren gaan.
3. **De chattoetsen worden gegeven** om de chatbox van het spel te openen, en de
   app wacht `pre_delay_ms` tot die de focus heeft.
4. **Je laat los.** De opname stopt en de clip gaat naar Whisper, op je eigen
   processor.
5. **De tekst wordt ingetypt**, daarna worden de verzendtoetsen gegeven.

Blijken de woorden een opdracht voor de engineer of de coach te zijn, dan worden
ze in plaats daarvan beantwoord en wordt er niets getypt. Die beslissing is
bewust smal — zie [Ertegen praten](engineer.md#tegen-hem-praten) — want dezelfde
toets stuurt berichten naar iedereen in je sessie, en een opdracht die de app
verzint is een bericht dat stilletjes nooit aankomt.

## Uitzetten

**Tekstchat → Naar het spel sturen** is de schakelaar waar je middenin een race
naar grijpt wanneer een sessie openbaar wordt. Uit wordt de trigger alleen nog
stem en engineer: geen chattoetsen, geen getyp, niets verzonden.

Er is een tweede schakelaar per spel, onder Profielen. "Heeft dit spel een
chatbox" is een feit over het spel en geen beslissing die je elke sessie neemt —
Assetto Corsa offline heeft geen chat om te openen, dus elke druk stuurde een
Enter het spel in die daar iets anders betekende. Eén keer instellen en vergeten.
De app-brede schakelaar wint nog steeds: daar uit is overal uit.

## Een bericht nakijken voordat het weggaat

Standaard wordt het bericht verzonden zodra het getypt is. Whisper verstaat
dingen verkeerd, en in een openbare sessie is een fout ieders probleem — daarom
heeft elk profiel een schakelaar **Automatisch verzenden**.

Staat die uit, dan wordt het bericht in de chatbox getypt en daar gelaten. Je
trigger beslist dan wat ermee gebeurt, zonder het stuur los te laten:

| Gebaar | Wat het doet |
| --- | --- |
| **Tik** | Verzenden |
| **Twee tikken** | Wissen |
| **Vasthouden** | Wissen en opnieuw opnemen |

Het tabblad Status toont **wacht op verzenden** zolang er een bericht staat.

Heb je knoppen over, dan koppelt **Instellingen → Trigger** ook toetsen
rechtstreeks aan *Wachtend bericht verzenden* en *Wachtend bericht wissen*. Die
werken meteen, zonder dubbeltikvenster om af te wachten, en bestaan naast de
gebaren in plaats van ze te vervangen.

**Op een tik kan niet meteen gehandeld worden**, want tot het dubbeltikvenster
sluit kan het de eerste helft van een dubbeltik zijn. Die wachttijd is
`review.double_tap_ms`, ongeveer een derde seconde. Zet hem op `0` in de
configuratie om meteen te verzenden en wissen met dubbeltik op te geven.
`review.tap_ms` is de grens tussen een tik en vasthouden.

**Een druk terwijl er een bericht wacht start meteen de opname**, voordat bekend
is of het een tik of vasthouden wordt. Wachten tot dat duidelijk is zou de eerste
woorden van een nieuwe opname opslokken; de buffer wordt weggegooid als het toch
een tik blijkt.

## Profielen

Welk profiel geldt wordt bepaald door het programma met focus, dus meerdere sims
kunnen tegelijk ingesteld staan en de juiste wordt zonder vragen gebruikt.

De instelling die het meest uitmaakt is **Vertraging chat openen**
(`pre_delay_ms`). De chatbox heeft een paar frames nodig om open te gaan en de
focus te pakken, en te vroeg typen kost de eerste tekens. Begin bij 350 ms en
verhoog hem als berichten afgekapt aankomen.

| Instelling | Waar het voor is |
| --- | --- |
| **Vertraging chat openen** | Hoe lang na het openen van de chatbox gewacht wordt voor er getypt wordt. Degene om te verhogen bij afgekapte berichten |
| **Chat-openen-toetsen** | Wat de chatbox opent. Enter bij de meeste sims |
| **Verzendtoetsen** | Wat het verstuurt. Meestal weer Enter |
| **Annuleertoetsen** | Wat de box sluit zonder te verzenden, om een wachtend bericht te wissen |
| **Toets vasthouden** | Hoe lang elke toets wordt vastgehouden. Spellen lezen invoer één keer per frame, dus een druk korter dan een frame is een druk die het spel nooit ziet |
| **Typvertraging** | De tussenruimte tussen tekens |
| **Maximum aantal tekens** | Langere berichten worden afgekapt. De meeste sims hebben een eigen limiet |
| **Automatisch verzenden** | Uit om na te kijken voor verzenden — zie hierboven |
| **Sessieplug-in** | Leest wie er in de sessie zit zodat namen goed getranscribeerd worden en vermeldingen worden. Laat op *automatisch* |

### Unicode of scancodes

**Typmodus** bepaalt hoe tekens het spel bereiken. *Unicode* stuurt het teken
zelf en kan overweg met elke toetsenbordindeling en elk alfabet. Sommige spellen
negeren dat omdat ze in plaats daarvan hardware-scancodes lezen; schakel voor die
spellen over op *scancode*, dat typt alsof de toetsen fysiek zijn ingedrukt.

Scancodes zijn beperkt tot wat een Amerikaans toetsenbord kan voortbrengen, dus
tekens met accenten en niet-Latijnse alfabetten overleven het niet. Probeer eerst
unicode; de instelling bestaat omdat "het spel negeert wat wij typen" een
configuratiewijziging moest zijn en geen codewijziging.

De twee hebben ook een andere timing, en juist daarom zijn het aparte modi.
Scancodetoetsen worden `key_hold_ms` vastgehouden omdat spellen invoer één keer
per frame lezen. Getypte tekst niet — die gaat via de berichtenwachtrij, en 40 ms
per teken zou een bericht van 200 tekens acht seconden laten duren.

## Namen en woordenlijst

Whisper transcribeert wat het hoort, en rijdersnamen zijn precies waar het het
slechtst in is. De sessieplug-in leest wie er werkelijk in je sessie zit en voert
die namen aan, zodat "Estre" er als "Estre" uitkomt en niet als "Ester".

**Woordenlijst** voegt daar je eigen woorden aan toe: sponsornamen, een
teamnaam, hoe de handles van je vrienden echt gespeld worden. Alles wat je jezelf
ziet corrigeren is het toevoegen waard.

## Er wordt niets getypt

**Kijk eerst op het tabblad Status.** Het laat zien waarop de hook nu scherp
staat en wanneer de trigger voor het laatst is gezien. Wordt *Laatste trigger*
nooit bijgewerkt, dan ligt het aan de toets of de hook, niet aan de transcriptie.

**Het moet als administrator draaien.** Windows gooit geïnjecteerde invoer weg
die gericht is op een proces met een hoger integriteitsniveau dan de afzender, en
sims draaien vaak verhoogd. De geïnstalleerde build vraagt daar vanzelf om.

**Controleer of het profiel klopt.** Het tabblad Status logt de naam van het
programma met focus; staat die niet bij je profielen, dan wordt het
standaardprofiel gebruikt en kloppen de chattoetsen daarvan misschien niet voor
dat spel.

**Controleer de vertraging voor chat openen.** Berichten die zonder hun eerste
tekens aankomen zijn elke keer een te lage `pre_delay_ms`.

**Controleer of het spel unicode niet negeert.** Gaat de chatbox open en
verschijnt er niets in, probeer dan typmodus *scancode*.
