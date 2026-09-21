# Sprachpakete

Der Ingenieur klingt nur dann wie ein Mensch, wenn es Aufnahmen von einem gibt.
Genau das ist ein Sprachpaket: ein Ordner mit WAV-Dateien, ein Ordner je Satz,
den der Ingenieur abspielt, statt über die Windows-Stimme zu sprechen. Mehrere
Aufnahmen eines Satzes können in seinem Ordner liegen, und der Ingenieur wählt
zufällig eine davon, sodass dieselbe Ansage zweimal in einem Stint nicht wie
eine sich wiederholende Maschine klingt.

Alles, was er sagt und nicht im Paket steht, wird weiterhin von der
Windows-Stimme gesprochen: Ihr Name, eine Rundenzeit, ein Fahrer, von dem er
nie gehört hat. Ein Paket muss nicht vollständig sein, um etwas zu taugen.

## Drei Wege zu einem Paket

**Ein veröffentlichtes installieren.** *Einstellungen → Stimme* listet die zum
Download veröffentlichten Pakete auf und installiert eines auf Wunsch, wobei die
Prüfsumme kontrolliert wird, bevor irgendetwas entpackt wird. Das ist der Weg für
eine andere Sprache als Ihre eigene.

**Selbst aufnehmen**, im Fenster. Das ist der Weg ohne Obergrenze und der, um den
herum die App gebaut ist: *Einstellungen → Stimme → Stimmmodell erstellen*.

**Eine Basis mit Piper erzeugen**, offline, und die Teile neu aufnehmen, die
Ihnen wichtig sind. Greifen Sie darauf zurück, wenn Sie noch heute etwas
Korrektes und Angenehmes wollen oder lieber nicht 171 Sätze vorlesen, bevor Sie
fahren.

Das schließt sich nicht aus. Ein Piper-Paket ist ein ganz gewöhnliches Paket,
also lässt sich jeder Satz darin später durch Ihre eigene Aufnahme ersetzen.

### Warum kein Voice Cloning

Das wurde zuerst versucht und verworfen, und der Grund ist es wert, ihn zu
kennen, bevor Sie danach suchen.

Für dieses Projekt wurde aus fast drei Minuten sauberem Referenzmaterial eine
geklonte Stimme erzeugt. Durch die eigene Spracherkennung der App zurückgeschickt
kam jede Aufnahme von „five“ als „bye“ an, „four“ als „boy“ und „zero“ als „yo“.

Das Inventar ist der Grund. **141 der 171 Sätze sind ein oder zwei Wörter**, und
kurzer Text ist genau die Stelle, an der ein Klonmodell am schwächsten ist: XTTS
erzeugt autoregressiv und entscheidet selbst, wann es aufhört — bei zwei Wörtern
gibt es fast nichts, was diese Entscheidung einschränkt. Piper ist ein Modell im
VITS-Stil, ein Durchlauf von Phonemen zur Wellenform, ohne Sampling-Schleife,
die abschweifen kann. Es kann kein anderes Wort sagen, und das zählt bei diesem
Inventar mehr als die Klangfarbe.

Crew Chief löst dasselbe Problem auf dieselbe Weise: Seine Pakete sind
*aufgenommen*, und seine 11.176 Fahrernamen und 1.052 Zahlenclips wurden von
einem Menschen eingelesen.

## Selbst aufnehmen

*Einstellungen → Stimme → Stimmmodell erstellen* öffnet einen Rekorder: ein Satz
zum Vorlesen, ein Countdown, eine Aufnahme und die Wiedergabe zur Kontrolle.

Es ist weniger Arbeit, als es klingt. Das ganze Inventar sind **etwa vierzig
Minuten bei drei Aufnahmen je Satz**, und es lässt sich fortsetzen, also in
mehreren Sitzungen. Ein Paket mit der Hälfte der Sätze funktioniert ab dem
Moment, in dem Sie es speichern.

Ein paar Dinge entscheiden, ob das Ergebnis brauchbar ist:

- **Seitlich am Mund vorbei**, ein paar Fingerbreit entfernt, statt davor. Ein
  Bügelmikro direkt im Luftstrom übersteuert bei jedem *p* und *b*, und
  Übersteuerung lässt sich hinterher nicht rückgängig machen.
- **Ein ruhiger Raum.** Ein Lüfter oder ein PC unter dem Schreibtisch landet in
  jedem Clip, und jeder Clip wird Ihnen mitten im Rennen über einen Kopfhörer
  vorgespielt.
- **Gleichbleibender Abstand.** Lehnen Sie sich zwischen den Aufnahmen nicht hin
  und her. Clips in vier verschiedenen Abständen klingen nach vier verschiedenen
  Menschen.
- **Die Mikrofonverstärkung von Windows abschalten.** Sie ist ein Kompressor und
  pumpt zwischen den Wörtern das Raumrauschen hoch.

Lesen Sie sie so, wie ein Ingenieur sie über Funk sagt: sachlich, unaufgeregt,
leicht gelangweilt. Der Ingenieur spielt keine Rolle.

## Eine Basis mit Piper erzeugen

Piper läuft offline, aus den Packaging-Skripten heraus statt in der App. Die
folgenden Pfade sind relativ zu `apps/client` in einem Source-Checkout:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

Für ein bestimmtes Modell:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Offline und nicht in der App, mit Absicht.** Piper ist auf einer CPU schnell
genug, um verführerisch zu sein, es zur Sprechzeit aufzurufen. Das brächte ein
63-MB-Modell und eine ONNX-Laufzeit in einen Build, dessen letzte vier kaputte
Releases allesamt native Abhängigkeiten waren, die nicht mit eingesammelt wurden.
Ein Paket ist ein Ordner voller WAVs; es hier zu erzeugen kostet die App nichts
und kann keinen Build zerstören.

Es ist nicht *Ihre* Stimme, und nichts tut so. Es ist eine Basis, die korrekt und
angenehm ist und über der sich jeder Satz im Fenster neu aufnehmen lässt.

**Japanisch braucht ein weiteres Paket und scheitert ohne es verwirrend.**
Das japanische Modell verlangt von Piper `pyopenjtalk`, um Text in Phoneme zu
verwandeln, und ohne das erzeugt jede Phrase gar kein Audio. Gemeldet wird
`wave.Error: # channels not specified`, was die leere Ausgabedatei ist und
nicht die eigentliche Ursache. Das originale `pyopenjtalk` liefert nur Quellcode
und will CMake und einen C++-Compiler; `pyopenjtalk-plus` ist ein Fork, der
Wheels unter demselben Importnamen liefert, und steht in der Anforderungsdatei
oben.

## Wie ein Paket aussieht

Ein Paket ist ein Ordner mit einem Unterordner `voice`, und darin ein Ordner je
Satz, der dessen Aufnahmen hält. Das ist das Layout, das
`crew-chief-autovoicepack` schreibt, also **lässt sich ein Crew-Chief-Paket
direkt einlegen**. Der äußere Ordner ist getrennt, damit ein Paket eine Lizenz
und seine Quellaufnahmen mitführen kann, ohne dass diese für Sätze gehalten
werden.

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

Der Ordner, in dem eine WAV-Datei liegt, ist der Satz, also ist die Tiefe
zwischen `voice` und diesem Ordner frei. Der Rekorder schreibt `pitradio/`;
Crew Chief schreibt einen Ordner je Kategorie. Beides wird gleich gelesen.

Nur WAV. Es ist das, was jeder Generator ausgibt, was die Standardbibliothek
liest, und es braucht keinen Decoder in einem Build, der ohnehin mit nativen
Abhängigkeiten kämpft.

Ordnernamen entstehen aus dem Satz, kleingeschrieben, wobei Satzzeichen
**entfallen** statt ersetzt zu werden, also sind „that's enough“ und „thats
enough“ derselbe Clip. Einen Apostroph in ein Trennzeichen zu verwandeln ergäbe
`that_s_enough`, und ein Paket, das gegen eine der beiden Schreibweisen
aufgenommen wurde, verfehlte die andere stillschweigend.

## Wo Pakete liegen

**Einstellungen → Stimme** ist der Ort, an dem sie alle aufgelistet sind: was
installiert ist, was mitgeliefert wird und was heruntergeladen werden kann.
Pakete liegen neben Ihrer Konfiguration, in `voices/`, statt im
Installationsverzeichnis. Ein Update ersetzt das Installationsverzeichnis
komplett, und ein Paket ist eine Menge Audio, die Sie dort abgelegt haben.
**Einstellungen → Stimme → Sprachpaket-Ordner öffnen** öffnet ihn.

Ordner hineinlegen, den Reiter neu öffnen, und es erscheint in der Auswahl.

## Die Satzliste

**Einstellungen → Stimme → Satzliste schreiben** exportiert jeden Satz, den der
Ingenieur sagen kann, als CSV, in der Sprache des Ingenieurs. Ein Paket wird in
der Sprache aufgenommen, in der es gesprochen wird.

Sie wird aus der App erzeugt statt von Hand gepflegt, kann also nicht davon
abweichen, was der Ingenieur tatsächlich sagt. Nutzen Sie sie, wenn Sie außerhalb
der App aufnehmen oder sich einen eigenen Generator schreiben.

## Es kommt nichts

**Prüfen Sie, ob ein Paket ausgewählt ist.** *Ingenieur → Stimme → Stimme* muss
auf das Paket zeigen und nicht auf *(kein Paket)*.

**Prüfen Sie das Ausgabegerät.** *Audio → Ausgabe* sollte Ihr Headset sein,
dasselbe, das Sie für den Sprachchat nutzen, statt der Ausgabe der Simulation.

**Ein fehlender Satz ist kein Fehler.** Alles, was nicht im Paket steht, fällt
auf die Windows-Stimme zurück, sodass ein halb aufgenommenes Paket nach zwei
Menschen klingt, statt auszufallen. Das ist Absicht: Es ist genau das, was ein
Paket brauchbar macht, bevor es fertig ist.
