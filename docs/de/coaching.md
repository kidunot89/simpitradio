# Der Coach

Wählen Sie jemanden zum Studieren. Jedes Mal, wenn Sie einen Abschnitt der
Strecke beenden, zeichnet das Panel Ihre Linie gegen dessen und der Coach sagt
Ihnen, was Sie anders machen sollen.

> *Tosa, du hast Kurvenmittengeschwindigkeit verschenkt, weil du am Scheitelpunkt
> noch auf der Bremse warst, und er scheitelt später, dadurch macht sich sein
> Ausgang früher gerade.*

Er liest Ihre Pedale, Ihr Lenkrad und Ihren Gang zusätzlich zur Uhr, also nennt
er eine Ursache und nicht eine Umformulierung des Zeitenmonitors. Blockieren Sie
ein Rad oder gehen Sie neben die Strecke, sagt er es sofort, solange Sie noch
spüren, was Sie getan haben.

Der Coach ist eine zweite Stimme mit eigenen Einstellungen: eine eigene
Lautstärke, eigene Benachrichtigungen, und jede Ansage kommt in dieser Stimme,
damit Sie immer wissen, wer von beiden mit Ihnen spricht. **Coaching → Wer**
richtet das ein. *Den Ingenieur als Coach verwenden* gibt beiden eine Stimme,
wenn Ihnen das lieber ist.

## Schnellstart

1. Fahren Sie drei oder vier Runden. Der Coach findet die Strecke zuerst heraus:
   siehe [Woher die Abschnitte kommen](#woher-die-abschnitte-kommen).
2. Halten Sie den Auslöser und sagen Sie **„coach me“**.
3. Sagen Sie **„focus on P3“**, oder **„focus on me“**, um an Ihrer eigenen
   Bestzeit gemessen zu werden.
4. Fahren Sie. Nach jeder Kurve zeichnet das Panel sie und der Coach spricht.

Nichts davon ist ein Häkchen, das Sie vor einer Session setzen. Coaching wird laut
verlangt, wenn Sie es wollen, und stellt sich ab, wenn Sie es sagen — denn ob Sie
durch eine Kurve angesprochen werden möchten, ist eine Entscheidung, die Sie Runde
für Runde treffen.

## Mit ihm sprechen

Die meisten Wendungen unten sind zwei Wörter oder länger, der Name des Coachs
davor ist also optional. Die Ausnahmen sind „study“ und „watch“: Beide sind ein
einzelnes Wort, und alles, was danach gesagt wird, ist der Fahrername, also
brauchen beide den Namen des Coachs davor. *Chief, study Estre.*

| Dafür | Sagen Sie |
| --- | --- |
| Coaching starten | **coach me** · *lead me to it* · *show me the lines* · *start coaching* |
| Beenden | **stop coaching** · *stop the coaching* · *no more lines* |
| Wählen, gegen wen gemessen wird | **study Estre** · *focus on P3* · *keep an eye on the LMP2 leader* |
| Gegen die eigene Bestzeit messen | **focus on me** · *study my best* · *focus on my ideal lap* |
| Wieder automatisch wählen lassen | **default focus** · *automatic focus* |
| Hören, was läuft | **what coaching is on** |
| Die eben gefahrene Kurve neu zeichnen | **last corner** · *that corner* |

Ein einzelnes Wort mit einem Argument ohne Ende würde sonst eine für die
Session bestimmte Nachricht verschlucken. „focus on“ und „keep an eye on“ sind
lang genug, um für sich allein sicher zu sein, und genau deshalb stehen sie
dort.

**Sie müssen keinen Rivalen wählen.** Bitten Sie ihn, sich auf *Sie* zu
konzentrieren, und die zweite Linie wird Ihre ideale Runde: Ihr Bestes durch
jede Kurve, zusammengesetzt. Keine Runde, die Sie gefahren sind, sieht so aus.
Eine leere Trainingssession hat immer noch jemanden zum Rennen, und auf einer
leeren Strecke ist es der ehrliche Gegner.

## Woher die Abschnitte kommen

**Die Strecke wird aus den in der Session gefahrenen Runden ermittelt**, Ihren
und denen aller anderen, statt aus einer Datenbank. Jede Runde wird auf ein
Gitter mit fünf Metern Abstand gelegt, und der Median dessen, was durch jeden
Punkt kam, ist der Verlauf der Straße. Vier Runden müssen einen Punkt kreuzen,
bevor er geglaubt wird, und die halbe Strecke muss bekannt sein, bevor
überhaupt eine Straße gebaut wird.

Darum funktioniert es auf jeder Strecke in jeder Simulation, auch auf solchen,
die nie jemand katalogisiert hat. Wo ein Katalog existiert, bekommen Sie
Namen, *Tosa* statt *Kurve sieben*. Wo keiner existiert, bekommen Sie Nummern,
und alles andere funktioniert genau gleich.

Das Zusammenlegen geschieht zweimal. Der erste Durchgang hat keine Straße, an
der er sich messen könnte, also nimmt er die eigene Fahrtrichtung des Autos,
um zu bestimmen, wo quer zur Strecke ist. Ein pendelndes Auto zeigt nie
entlang der Straße, der Fehler kommt also auf jeder Runde in dieselbe Richtung
heraus. Sobald eine Straße da ist, ist deren eigene Richtung die richtige
Referenz, und der zweite Durchgang korrigiert. Auf einem synthetischen Kreis
mit drei Metern Pendeln legte der erste Durchgang die Straße zweieinhalb Meter
neben ihre tatsächliche Lage.

### Was als Abschnitt zählt

Ein Abschnitt ist eine Kurve plus die Anfahrt und die Ausfahrt, denn das ist, was
Sie fahren.

- Die **Anfahrt** reicht zurück bis dorthin, wo Sie auf die Bremse gegangen sind,
  gedeckelt bei 250 m. Bremsen Sie später, beginnt der Abschnitt später.
- Die **Ausfahrt** reicht 50 m über den Kurvenausgang hinaus, genug um zu zeigen,
  wo das Auto herauskam und wohin es zeigte.
- **Zwei Kurven, für die Sie einmal bremsen, sind ein Abschnitt.** Club und Vale
  sind eine Sache zu fahren und eine Sache anzusehen. Ebenso das Haarnadelpaar
  in Sebring.
- **Kurven, die Sie voll nehmen, werden übersprungen.** Eine Kurve, die über 90 %
  Gas gehalten wird, hat keinen Bremspunkt zu verschieben und keine
  Eingangsgeschwindigkeit mitzunehmen, sie gilt also als Gerade. Sie bleibt auf
  der Karte und behält ihren Namen, und sie wird Ihnen einfach nie vorgelegt.
  Schalten Sie **Geraden und Vollgas-Abschnitte** unter *Was gecoacht wird* ein,
  um sie trotzdem zu sehen.

Zusammenlegen und Überspringen brauchen beide eine Referenzrunde. Ohne sie hat der
Coach keinen Grund zu entscheiden, dass zwei Kurven wirklich eine sind, also lässt
er sie getrennt.

## Was er sagt

**Coaching → Was gecoacht wird → Fahrerniveau** entscheidet, wie viel. Alle drei
Stufen sehen dieselbe Kurve an und finden denselben Fehler; sie lassen Nebensätze
weg, keine Befunde.

| Stufe | Was Sie bekommen |
| --- | --- |
| **Anfänger** | Alles — was besser war, was schlechter, was es verursacht hat und was zu tun ist |
| **Fortgeschritten** | Ohne Folge. Der Fehler und die Abhilfe, in der Annahme, dass Sie wissen, was Untersteuern am Scheitelpunkt mit einem Ausgang macht |
| **Erfahren** | Auch ohne Abhilfe. Was gut war und was falsch; „bremse früher“ zu hören heißt meist, etwas zu hören, das Sie schon wissen |

Einiges davon, was er misst, und die Schwellen, die er benutzt, damit Sie wissen,
wann er absichtlich schweigt:

- Zwei Geschwindigkeiten müssen sich um einen halben Meter pro Sekunde
  unterscheiden, was unter 2 km/h liegt, bevor es der Rede wert ist. Darunter
  haben Sie beide dasselbe getan, und der Unterschied liegt darin, wo die
  Runden zufällig abgetastet wurden.
- Die Strecke zu nutzen heißt, 85 % ihrer halben Breite zu erreichen, nicht die
  ganze. Wer jede Runde ein Rad exakt auf die weiße Linie setzt, nimmt
  Track-Limits mit, und die Linie, die gewinnt, ist die, die nah herankommt.
- Ein Pedal gilt bei 5 % Weg als getreten, und das Lenkrad bei 5 % Einschlag als
  eingeschlagen. Sim-Pedale und -Lenkräder ruhen selten exakt bei null.

## Benachrichtigungen

**Coaching → Benachrichtigungen** schaltet die drei Arten von Ansagen des Coachs
unabhängig voneinander an und aus:

- **Abschnittsanalyse**: die Auswertung nach jeder Kurve.
- **Fehler, während sie passieren**: ein blockiertes Rad, ein Ausflug neben die
  Strecke, sofort angesagt statt aufgespart.
- **Wo sie schneller waren**: einmal pro Runde.

Diese sind absichtlich von den Verhaltensweisen des Ingenieurs getrennt, damit das
Herunterdrehen des Coachings nicht den Spotter mit herunterdreht. Alle drei
brauchen weiterhin den laufenden Coach, und keine sagt etwas, bevor Sie um
Coaching gebeten haben.

## Das Diagramm

![Curva Parabolica, Ihre Linie gegen die eines Rivalen](images/segment_parabolica.png)

Die Parabolica in Monza, aus einer echten Session. Der helle Verlauf ist Bremsen,
der dunkle ist am Gas; der Kreis ist, wo jedes Auto auf die Bremse ging, und das
Dreieck, wo es wieder aufs Gas ging, in Fahrtrichtung zeigend.

Das Panel hält drei Diagramme: eines kommt an, eines wird gerade in der Mitte
besprochen und eines geht. Die Position ist der Fortschritt, ein Blick sagt
also, wo der Coach steht. Die Diagramme schweben über dem Spiel, ohne dass
etwas dahinterliegt.

Ihre Linie wird in **Orange bis Rot** gezeichnet, die eines Rivalen in **Indigo
bis Cyan**. Der Farbton sagt, wessen Linie es ist. **Die Helligkeit sagt, was
die Füße taten**, am hellsten auf der Bremse und am dunkelsten am Gas. Beide
Linien sind gestrichelt, und die beiden Muster sind um eine halbe Periode
versetzt, sodass dort, wo die Autos exakt dieselbe Linie nehmen, jede durch die
Lücken der anderen scheint, statt dass eine die andere verdeckt. Der Name
jedes Fahrers steht in der jeweils leersten Ecke des Diagramms, in der Farbe
dieses Fahrers, damit Sie sich nie merken müssen, welche Rampe wem gehört.

Die Straße ist ein dunkles Band zwischen zwei weißen Linien, aus der eigenen
Streckenrandmessung der Simulation genommen statt aus der Ideallinie geraten.
Ein Rad außerhalb der Linie wird also außerhalb der Linie gezeichnet.

![Die Diagramm-Schlange](images/diagram_queue.png)

Drei Diagramme: eines kommt an, das besprochene in der Mitte, eines geht. Das
mittlere ist die Kurve, über die der Coach spricht.

### Wie es vom Sitz aus aussieht

![Tosa und die Kurve davor, über das Cockpit in Imola gezeichnet](images/incar_tosa.jpg)

Imola, mitten in der Session. Zwei Diagramme stehen gleichzeitig, die eben
beendete Kurve und die davor, und beide benennen sich aus dem Katalog der
Strecke statt nach Nummer. Sie sitzen über dem Spiel, ohne etwas dahinter,
sodass dem Bildschirm nur die Zeichnung hinzugefügt wird.

![Eine Kurve in Daytona mit beiden Linien und ihren Geschwindigkeiten](images/incar_daytona.jpg)

Dasselbe auf einer Strecke, die niemand katalogisiert hat. Die Kurve heißt `T5`
statt einen Namen zu tragen, und alles andere funktioniert identisch: die
Straße aus der eigenen Streckenrandmessung der Simulation, beide Linien
gestrichelt und versetzt, sodass keine die andere verdeckt, und die
Geschwindigkeiten an Eingang, Scheitelpunkt und Ausgang.

**Coaching → Abschnittsdiagramm** platziert es, bemisst es, setzt seine
Deckkraft und wählt, in welche Richtung die Schlange läuft. **Panel anzeigen**
stellt drei Beispielkurven hin, damit Sie es dorthin ziehen können, wo Sie es
wollen, und gegen das echte Bild bemessen.

Es zeichnet über ein Spiel, das randlos oder im Fenster läuft. Über exklusivem
Vollbild zeichnet nichts, was eine Eigenschaft des Anzeigemodus ist und keine
Einstellung.

## Der Trailbraking-Trainer

Ein Klavierton jedes Mal, wenn ein Reifen unter Bremsen die Haftgrenze erreicht,
damit das Lösen etwas zum Hören wird statt etwas, das man hinterher aus einer
Rundenzeit erschließt.

Das Lösen der Bremse ist das, was sich im Auto am schwersten über das Gefühl
lernen lässt. Das Pedal gibt fast nichts zurück, das Ziel wandert, während das
Auto langsamer wird und Lenkeinschlag dazukommt, und ein Fahrer kann eine Saison
weit unter dem Limit verbringen, ohne es je zu merken. Es erklingt ein Ton je
Löseschritt. Ein Dauerton, der dem Schlupf folgt, wäre ein Summer, den man
ignorieren lernt, und er würde melden, wo man ist, wenn man eigentlich einen
Moment zum Handeln braucht.

| Was Sie hören | Was es bedeutet |
| --- | --- |
| Drei bis sechs Töne, absteigend | Ein sauberes Lösen |
| Ein Ton, dann Stille | Sie sind zu schnell von der Bremse |
| Gar keine Töne | Das Limit wurde nie gefunden |
| Ein tiefer Ton außerhalb der Tonleiter | Ein Reifen hat blockiert |

| Dafür | Sagen Sie |
| --- | --- |
| Starten | **train on the brakes** · *let's start training on the brakes* · *brake training* |
| Beenden | **end brake training** · *stop training on the brakes* |

Er lernt den Abrollradius Ihres Autos über die ersten Bremszonen, funktioniert
also in jeder Klasse und mit der Bremsbalance, wo immer Sie sie haben wollen.
**Coaching → Trailbraking-Trainer** legt fest, ob er mit der Session scharf
geschaltet wird und wie laut die Töne sind. Seine Lautstärke ist von der des
Coachs getrennt, weil beide gemischt und nicht in eine Schlange gestellt werden.
Ein Ton klingt über allem, was gerade gesagt wird, und ein Ton muss nur bemerkt
werden, während Sprache verstanden werden muss.

## Es wird nichts gezeichnet

**Geben Sie ihm ein paar Runden.** Unter vier Runden durch einen Streckenabschnitt
gibt es dort keine Straße, und mit weniger als der halben bekannten Strecke gibt
es gar keine. Das ist die übliche Antwort.

**Prüfen Sie, ob die Simulation eine Position veröffentlicht.** Die Linien werden
aus X/Z-Koordinaten und dem Streckenrand gezeichnet. Eine Simulation, die sie
nicht veröffentlicht, gibt Ihnen weiterhin Rundenzeiten, Fehler und die
gesprochene Analyse. Ein Bild kann sie nicht geben. Siehe
[Was jede Simulation kann](engineer.md#was-jede-simulation-kann).

**Prüfen Sie, ob es nicht exklusives Vollbild ist.** Nur randlos oder im Fenster.

**Prüfen Sie, ob Sie tatsächlich gefragt haben.** Coaching ist aus, bis Sie es
sagen. Wenn es startet, antwortet es mit „coaching“, dann, gegen wen es Sie
misst, und entweder wie viele Abschnitte es hat oder „learning the track“.
