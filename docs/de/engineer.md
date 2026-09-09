# Der Ingenieur

Eine Stimme mit Namen, die die Simulation beobachtet und mit Ihnen spricht: Ihre
Rundenzeiten, Autos daneben, und Antworten, wenn Sie etwas fragen.

Sie teilt sich die Sprechtaste mit allem anderen, was SimPitRadio tut. Auslöser
halten, „Chief, target P3“ sagen, loslassen — und statt in die Chatbox zu gehen,
antwortet der Ingenieur.

**Er ist aus, bis Sie ihn einschalten.** Es wird nichts gesprochen, bevor Sie in
Einstellungen → Ingenieur das Häkchen gesetzt haben.

---

## Schnellstart

1. Öffnen Sie **Einstellungen → Ingenieur** und setzen Sie **Ingenieur an**.
2. Wählen Sie einen der vier Ingenieure. Das legt Namen, Stimme und Redemenge
   fest.
3. Drücken Sie **Test**. Sie sollten hören, wie er seinen Namen zurücksagt.
4. Stellen Sie das **Ausgabegerät** auf Ihr Headset — dasselbe, das Sie für den
   Sprachchat nutzen, nicht die Ausgabe der Simulation.
5. Fahren Sie. Er liest Ihre Rundenzeit an der Linie vor.
6. Halten Sie den Auslöser und sagen Sie **„Chief, target P3“**, um den
   Kurven-Coach gegen den Dritten zu starten.

Wenn Test nichts sagt, siehe [Es wird nichts gesprochen](#es-wird-nichts-gesprochen)
unten.

---

## Mit ihm sprechen

Es gibt zwei Wege, wie ein Satz zu einem Befehl wird, und beide sind bewusst eng.
Dieselbe Taste schickt Nachrichten an alle in Ihrer Session, also ist ein Befehl,
den der Ingenieur *erfindet*, eine Nachricht, die stillschweigend nie ankommt.

**Sagen Sie zuerst seinen Namen.** „Chief, target P3.“ Der Name kommt zuerst, die
Wendung direkt danach. `hey`, `ok` und `right` sind vor dem Namen erlaubt.

**Oder sagen Sie eine Wendung für sich** — aber nur Wendungen, die keinen Fahrer
mitnehmen. „initiate corner coaching“ funktioniert ohne irgendetwas davor.
„target Verstappen“ nicht, denn „target“ könnte einen gewöhnlichen Satz beginnen
und sein Argument hat kein Ende: *„target time is a twenty three“* würde sonst
ganz verschluckt und erreichte die Chatbox nie.

Nur den Namen zu sagen bringt „go ahead“, wie es ein echtes Funkgerät täte — und
hält ein verirrtes „Chief“ aus einer Nachricht an zwanzig andere heraus.

**„Stop“** funktioniert immer, was auch läuft und was es auch gestartet hat.
Ebenso „stand down“, „cancel“, „that's enough“ und „forget it“.

Alles, was der Ingenieur nicht erkennt, ist eine Nachricht und geht genau wie
vorher in die Chatbox.

---

## Einen Ingenieur wählen

Vier kommen mit der App:

| | Stimme | Stil |
| --- | --- | --- |
| **Chief** | männlich | Ruhig und vollständig. „Kurve vier, Tandy war am Ausgang schneller, zwei Zehntel.“ |
| **Ada** | weiblich | Knapp. Lässt die Kurvennummer weg: „Tandy, schnellerer Ausgang, zwei Zehntel.“ |
| **Marshall** | männlich | Langsamer und fülliger, falls die anderen gehetzt wirken. |
| **Vic** | weiblich | Schnell und kurz. Redet von den vieren am wenigsten. |

Sie sind **Voreinstellungen, keine Aufnahmen** — ein Name, eine bevorzugte
Windows-Stimme, ein Tempo und wie viel gesagt wird. Das ist es wert, klar
gesagt zu werden, denn „vier Stimmen“ heißt sonst vier Audio-Sammlungen: ein
erzeugtes Sprachpaket ist ein bis zwei Gigabyte, und vier auszuliefern wäre ein
Acht-Gigabyte-Download, um etwas zu ersetzen, das auf jeder Windows-Maschine
schon kostenlos vorhanden ist.

Jeder wählt die beste installierte Windows-Sprachstimme, die zu seiner Vorliebe
und Ihrer Sprache passt. Auf einer Standardinstallation von Windows 11 gibt es
meist zwei oder drei, also können sich zwei Ingenieure eine Stimme teilen und
sich in Tempo und Formulierung unterscheiden. Wenn Sie eine bestimmte wollen,
setzen Sie **Windows-Stimme**, und sie überschreibt die Voreinstellung.

**Angesprochen als** ist das, worauf er hört. Setzen Sie es auf irgendetwas — der
Name wird nur zum Ansprechen verwendet, und „Bob, target P3“ funktioniert genauso
gut.

---

## Was er Ihnen sagt

### Rundenzeiten

Liest Ihre Runde vor, während Sie die Linie überqueren, und sagt, wenn es Ihre
beste war. Standardmäßig an.

### Spotter

Meldet Autos daneben: „car left“, „car right“, „cars both sides“, dann „clear“,
sobald sie weg sind. Standardmäßig aus, und es gibt eine Sache, die man dazu
wissen muss.

**Welche Seite welche ist, ließ sich ohne Auto auf einer Strecke nicht
überprüfen.** Die Positionen kommen aus den Weltkoordinaten der Simulation, und
ob die Rechnung links oder rechts ergibt, hängt von einer Händigkeitskonvention
ab, die dieses Projekt von einer Entwicklungsmaschine aus nicht prüfen konnte.
Wenn er also „links“ für ein Auto rechts von Ihnen ruft, schalten Sie
**Spotter-Seiten tauschen** in Profile → Plugin-Einstellungen des Spiels ein. Ein
Häkchen, einmalig.

Alles andere am Spotter ist exakt: Er nutzt spielinterne Positionen, er lässt die
Höhe weg (damit eine Brücke oder die Esses von Le Mans niemanden an Ihre Tür
setzt) und er meldet keine Autos auf einer benachbarten Gerade.

### Schaden

Sagt, was kaputt ist und ob man dafür hereinkommen soll. Standardmäßig an, und es
braucht eine Simulation, die den Zustand des Autos veröffentlicht — heute ist das
Le Mans Ultimate.

> *Sie haben Karosserie verloren. Diese Runde an die Box.*

**Gesagt, wenn es sich ändert, nicht solange es andauert.** Wer eine verbeulte
linke Hinterseite eine halbe Stunde mit sich herumfährt, muss nicht jede Runde
daran erinnert werden, also wird gesprochen, wenn es schlimmer wird, und danach
geschwiegen. Jeder Teil der Auslesung wird beobachtet, nicht nur der schlimmste —
dass ein zweites Teil von einem bereits verbeulten Auto abgeht, ist eine
Nachricht, auch wenn sich die Schwere nicht bewegt hat.

**Was er sagt, ist wo, dann ob.** Sie wissen schon, dass Sie etwas getroffen
haben; was Sie vom Sitz aus nicht sehen können, ist, wie schlimm es ist und ob
Zeit für eine Reparatur bleibt. Also nennt er den Ort — die Nase, das Heck, die
linke Seite entlang — und gibt dann eine von drei Antworten:

| | |
| --- | --- |
| **Diese Runde an die Box** | Das Auto kann nicht gefahren, nur hereingebracht werden: ein hängendes Teil, ein Platten, ein fehlendes Rad oder eine gebrochene Nase. Wie viel Zeit bleibt, ändert daran nichts — die Alternative ist eine schwarze Flagge oder eine Mauer |
| **An die Box, wenn es geht** | Lohnt sich zu reparieren. Immer im Training und Qualifying, wo ein Stopp nichts kostet und der Sinn des Draußenseins ein funktionierendes Auto ist |
| **Draußen bleiben, wir leben damit** | Ein Rennen, von dem weniger als ein Fünftel übrig ist. Drei Runden vor Schluss fahren Sie besser ein kaputtes Auto zur Flagge, als eine Minute abzugeben |

Leichter Schaden bekommt die erste Hälfte und gar keinen Rat. Für ein
verschrammtes Heckviertel gegen einen Stopp abwägen zu sollen, ist schlimmer, als
nichts gesagt zu bekommen.

Er spricht nie über den Coach. Schaden ist dringend — man will wissen, dass der
Flügel weg ist, vor der nächsten Kurve und nicht danach —, aber eine Kritik, um
die Sie gebeten haben, ist es nicht wert, für ein Auto unterbrochen zu werden,
das in vier Sekunden immer noch kaputt sein wird. Der Spotter ist die einzige
Ansage, die über irgendetwas spricht.

---

## Wen er beobachtet

Der Ingenieur behält einen **Fokus**: einen Fahrer, an dem er Sie misst. Sie
müssen ihn nicht setzen. Standardmäßig ist es **das Auto vor Ihnen in Ihrer
Klasse**, oder das Auto dahinter, wenn Sie sie anführen — weil es niemanden zu
jagen gibt und die Frage wird, ob Sie sie dort halten.

Er folgt einem Wechsel erst, wenn die Position **acht Sekunden gehalten** hat.
Positionen kochen: Bei einem echten Rennstart gemessen waren fünfzehn
verschiedene Fahrer innerhalb von neunzig Sekunden das Auto davor, und jeder
Wechsel warf die gesammelten Runden weg, sodass er nie genug hatte, um überhaupt
etwas zu sagen.

Sagen Sie es, wenn Sie jemand anderen wollen:

- `focus on {Fahrer}` — oder „keep an eye on“, „keep tabs on“, „study“, „watch“
- `default focus` — zurück zum Selberwählen
- `stop focusing` — aus, und es bleibt aus, bis wieder darum gebeten wird

Ein von Ihnen genannter Fahrer wird nie überstimmt. Zwei Kurven später zu dem
zurückzuwandern, der gerade vorn ist, wäre die App, die Ihnen widerspricht.

Der Reiter Status zeigt, wer beobachtet wird, und `what are we watching` fragt
danach.

---

## Ihn etwas fragen

Jede Frage hat ein Feld mit Wendungen in Einstellungen → Ingenieur, eine pro
Zeile, und was Sie tippen ersetzt die Standardwerte. Jede lässt sich abschalten;
eine abgeschaltete Frage steuert überhaupt keine Wendungen bei, ihre Worte
erreichen also die Chatbox wie alle anderen, statt genommen und mit nichts
beantwortet zu werden.

- **Ihr Auto** — `what's my best lap`, `how are the tyres`, `what's the damage`,
  `how's the fuel`, `how much fuel do I need to finish the race when I pit on
  the next lap`
- **Die Session** — `who has the fastest lap`, `who's fastest`,
  `who has the fastest sector`, `who's in the lead`, `who's ahead`
- **Wo die Zeit bleibt** — `where am I slower`, `where am I faster`, beides auch
  mit `than {Fahrer}` am Ende

**Fragen überholen die Warteschlange.** Eine Frage, die gestellt wurde, während
der Ingenieur mitten in einer Ansage war, wartete früher dahinter oder fiel ganz
weg — die Schlange fasst sechs, und eine geschäftige Runde füllt sie — Sie
fragten also, hörten ihn über etwas anderes reden und bekamen keine Antwort. Eine
Antwort räumt jetzt den gewöhnlichen Verkehr, unterbricht das Gesagte und kann
nicht hinausgedrängt werden. Sie weicht weiterhin dem Spotter, denn ein Auto
daneben handelt davon, nicht zu crashen.

**Eine Frage, die er nicht beantworten kann, bleibt aus der Chatbox.** „Who's
faster?“ ist keine Wendung, die er kennt, und früher fiel das durch und ging an
die Session hinaus. Alles, was sich wie eine Frage liest — es endet mit einem
Fragezeichen oder beginnt mit einem Fragewort — wird stattdessen mit „say again“
beantwortet. Auf dem Reiter Textchat gibt es ein Häkchen, wenn Ihnen das alte
Verhalten lieber ist, und eine Frage, die Sie ausdrücklich abgeschaltet haben,
erreicht weiterhin den Chat, denn sie abzuschalten ist die Art zu sagen, dass
diese Worte Ihnen gehören.

Sie können den Namen des Ingenieurs an beide Enden setzen: „Bono, how are the
tyres“ und „how are the tyres, Bono“ funktionieren beide. Das Komma ist es, was
ihn als Namen markiert, also fokussiert `focus on Bono` weiterhin auf einen
Fahrer namens Bono.

### Wo bin ich langsamer

Die eine, die man kennen sollte. Sie vergleicht Sie mit Ihrem Fokus **Kurve für
Kurve, gemittelt über jede Runde dieser Session**, statt sie von einer
abzulesen — eine einzelne Runde sagt, was auf dieser Runde passierte, und die
Frage geht darum, was immer wieder passiert.

> Chief, where am I slower
>
> *Kurve drei, Sie sind beim Einlenken langsamer, zwei Zehntel.*
>
> *Kurve sieben, sie haben den besseren Ausgang, ein Zehntel.*

Sie sagt *wie*, nicht nur wo: Eingang, Ausgang, später gebremst oder langsamer
durch die ganze Kurve. Wo es einen Kurvenkatalog für die Strecke gibt, benutzt
sie den Namen — „Eau Rouge“ statt „Kurve drei“.

**Wie sie Kurven findet.** Es gibt keine Streckenkarte und es wird auch keine
geben — das bräuchte eine Datei je Strecke, würde mit jeder Layoutänderung
veralten und würde auf den vier Strecken funktionieren, zu denen jemand gekommen
ist. Eine Kurve ist ein Ort, an dem die Referenzrunde langsamer wurde und wieder
beschleunigte, und das gilt auf jeder Strecke in jeder Simulation. Schikanen
zählen als eine Kurve.

**Sie beschreibt, sie weist nicht an.** „Sie haben den besseren Ausgang“ ist,
was die App weiß. Sie weiß nicht, ob das Linie, Reifen oder Windschatten war, und
„brems später“ wäre eine Vermutung in Coaching-Kleidung.

**Wenn Runden fehlen, sagt sie wessen.** Ihre oder deren — sonst lässt „keine
Runden zum Vergleichen“ Sie raten, welche.

### Was sie nicht als Referenz nimmt

- Eine Runde mit irgendeinem Teil in der Boxengasse. Eine schnelle Runde, die in
  Wahrheit eine Abkürzung durch die Box war, würde sonst zum Ziel, an dem alle
  gemessen werden, und nichts daran sähe falsch aus.
- Eine Runde, in die Sie mittendrin eingestiegen sind.
- Eine Runde, für die die Simulation keine Zeit gab — eine Auslaufrunde oder ein
  gerade angekommenes Auto.
- Alles von einer anderen Strecke. Ein Streckenwechsel löscht alles.

Sie bleibt auch still, während Sie zuschauen. Eine Runde zu kommentieren, die Sie
sehen statt fahren, wäre Unsinn.

---

## Wenn Ihre Simulation nicht antworten kann

Nicht jede Simulation veröffentlicht dasselbe, und der Ingenieur sagt es, statt
zu raten. Das ursprüngliche Assetto Corsa etwa veröffentlicht **Ihr eigenes Auto
und nichts über irgendwen sonst** — keinen Namen, keine Position, keine
Rundenzeit eines anderen Fahrers — also hat alles, was Sie mit dem Feld
vergleicht, auf keinem Weg Daten.

Fragen Sie dort „who's leading“, antwortet er **„dieses Spiel sagt es nicht“**.
Das ist Absicht und nicht dasselbe wie „niemanden zu beobachten“, was heißt, dass
das Feld wirklich leer ist. Einem Fahrer auf Platz sieben zu sagen, es sei
niemand vor ihm, ist keine unnütze Antwort, sondern eine falsche.

Verhaltensweisen, die Daten brauchen, die Ihre Simulation nicht liefert, werden
mit einer Zeile im Log übersprungen, statt eingeschaltet und stumm gelassen zu
werden:

```
Spotter is on but this sim does not publish positions or spotter; it will stay quiet
```

`--telemetry` gibt aus, was Ihre Simulation tatsächlich sendet — siehe den
letzten Abschnitt.

---

## Andere Sprachen

Der Ingenieur spricht die Sprache, die Sie für die **Transkription** gesetzt
haben, außer Sie legen ihn auf dem Reiter Ingenieur fest. Das ist die richtige
Vorgabe und keine willkürliche: Ihre Befehle kommen durch Whisper, wenn Whisper
also Spanisch produziert, wird ein Ingenieur, der auf englische Wendungen hört,
nie eine einzige hören.

Alles, was er sagt — einschließlich der Auslösewendungen —, geht durch dieselben
Übersetzungskataloge wie das Fenster. Eine Sprache hinzuzufügen ist eine
JSON-Datei in `src/pitradio/locale/`; siehe die Haupt-README.

**Zahlen werden auf Englisch ausgeschrieben und überall sonst als Ziffern
gelesen.** Nicht Faulheit: Zahlengrammatik ist wirklich sprachabhängig — Deutsch
dreht Zehner und Einer um, Spanisch verschmilzt die Zwanziger — und eine halb
fertige Umsetzung produzierte selbstbewussten Unsinn in jemandes eigener Sprache.
Ziffern geben das Problem an die Sprachstimme dieser Sprache weiter, die es
bereits richtig löst. Der Nebeneffekt ist, dass ein nicht-englisches Sprachpaket
Zahlen nicht abdecken kann und sie synthetisiert herauskommen.

---

## Sprachpakete

**Aus welchem Paket dieser Ingenieur spricht, wird hier gesetzt, auf dem Reiter
Ingenieur**, und der Coach wählt sein eigenes auf dem Reiter Coaching — die
beiden sind getrennte Aufgaben, und ein Fahrer kann vernünftigerweise hören
wollen, welcher von beiden spricht.

**Installieren, Aufnehmen und Entfernen von Paketen ist Einstellungen →
Stimme.** Ein Paket ist etwas, das die Anwendung hält; aus welchem eine Persona
spricht, ist eine Einstellung an dieser Persona.

Zwei Pakete kommen mit: **Norman** und **Claudia**. Beide wurden mit Piper
erzeugt — siehe [voicepacks.md](voicepacks.md) — und jedes lässt sich durch ein
eigenes ersetzen.

Ein Sprachpaket ersetzt den Synthesizer durch aufgenommenes Audio: ein Ordner mit
WAV-Dateien, ein Ordner je Satz, mehrere Aufnahmen davon. Der Ingenieur wählt
zufällig eine, und das ist der größte Teil davon, warum ein Paket wie ein Mensch
klingt und Text-to-Speech nicht.

**Das Layout ist das von Crew Chief**, mit Absicht:

```
%APPDATA%\pitradio\voices\
  Ada\
    voice\
      corners\
        two_tenths\
          a.wav
          b.wav
```

Ein flaches `<Paket>/<Satz>/*.wav` geht auch, und das bekommen Sie, wenn Sie
selbst aufnehmen.

Dieses Layout bedeutet, dass ein von
[crew-chief-autovoicepack](https://github.com/cktlco/crew-chief-autovoicepack)
erzeugtes Paket direkt eingelegt werden kann. Um eines für SimPitRadios Sätze
statt für die von Crew Chief zu erzeugen:

1. Einstellungen → **Stimme** → **Satzliste schreiben**. Das schreibt
   `phrase_inventory.csv` in den Stimmenordner, in der Sprache des Ingenieurs.
2. Geben Sie dieses Inventar dem Generator anstelle seines eigenen.
3. Legen Sie den Ausgabeordner unter `voices\` und wählen Sie ihn auf dem Reiter
   Ingenieur (oder nutzen Sie **Einstellungen → Stimme → Sprachpaket-Ordner
   öffnen**, um hinzukommen).

**Namen und Zahlen sind nie in einem Paket** und werden immer von der
Windows-Stimme gesprochen. Es führt kein Weg daran vorbei — kein Paket kann jeden
Fahrernamen oder jede Rundenzeit halten —, also ist eine Ansage wie „Kurve vier,
Tandy war am Ausgang schneller“ teils aufgenommen und teils synthetisiert. Diese
Naht ist hörbar. Es ist trotzdem der richtige Handel: Die Alternative ist ein
Paket, das in dem Moment ungenutzt bleibt, in dem ein Fahrer genannt wird, und
das sind die meisten Ansagen.

Pakete werden neben Ihrer Konfiguration abgelegt, nicht im
Installationsverzeichnis, damit ein Update kein Gigabyte Audio löscht, das Sie
installieren wollten.

---

## Wie es zusammenpasst

Der Ingenieur läuft auf **einem eigenen Thread**, getrennt von den vier, die
SimPitRadio schon hat, und das Sprechen bekommt einen Thread darunter. Keiner
kann den Tastatur-Hook, den Worker oder das Fenster aufhalten.

Alles, was er tut, darf fehlschlagen. Dass der Ingenieur verstummt, darf Sie
niemals einen Auslöser, eine Transkription oder eine Nachricht in der Chatbox
kosten — wenn also hier drin etwas kaputtgeht, gehen die Worte wie immer in die
Chatbox und das Problem ist eine Zeile im Log.

Er liest die Simulation zehnmal pro Sekunde durch dasselbe Plugin, das die
Fahrernamen für Erwähnungen liefert. Es gibt keinen zweiten Datenpfad und keine
zusätzliche Verbindung zum Spiel.

---

## Es wird nichts gesprochen

**Test tut nichts.** Der Synthesizer läuft in einem PowerShell-Host über
`System.Speech`, das Teil des .NET Framework auf jeder Windows-10- und
-11-Maschine ist. Prüfen Sie das Log auf `no speech host` — eine gesperrte
Maschine mit blockiertem PowerShell ist die übliche Ursache.

**Sie hören ihn, aber nicht im Headset.** Setzen Sie das Ausgabegerät auf dem
Reiter Audio. Es steht standardmäßig auf dem Systemstandard, was während eines
Rennens oft der Lautsprecher des Lenkrads ist.

**Er liest Rundenzeiten, coacht aber nie.** Der Kurven-Coach braucht eine
Referenzrunde. Bis der Fahrer, den Sie anvisiert haben, eine beendet hat —
sauber, nicht durch die Box —, gibt es nichts zu vergleichen. Die Statuszeile des
Reiters Ingenieur sagt, wie viele Kurven er kartiert hat.

**Er coacht, sagt aber an manchen Kurven nichts.** Das ist das Design: Diese
Kurven lagen innerhalb der Schwelle. Senken Sie **Kurvenschwelle**, wenn Sie mehr
wollen.

**Er hört auf nichts, was Sie sagen.** Prüfen Sie den Namen auf dem Reiter
Ingenieur, und denken Sie daran, dass jede Wendung, die einen Fahrer mitnimmt,
den Namen davor braucht. Sagen Sie „Chief“ für sich — wenn Sie „go ahead“
bekommen, hört er zu und die Wendung ist das Problem.

**Er hat eine Nachricht gefressen.** Sollte er nicht. Wenn der Ingenieur etwas
genommen hat, das Sie senden wollten, sagt die Logzeile `that was for the
engineer` samt dem, was er getroffen hat — bitte öffnen Sie ein Issue mit dieser
Zeile, denn ein zu eifriger Matcher ist der eine Fehler in dieser Funktion, der
wirklich etwas kostet.

---

## Prüfen, was Ihre Simulation tatsächlich sendet

Die meisten „der Ingenieur sagt nichts“-Probleme sind nicht der Ingenieur.
Starten Sie das Spiel, kommen Sie **auf die Strecke und in Bewegung**, dann:

```bash
python -m pitradio --telemetry
```

Es gibt jedes Auto so aus, wie der Ingenieur es sieht — Rundendistanz,
Geschwindigkeit, Rundenzahl, Sektor, Rundenzeiten, Boxen-Flag, Weltposition —
und, nützlicher noch, es vergleicht aufeinanderfolgende Lesungen und sagt Ihnen,
ob sich etwas ändert.

Dieser letzte Teil zählt mehr, als er klingt. Eine pausierte oder in einem Menü
sitzende Simulation veröffentlicht weiter einen Block, der völlig gesund
aussieht: Autos, Positionen, Geschwindigkeiten, alles plausibel. Nichts bewegt
sich, also hat der Ingenieur nichts zu sagen, und keine einzelne Momentaufnahme
zeigt das. Wenn es meldet

> Nothing changed across 4 reads, including the sim's own clock.

dann ist das Spiel pausiert, in einem Menü oder die Session ist beendet — nicht
kaputt.

Worauf man achtet, wenn es *läuft*:

| Spalte | Speist |
| --- | --- |
| `lapdist`, `speed` | Kurvenerkennung und wo die Zeit bleibt |
| `lap`, `last lap`, `best lap` | Rundenzeit- und Schnellste-Runde-Ansagen |
| `sec` — wechselt dreimal pro Runde | jede Sektoransage |
| `world x/y/z` — je Auto verschieden | den Spotter |

Die Zeile `provides:` oben sagt, welche davon das Plugin zu liefern behauptet.
Eine Verhaltensweise, die etwas Fehlendes braucht, wird übersprungen, statt
eingeschaltet und stumm gelassen zu werden, und das Log sagt, welche Fähigkeit
fehlt.

## Was jede Simulation kann

Simulationen veröffentlichen sehr Unterschiedliches, und eine Verhaltensweise,
deren Daten fehlen, wird **mit einer Zeile im Log übersprungen**, statt
eingeschaltet und stumm gelassen zu werden.

| | Le Mans Ultimate | iRacing | Assetto Corsa / Competizione / Evo | Automobilista 2, Project CARS 2 / 3 |
| --- | --- | --- | --- | --- |
| Rundenzeiten | ja | ja | ja | abgeleitet |
| Neue schnellste Runde | ja | ja | — | ja |
| Sektoransagen | ja | — | ja | — |
| Wo bin ich langsamer | jeder Fahrer | jeder Fahrer | Ihre eigene beste | jeder Fahrer |
| Wer ist vorn / führt | ja | ja | — | ja |
| Spotter | Geometrie | die eigene Ansage der Simulation | nur Competizione | Geometrie |
| Fahrererwähnungen, „P3“ | ja | ja | — | ja |
| Schaden | ja | — | — | — |
| Coaching und das Abschnittsdiagramm | ja | — | — | — |

Die Lücken sind die Spiele, nicht die App:

- **iRacing** veröffentlicht keine Sektorzeiten je Auto, Sektoransagen haben also
  nichts, womit sie arbeiten könnten. Sein Spotter ist der beste von allen —
  `CarLeftRight` kommt von den echten Fahrzeugkörpern, es braucht also keine
  Tausch-Einstellung und keine Breitenschätzung.
- **Assetto Corsa** veröffentlicht Rundenzeiten nur für Ihr Auto und überhaupt
  keine Fahrernamen. Darum gibt es keine Wertung und keine Erwähnungen, und darum
  jagt „wo bin ich langsamer“ Ihre eigene beste Runde — wofür eine
  Trainingssession ohnehin da ist.

  Das ursprüngliche Spiel geht weiter: Es veröffentlicht **überhaupt kein anderes
  Auto**, nicht einmal eine Position. Gegen ein laufendes Rennen mit acht Autos
  geprüft, hielt das Koordinatenarray den Spieler in Slot null und unberührten
  Speicher in jedem anderen — Nullen, ein NaN, ein Denormal. Also hat der Spotter
  auch dort nichts, womit er arbeiten könnte, und das Plugin sagt das je Session
  statt je Spiel: **Competizione veröffentlicht** das Array, und dasselbe Plugin
  meldet dafür Positionen.
- **Automobilista 2 und Project CARS** führen in dem Teil ihres Blocks, dem man
  trauen kann, Runden*zählungen* statt Rundenzeiten, also werden Rundenzeiten
  hier mit einer Stoppuhr gemessen. Eine Runde, die eine Pause überspannt, kommt
  länger heraus, als sie war; das versagt sicher, denn eine aufgeblähte Runde
  wird nie die Referenz, der ein Vergleich nachjagt. Ihr Sektorfeld ist ein Enum,
  das sich von außerhalb der Spiele nicht festnageln ließ, also werden
  Sektoransagen nicht angeboten.

Automobilista 2 hat einen eigenen Eintrag, statt sich den von Project CARS zu
teilen, damit Sie das Spiel wählen können, das Sie tatsächlich fahren, und damit
die beiden getrennte Spotter- und Näheeinstellungen behalten.

**Le Mans Ultimate ist das einzige, das gegen das laufende Spiel überprüft
wurde.** Jeder andere Leser wird gegen von Hand gebauten Shared Memory getestet,
was eine falsche Feldbreite, einen falsch dekodierten Namen oder einen
Padding-Fehler fängt — und keine falsche Annahme darüber fangen kann, was die
Simulation wohin legt. Führen Sie `--telemetry` mit dem Spiel auf der Strecke
aus, bevor Sie einem davon trauen, und besonders Assetto Corsa Evo, das noch
Early Access ist und sein Layout verschieben kann.

**iRacing ist als experimentell markiert** und zeigt sich so im Profilwähler.
Nicht weil es schlechterer Code als die anderen wäre, sondern weil niemand, der
an SimPitRadio arbeitet, ein Exemplar besitzt — es wird also, anders als der
Rest, nicht am echten Ding geprüft, es sei denn, jemand mit dem Spiel führt
`--telemetry` aus und sagt, was zurückkam. Wenn das Sie sind, bitte tun Sie es;
der Hinweis in der Plugin-Liste bittet um genau das.

## Einstellungen je Simulation

Drei der Zahlen des Ingenieurs leben auf dem **Profil**, unter den
Plugin-Einstellungen des Spiels, nicht auf dem Reiter Ingenieur — weil sie das
Spiel beschreiben und nicht Ihren Geschmack:

- **Spotter-Seiten tauschen** — wenn „links“ ein Auto rechts von Ihnen meint
- **Spotter-Überlappung (Meter)** — wie weit auseinander entlang der Strecke noch
  als nebeneinander zählt. Ein Hypercar ist etwa 5 m lang
- **Spotter-Breite (Meter)** — wie weit zur Seite zählt, bevor sie schlicht auf
  einem anderen Teil der Strecke sind

Fahrzeuglängen und Achsenkonventionen unterscheiden sich zwischen Simulationen,
also ist eine Zahl, die zu einem Spiel passt, im nächsten falsch.

## Flaggen und Zwischenfälle

Eine eigene Verhaltensweise, und bewusst getrennt vom Spotter. Crew Chiefs eigene
Sound-Ordner ziehen die Linie, und es ist die richtige: `car_left`,
`still_there` und `clear_all_round` liegen in `spotter/`, während
`stopped_car_in_turn_3`, `slow_car_ahead` und `local_yellow_ahead` in `flags/`
liegen. Der Spotter beantwortet „wer ist neben mir“, was Geometrie ist. Flaggen
beantworten „was ist mit der Strecke passiert“, was es nicht ist.

Das Zweite aus dem Ersten abzuleiten ist, was in jeder Bremszone eine Warnung
erzeugte: SimPitRadio hatte eine Regel, die besagte, ein viel langsameres Auto sei
eine Gefahr, und eine Bremszone ist genau der Ort, an dem das Auto davor viel
langsamer ist als Sie. Diese Regel ist weg.

**Drei Quellen, nicht gleich vertrauenswürdig.**

*Volle Gelbphase* und *Blau* kommen aus der Simulation und sind verlässlich —
LMUs `mGamePhase`, `mYellowFlagState` und das `mFlag` je Auto lesen sich gegen
eine laufende Session alle vernünftig.

*Lokale Gelbe werden abgeleitet*, weil LMUs `mSectorFlag` nicht brauchbar ist. Es
ist dokumentiert als „ob es im Moment in jedem Sektor lokale Gelbe gibt“ und
liest unter grüner Flagge `[11, 11, 1]`, während die Felder daneben stimmen — es
ist also kein verrutschter Offset, LMU veröffentlicht dort schlicht etwas
anderes. Als Boolesche gelesen legte es ein dauerhaftes Gelb über die ganze
Strecke. Ein Zwischenfall bedeutet hier also, was ein Streckenposten damit meint:
Ein Auto steht auf der Straße und steht dort seit zwei Sekunden. Das ist eine
Ableitung aus Daten, die die Simulation ehrlich veröffentlicht, im selben Geist
wie die Kurven in der Geschwindigkeitsspur zu finden, statt eine Streckenkarte
auszuliefern.

Der Preis ist, dass die Ansage dem Zwischenfall nicht vorausgehen kann — ein
echtes Gelb ist draußen, sobald die Posten es sehen, und dieses wartet, um sicher
zu sein. Der Nutzen ist, dass es sich über eine grüne Strecke nie irrt, und das
ist der Fehler, wegen dem Leute eine Funktion abschalten.

**Zwischenfälle werden nach Kurve benannt, nicht nach Fahrer.** Bei der
Geschwindigkeit, bei der das zählt, ist „Kurve sechs“ etwas, worauf ein Fahrer
handeln kann, und ein Name eine Silbenzahl, auf die er es nicht kann. Die
Nummerierung ist die des Rundenbuchs, damit ein Fahrer einen Satz Kurvennummern
hört statt einer Funktion mit einem Satz und den Flaggen mit einem anderen; die
Kurven werden einmal je Referenzrunde gefunden und zwischengespeichert, weil
`find_corners` eine ganze Runde neu abtastet und dies mehrmals pro Sekunde läuft.
Ohne Referenzrunde wird stattdessen der Sektor genannt.

**Wenn Sie der Zwischenfall sind, hören die Seitenansagen auf.** Dem Fahrer eines
gedrehten Autos die vorbeifahrenden Autos zu beschreiben ist Lärm; die einzige
nützliche Frage ist, ob Platz zum Ausfahren ist, und
[rejoin.py](../src/pitradio/engineer/rejoin.py) beantwortet sie — es vergleicht
*Zeit, um sicher zu sein* mit *Zeit, bis das nächste Auto ankommt*, nicht
Entfernung mit Entfernung. Ein stehendes Auto braucht seine ganze Beschleunigung
zurück, bevor der Erste eintrifft. Darum werden Leute bei der naiven Antwort
„drei Sekunden freie Strecke“ eingesammelt.

Zwei Schutzmaßnahmen, beide gelernt statt angenommen: In der Boxengasse wird
nichts gesagt, wo Stehen der Sinn ist, und nichts, bevor das Auto sich je bewegt
hat — vor dem Start auf dem Grid zu sitzen ist stehend, auf der Ideallinie, mit
dem ganzen Feld dahinter, und das sind alle Eingaben, die der Wiedereinfahrtsrat
betrachtet.

Siehe [voicepacks.md](voicepacks.md) zum Erzeugen einer Stimme.

## Fragen

Verschieden von Verhaltensweisen, und der Unterschied ist keine Buchführung. Eine
Verhaltensweise ist etwas, das der Ingenieur *weiter tut* — siehe [Was er Ihnen
sagt](#was-er-ihnen-sagt) — und sie trägt ein Wiederholungsintervall, denn ein
Auto daneben hört auf, dort zu sein, ohne dass etwas passiert. Eine Frage hat
eine Antwort, und wenn die Antwort gegeben ist, läuft nichts mehr. Das eine als
das andere zu modellieren würde „who has the fastest lap“ in die Liste der
Verhaltensweisen setzen, wo jeder Eintrag ein Wiederholungsintervall hat, und es
gibt kein Wiederbeantworten einer Frage alle 1,2 Sekunden.

Drei davon: die schnellste Runde, der schnellste Sektor und Ihre eigene beste.

**Der Parameter folgt dem Schlüsselwort und ist nie Teil der Wendung.** Wonach
ein Fahrer fragen kann, hängt von der Simulation ab, in der er ist — die Klassen
auf diesem Grid, die Sektoren, die diese Strecke hat —, und nichts davon gehört
in eine Wendung, die jemand in ein Einstellungsfeld getippt hat. „Who has the
fastest sector“ ist die Wendung; „three in GT3“ ist, was danach kam, gegen die
Session geparst. Eine Klasse wird über `mentions.class_aliases` abgeglichen,
sodass LMUs „LMGT3“ genau wie überall sonst auf „GT3“ hört, und „LMP2“ sich
weiterhin weigert, auf „P2“ zu hören, weil das eine Position ist.

**Ein geschlossener Argumentraum ist die Verteidigung gegen Falschtreffer**, und
eine bessere als Wörter zu zählen. `phrases.MIN_BARE_WORDS` schützt die
gesprochenen Befehle, indem es zwei Wörter vor einem offenen Parameter verlangt;
das reicht hier nicht, denn „who has the fastest lap of my life that one“ schafft
das mühelos und würde als Frage nach einer Klasse namens „of my life that one“
genommen — und die Nachricht verschlucken. Aber das Argument einer Frage kann nur
eine Klasse auf diesem Grid sein, ein Sektor zwischen eins und drei, oder nichts.
Alles andere war keine Frage, womit auch immer es begann. Namentlich angesprochen
ist es unabhängig davon eine: Wer den Namen des Ingenieurs gesagt hat, sprach mit
ihm.

**Keine genannte Klasse heißt Ihre eigene Klasse**, denn das meint jemand in
einem GT3-Auto mit „who has the fastest lap“. Eine genannte Klasse, in der
niemand ist, wird als solche gemeldet, statt still mit der Gesamtzahl beantwortet
zu werden — eine selbstbewusst behauptete falsche Antwort ist der Ausfall ohne
Symptom.

Jede hat ein Häkchen auf dem Reiter Ingenieur und sonst nichts. Wonach eine Frage
gefragt werden kann, ist dadurch festgelegt, was die Simulation veröffentlicht,
ein editierbares Wendungsfeld dort würde also andeuten, man könne eine erfinden.

Der Schalter verdient seinen Platz aus einem anderen Grund: **Jede Wendung, auf
die der Ingenieur hört, ist eine Wendung, die aus einer Nachricht an die ganze
Session herausgenommen werden kann**, und wer diese nie fragt, hat keinen Grund,
das Risiko zu tragen. Eine abzuschalten entfernt ihre Wendungen vollständig aus
dem Matcher, statt sie weiter hinten stummzuschalten — sonst würde „who has the
fastest lap“ weiterhin aus der Nachricht gehoben und dann mit nichts beantwortet,
was das Schlechteste von beidem ist. In der Konfiguration fehlend bedeutet an,
sodass das Hinzufügen einer Frage nie eine Migration braucht.

## Der Spotter und woher seine Zahlen kommen

Jede Schwelle in `spotter.py` ist die von Crew Chief, aus einer lokalen
Installation ausgelesen statt geraten — sein `ui_text/en.txt` benennt jede
Einstellung und `CrewChiefV4.exe.config` liefert die Standardwerte:

| Unsere | Die von Crew Chief | Standard |
| --- | --- | --- |
| `DEFAULT_CAR_LENGTH` | `lmu_spotter_car_length` | 4,5 (5 für pcars2/ACC, 4,4 für AMS2) |
| `GAP_FOR_CLEAR` | `spotter_gap_for_clear` | 0,5 m |
| `OVERLAP_DELAY` | `spotter_overlap_delay` | 50 ms |
| `CLEAR_DELAY` | `spotter_clear_delay` | 150 ms |
| `MIN_SPEED` | `min_speed_for_spotter` | 10 m/s |
| `MAX_CLOSING_SPEED` | `max_closing_speed_for_spotter` | 12 m/s |
| das Wiederholungsintervall | `spotter_hold_repeat_frequency` | 3 s |

Drei davon fehlten hier ganz, und jede verursachte einen Fehler, den der Fahrer
spüren konnte:

**Die Annäherungsgrenze ist es, die das überrundende Auto fängt.** Etwas, das
12 m/s schneller ankommt, durchquert das ganze Überlappungsfenster in deutlich
unter einer Sekunde, sodass es weg ist, bis die Ansage gesprochen ist — und der
Fahrer hält eine Linie für ein Auto, das nicht mehr da ist.

**Die Mindestgeschwindigkeit ist es, die die Boxengasse und das Grid stoppt.**
Unter 10 m/s stehen die Autos um Sie herum oder ziehen im Schritttempo vorbei,
und die anzusagen ist, wie ein Spotter abgeschaltet wird.

**Die beiden Beruhigungsverzögerungen sind es, die das Geplapper stoppen.** Zwei
Autos in derselben Kurve kreuzen in und aus der Überlappung, während sie atmen.
Sie sind bewusst unterschiedlich lang: Die Überlappungsverzögerung ist kurz, weil
eine verspätete Warnung wertlos ist, und die Freigabeverzögerung ist länger, weil
sie es sich leisten kann, sicher zu sein — wer seine Linie ein Zehntel länger als
nötig hält, hat nichts verloren.

Die Freigabereichweite ist `Fahrzeuglänge + Abstand`, nicht ein zweites Vielfaches
der Länge. Der Unterschied zählt an den Extremen: Für ein Kart sind „eine weitere
Fahrzeuglänge“ zwei Meter Hysterese und die Ansage hängt viel zu lange nach,
während ein halber Meter Tageslicht ein halber Meter ist, egal was Sie fahren.

**Der Spotter schweigt unter voller Gelbphase** — Crew Chiefs
`fcy_stop_spotter_immediately`, standardmäßig an. Das Feld ist im Schritttempo
zusammengedrängt und dauerhaft überlappend, jede Ansage wäre also wahr und
nutzlos.

### Was er sagt

Das Vokabular ist Crew Chiefs Ordner `Sounds/voice/spotter/`, ein für Crew Chief
gebautes Sprachpaket spricht also alles davon ohne Zuordnung: `car_left`,
`car_right`, `still_there`, `hold_your_line`, `in_the_middle`, `clear_left`,
`clear_right`, `clear_all_round`, `three_wide_on_left`, `three_wide_on_right`.

Zwei davon ersetzten Ansagen, die dieselbe Tatsache umständlicher herum sagten:

* **„Three wide, you're on the right“** war „two cars left“. Wer die alte hört,
  muss sich ausrechnen, wo ihn das lässt, während er beschäftigt ist; die neue
  sagt direkt, in welche Richtung kein Platz ist.
* **„In the middle“** war „three wide“, für je ein Auto auf beiden Seiten.

Eine Wiederholung sagt `still there` auf einer Seite und `hold your line` auf
beiden, denn das sind verschiedene Anweisungen — die eine heißt, geh nicht dorthin,
die andere heißt, beweg dich nicht. Die Ankunft und ihre Wiederholungen teilen
sich einen Schlüssel, der aus den *Zählungen* abgeleitet ist, damit das
Wiederholungsintervall sie regiert; ein Schlüssel, der sich mit der Formulierung
änderte, machte die Folgeansage zu einer neuen Ansage, fällig schon beim nächsten
Tick.

**Das Oval-Set fehlt bewusst** — `car_inside`, `clear_outside`,
`three_wide_on_inside`. Welche Seite innen ist, ist eine Tatsache über die
Steilkurve, die keine der Simulationen hier veröffentlicht und die Crew Chief je
Strecke pflegt. Eine Vermutung darüber ist eine Ansage, die selbstbewusst
verkehrt herum ist.

### Sprit

„How much fuel do I need to finish the race when I pit on the next lap“, oder
„...when I pit in five laps“. **Die Antwort ist ein Prozentsatz**, denn das ist
die Zahl auf dem eigenen Spritbildschirm der Simulation, und der Fahrer hat auf
dem Weg zur Boxeneinfahrt etwa vier Sekunden, um sie einzustellen. Liter sind der
Rechenweg.

**Der Verbrauch wird gemessen, nie angenommen.** Was ein Auto braucht, hängt von
der Strecke ab, vom Motorkennfeld, vom Verkehr und davon, wie die Person es
fährt, also ist Liter pro Runde hier das, was *dieses* Auto über *diese* Runden
verbraucht hat — ein kurzer gleitender Durchschnitt, damit er einem Wechsel des
Kennfelds folgt, statt von einem ganzen Stint zurückgezogen zu werden. Bevor eine
Runde beendet ist, gibt es keine Antwort, und das wird gesagt. Eine aus dem
Nichts erfundene Spritzahl ist die eine falsche Antwort hier, die jemandes Rennen
beendet.

Drei Details, die sonst neu entdeckt würden:

* **Für die Runden vor dem Stopp wird nicht getankt.** Was jetzt im Tank ist,
  deckt die ab. Nur die danach sind die Frage, und deshalb liest dies nie den
  aktuellen Stand.
* **`mMaxLaps` ist in einer Zeitsession `INT_MAX`.** Für bare Münze genommen
  verlangt es Sprit für zwei Milliarden Runden. `SessionInfo` führt `max_laps`
  *oder* `ends_at`, nie beides, und das Plugin entscheidet, welches — der
  Ingenieur rät das fehlende nie. Ein Zeitrennen teilt die verbleibende Uhr durch
  die eigene beste Runde des Fahrers und rundet **auf**, weil die Flagge am Ende
  der Runde fällt, auf der Sie sind, wenn die Uhr abläuft.
* **Eine Füllung über der Tankkapazität wird gemeldet, nicht abgeschnitten.** Sie
  bedeutet, dass der Stopp nicht der letzte sein kann, und ein Fahrer, dem
  „einhundert Prozent“ gesagt wird, ohne dass ihm das gesagt wird, plant ein
  Rennen, das nicht aufgeht.

Alles andere rundet in Richtung mehr Sprit: Leerfahren ist ein Ausfall, und einen
Liter zu viel zu tragen ist ein Zehntel pro Runde.

Sprit erreicht `Car` **nur für das Auto des Spielers** — die Simulationen
veröffentlichen Tanktelemetrie für das Auto, das Sie fahren, und für niemanden
sonst — und er wird über den Abgleich von `mID` angehängt, weil LMUs
Telemetriearray über `playerVehicleIdx` indiziert ist und das Wertungsarray
nicht. Nach Position anzuhängen legte Ihren Tank auf das Auto, das zufällig in
diesem Slot gewertet wurde.

## Weg vom Lenkrad sein

Der Ingenieur sagt nichts und **zeichnet nichts auf**, wenn der Fahrer nicht
fährt. Drei Zustände, und sie brauchen drei verschiedene Signale:

* **Pausiert** — die Uhr der Simulation steht still, während die dieser Maschine
  weiterläuft, und die Differenz ist das Signal. Nicht `mGamePhase`: Das las
  *grüne Flagge* durch eine ganze Session, die pausiert in der Garage saß, mit
  `mCurrentET` eingefroren bei 2218,0. Die Phase sagt, welche Art Session es ist,
  nicht ob sie läuft.
* **In der Garage** — hier läuft die Uhr weiter, die Uhr kann also nicht das
  Signal sein. `mInGarageStall` ist es. Verschieden von `in_pits`, das die ganze
  Boxengasse abdeckt: Ein Auto, das einen Stopp absolviert, fährt Rennen.
* **An die KI übergeben** — `mControl` ist 1, und so sieht Zuschauen aus.

**Es wird auch nichts beobachtet, nicht bloß nichts gesagt.** Eine pausierte
Simulation veröffentlicht denselben Frame für immer neu, und das dem Rundenbuch
zu füttern zeichnet ein Auto auf, das keinen Boden gutmacht, solange jemand das
Spiel dort sitzen lässt — eine korrupte Referenzrunde statt einer fehlenden. Der
Zustand des Spotters wird auf dem Weg hinein aus demselben Grund verworfen: Ein
Auto, das vor der Pause daneben war, ist eine Tatsache über einen Moment, der
vorbei ist.

**Ein Online-Rennen zu pausieren wird nicht erkannt und kann es nicht.** Die Uhr
läuft dort weiter, weil das Rennen weiterläuft — das Menü ist auf dieser Maschine
offen und die Autos fahren weiter. Nichts im Shared Memory trennt das von
gewöhnlichem Rennfahren, und ein Signal dafür zu erfinden würde den Ingenieur
während eines echten Rennens verstummen lassen. Was der schlimmere der beiden
Fehler ist.
