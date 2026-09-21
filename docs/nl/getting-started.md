# Aan de slag

Installeren, vertellen naar welke toets geluisterd moet worden, en iets zeggen.
Al het andere op deze pagina's is optioneel.

![Het SimPitRadio-venster op het tabblad Status](images/window.png)

## Installeren

Download het installatieprogramma van de
[releasespagina](https://github.com/kidunot89/simpitradio/releases/latest) en voer
het uit. Windows waarschuwt je: de builds zijn niet ondertekend, dus SmartScreen
toont "Uw pc is beveiligd door Windows" en je moet **Meer informatie → Toch
uitvoeren** kiezen. Zo ziet een niet-ondertekend installatieprogramma eruit, en
ondertekenen kost geld dat dit project niet uitgeeft.

De installatie stelt één vraag — **welke taal** — met je Windows-taal al
geselecteerd. Daarmee liggen drie dingen tegelijk vast: het venster, de
spraakherkenning en de taal waarin de race-engineer spreekt en luistert. Je kunt
dat later wijzigen op het tabblad Taal.

**Het installeert als administrator, met opzet.** Windows gooit geïnjecteerde
toetsaanslagen weg die gericht zijn op een programma met meer rechten dan de
afzender, en sims draaien vaak verhoogd. Zonder dit lijkt alles te werken en
bereikt er nooit iets het spel.

### De eerste start downloadt twee dingen

Er zit niets groots in het installatieprogramma, dus de eerste keer dat je het
opent wordt gevraagd om op te halen:

- **het spraakmodel**, ongeveer 250 MB, dat je stem in tekst omzet
- **een opgenomen stem** voor de engineer, ongeveer 45 MB, als er een in jouw
  taal is gepubliceerd

Beide eenmalig. Het model staat buiten de installatiemap, zodat een update het
nooit opnieuw kost. Zeg je "niet nu", dan doen de tabbladen Taal en Instellingen
hetzelfde wanneer je maar wilt.

De portable zip heeft geen installatieprogramma en dus ook geen taalvraag — die
stelt hem in plaats daarvan bij de eerste start.

## Kies een toets

**Instellingen → Trigger.** Druk op *Druk op een toets…* en dan op de toets die
je wilt.

![Het gedeelte Trigger op het tabblad Instellingen](images/trigger.png)

De toets wordt **onderweg opgeslokt**, dus het spel ziet hem nooit — je kunt er
dus een gebruiken die het spel al gebruikt. `F13` is de standaard omdat de
meeste toetsenborden er geen hebben en niets anders ernaar luistert.

**Een stuurknop werkt net zo goed.** Druk op de regel **Stuurknop** op *Druk op
een knop…* en druk dan op de knop die je wilt. SimPitRadio opent het stuur
zonder het van het spel af te pakken, dus de sim blijft elke knop lezen,
inclusief die ene. Houd hem ingedrukt om te praten, precies zoals bij de toets.
Beide staan tegelijk scherp, dus je kunt allebei koppelen en gebruiken wat het
dichtst bij de hand ligt.

De andere weg is de software van je stuur zelf, of
[JoyToKey](https://joytokey.net/): zet `F13` op een knop en koppel `F13` hier.
Grijp hiernaar als je stuur al met software draait die je vertrouwt, of als
SimPitRadio het apparaat niet kan openen.

## Stel je microfoon in

**Audio → Microfoon.** Kies de ingang, houd de trigger vast en kijk naar de
niveaubalk — die toont het signaal *na* versterking, dus wat het spraakmodel
werkelijk krijgt. Mik op pieken rond driekwart.

![Het tabblad Audio](images/audio.png)

**De uitvoer moet niet het apparaat van je sim zijn.** De engineer, de coach en
de opnametoon spelen allemaal hier af; richt je hem op dezelfde uitvoer als het
spel, dan komt de piep in de opname terecht.

Druk op **4 s opnemen en transcriberen** om te horen wat er verstaan is. Tijdens
een test wordt nergens iets getypt.

## Zeg iets

Houd de toets vast, zeg wat je wilt zeggen, laat los.

1. De toets wordt opgeslokt.
2. De opname begint **meteen** — vóór de chatbox opengaat, zodat er niets van de
   eerste paar honderd milliseconden verloren gaat.
3. De chattoetsen openen de chatbox van het spel.
4. Bij het loslaten gaat de clip naar het spraakmodel, op je eigen processor.
5. De tekst wordt ingetypt en de verzendtoetsen worden gegeven.

Het tabblad Status laat zien waarop de hook scherp staat en wanneer de trigger
voor het laatst is gezien. Wordt *Laatste trigger* nooit bijgewerkt, dan ligt het
aan de toets of de hook, niet aan de transcriptie.

![De statuskaart](images/status.png)

## En dan, als je meer wilt

De engineer, de coach en voicechat staan allemaal uit tot je ze aanzet.

| | |
| --- | --- |
| [Tekstchat](text-chat.md) | Het dicteren zelf: profielen, nalezen vóór verzenden, wat te doen als er niets getypt wordt |
| [De engineer](engineer.md) | Een stem met een naam die je rondetijden voorleest, auto's naast je meldt en vragen beantwoordt |
| [De coach](coaching.md) | Jouw lijn naast die van een rivaal na elke bocht, met wat je moet veranderen |
| [Stem op de radio](voice-chat.md) | De andere rijders in je sessie horen, en alleen wie dichtbij is |
| [Stempakketten](voicepacks.md) | De stem van de engineer opnemen of installeren |

## Als er iets mis is

**Kijk eerst op het tabblad Status.** Dat is de ene plek die laat zien wat de app
gelooft: de scherpe toets, het programma met focus, het gebruikte profiel en een
live logboek.

![Het logboek op het tabblad Status](images/log.png)

- **Er wordt niets getypt** — zie [Er wordt niets getypt](text-chat.md#er-wordt-niets-getypt).
- **Er wordt niets gezegd** — zie [Er wordt niets gezegd](engineer.md#er-wordt-niets-gezegd).
- **Er wordt niets getekend** — zie [Er wordt niets getekend](coaching.md#er-wordt-niets-getekend).

Het logboek wordt ook naar een bestand geschreven. **Status → Logmap openen**
brengt je erheen, en het is het eerste wat de moeite waard is om aan een melding
toe te voegen.
