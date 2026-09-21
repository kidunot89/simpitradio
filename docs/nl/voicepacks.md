# Stempakketten

De engineer klinkt alleen als een mens wanneer er opnames van een mens zijn. Een
stempakket is precies dat: een map met WAV-bestanden, één map per zin, die de
engineer afspeelt in plaats van via de Windows-synthesizer te spreken. In die
map kunnen meerdere opnames van dezelfde zin staan, en de engineer kiest er
willekeurig één uit, zodat dezelfde melding twee keer in een stint niet klinkt
als een machine die zichzelf herhaalt.

Alles wat hij zegt en niet in het pakket staat — je naam, een rondetijd, een
rijder van wie hij nog nooit gehoord heeft — wordt nog steeds door de
Windows-stem uitgesproken. Een pakket hoeft niet compleet te zijn om de moeite
waard te zijn.

## Drie manieren om er een te krijgen

**Een gepubliceerd pakket installeren.** *Instellingen → Stem* toont de pakketten
die voor download zijn gepubliceerd en installeert er een op verzoek, waarbij de
checksum wordt gecontroleerd voordat er iets wordt uitgepakt. Dit is de route
voor een andere taal dan de jouwe.

**Zelf opnemen**, in het venster. Dit is de route zonder plafond en degene waar
de app omheen is gebouwd: *Instellingen → Stem → Een stemmodel maken*.

**Een basis met Piper genereren**, offline, en de delen opnieuw opnemen die je
belangrijk vindt. Handig als je meteen iets correct en aangenaam wilt, of liever
geen 171 zinnen voorleest voordat je gaat rijden.

Ze sluiten elkaar niet uit. Een Piper-pakket is een gewoon pakket, dus elke zin
erin kan later worden vervangen door je eigen opname.

### Waarom geen voice cloning

Dat is eerst geprobeerd en losgelaten, en de reden is de moeite waard voordat je
ernaar op zoek gaat.

Voor dit project werd een gekloonde stem gemaakt uit bijna drie minuten schone
referentie-audio. Terug door de spraakherkenning van de app zelf kwam elke opname
van "five" terug als "bye", "four" als "boy" en "zero" als "yo".

De inventaris is de reden. **141 van de 171 zinnen zijn één of twee woorden**, en
korte tekst is precies waar een kloonmodel het slechtst is: XTTS genereert
autoregressief en bepaalt zelf wanneer het stopt, en bij een zin van twee woorden
beperkt vrijwel niets die beslissing. Piper is een model in VITS-stijl — één
doorgang van fonemen naar golfvorm, zonder samplinglus die kan afdwalen. Het kan
geen ander woord zeggen, en bij deze inventaris telt dat zwaarder dan klankkleur.

Crew Chief lost hetzelfde probleem op dezelfde manier op: zijn pakketten zijn
*opgenomen*, en zijn 11.176 rijdersnamen en 1.052 cijferclips zijn door een mens
ingelezen.

## Zelf opnemen

*Instellingen → Stem → Een stemmodel maken* opent een recorder: een zin om voor
te lezen, een aftelling, een opname, en het afspelen om die te controleren.

Het is minder werk dan het klinkt. De hele inventaris is **ongeveer veertig
minuten bij drie opnames per zin**, en het hervat — het kan dus in meerdere
sessies, en een pakket dat de helft van de zinnen dekt werkt vanaf het moment dat
je het opslaat.

Een paar dingen bepalen of het resultaat bruikbaar is:

- **Naast je mond**, een paar vingerbreedtes ervandaan, niet ervoor. Een
  headsetmicrofoon recht in de luchtstroom vervormt bij elke *p* en *b*, en
  vervorming is achteraf niet terug te draaien.
- **Een stille ruimte.** Een ventilator of een pc onder het bureau belandt in
  elke clip, en elke clip wordt je midden in een race via een koptelefoon
  voorgespeeld.
- **Constante afstand.** Ga niet heen en weer zitten tussen opnames. Clips op
  vier verschillende afstanden klinken als vier verschillende mensen.
- **Zet de microfoonversterking van Windows uit.** Dat is een compressor, en die
  trekt het ruisniveau tussen woorden omhoog.

Lees ze zoals een engineer ze over de radio zou zeggen — vlak, zonder haast,
licht verveeld. De engineer speelt geen rol.

## Een basis genereren met Piper

Piper draait offline, vanuit de packagingscripts en niet binnen de app. De
paden hieronder zijn relatief aan `apps/client` in een checkout van de
broncode:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Om met een bepaald model te bouwen:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Offline, en niet in de app, met opzet.** Piper is op een cpu snel genoeg om de
verleiding te wekken het op spreekmoment aan te roepen. Dat zou een model van
63 MB en een ONNX-runtime in een build stoppen waarvan de laatste vier kapotte
releases allemaal native afhankelijkheden waren die niet werden meegenomen. Een
pakket is een map met WAV's; het hier genereren kost de app niets en kan geen
build breken.

Het is niet *jouw* stem, en niets doet alsof. Het is een basis die correct en
aangenaam is, waarover elke zin in het venster opnieuw kan worden opgenomen.

**Japans heeft nog een pakket nodig en faalt er verwarrend zonder.** Het
Japanse model vraagt Piper om `pyopenjtalk` om tekst in fonemen om te zetten,
en zonder dat levert elke zin helemaal geen audio op — gemeld als
`wave.Error: # channels not specified`, wat het lege uitvoerbestand is en niet
de echte oorzaak. Het oorspronkelijke `pyopenjtalk` publiceert alleen broncode
en wil CMake en een C++-compiler; `pyopenjtalk-plus` is een fork die wheels
publiceert onder dezelfde importnaam, en staat in het requirements-bestand
hierboven.

## Hoe een pakket eruitziet

Een pakket is een map met daarin een submap `voice`, en daarbinnen weer één map
per zin met de opnames erin. Dat is de indeling die `crew-chief-autovoicepack`
schrijft, dus **een Crew Chief-pakket past er zo in**. De buitenste map staat
apart zodat een pakket een licentie en zijn bronopnames kan meedragen zonder
dat die voor zinnen worden aangezien.

```
voices/
  Norman/
    voice/
      pitradio/
        go_ahead/
          1.wav
          2.wav
        box_this_lap/
          1.wav
        ...
```

De map waarin een WAV-bestand staat is de zin, dus de diepte tussen `voice` en
die map maakt niet uit. De recorder schrijft `pitradio/`; Crew Chief schrijft
een map per categorie. Beide worden op dezelfde manier gelezen.

Alleen WAV. Het is wat elke generator uitspuugt, wat de standaardbibliotheek
leest, en het vraagt geen decoder in een build die al vecht met native
afhankelijkheden.

Bestandsnamen komen uit de zin, in kleine letters, met leestekens **weggelaten**
in plaats van vervangen — zo zijn "that's enough" en "thats enough" dezelfde clip.
Een apostrof in een scheidingsteken veranderen zou `that_s_enough` opleveren, en
een pakket dat tegen één van beide spellingen is opgenomen zou de andere stilletjes
missen.

## Waar pakketten wonen

**Instellingen → Stem** is waar ze allemaal staan: wat geïnstalleerd is, wat
meegeleverd is en wat te downloaden valt. Pakketten wonen naast je configuratie,
in `voices/`, niet onder de installatiemap — een update vervangt die map in zijn
geheel, en een pakket is een hoop audio die je daar zelf hebt neergezet.
**Instellingen → Stem → Map met stempakketten openen** opent hem.

Zet er een map in, open het tabblad opnieuw, en hij verschijnt in de keuzelijst.

## De zinnenlijst

**Instellingen → Stem → Zinnenlijst schrijven** exporteert elke zin die de
engineer kan zeggen, als CSV, in de eigen taal van de engineer — want een pakket
wordt opgenomen in de taal waarin het gesproken zal worden.

Hij wordt uit de app gegenereerd in plaats van met de hand bijgehouden, dus hij
kan niet afwijken van wat de engineer werkelijk zegt. Gebruik hem als je buiten
de app opneemt, of als je zelf een generator schrijft.

## Er komt niets uit

**Controleer of er een pakket geselecteerd is.** *Engineer → Stem → Stem* moet
naar het pakket wijzen en niet naar *(geen pakket)*.

**Controleer het uitvoerapparaat.** *Audio → Uitvoer* zou je koptelefoon moeten
zijn — dezelfde die je voor voicechat gebruikt, niet de uitvoer van de sim.

**Een ontbrekende zin is geen storing.** Alles wat niet in het pakket staat valt
terug op de Windows-stem, dus een half opgenomen pakket klinkt als twee mensen in
plaats van te falen. Dat is opzet: het is precies wat een pakket bruikbaar maakt
voordat het af is.
