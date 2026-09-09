# Erste Schritte

Installieren, sagen, auf welche Taste gehört werden soll, und etwas sagen.
Alles andere auf diesen Seiten ist optional.

![Das SimPitRadio-Fenster im Reiter Status](images/window.png)

## Installation

Laden Sie das Installationsprogramm von der
[Releases-Seite](https://github.com/kidunot89/simpitradio/releases/latest) herunter
und führen Sie es aus. Windows wird warnen: Die Builds sind nicht signiert, also
zeigt SmartScreen „Der Computer wurde durch Windows geschützt“ und Sie müssen
**Weitere Informationen → Trotzdem ausführen** wählen. So sieht ein unsigniertes
Installationsprogramm aus, und eine Signatur kostet Geld, das dieses Projekt
nicht ausgibt.

Das Setup stellt genau eine Frage — **welche Sprache** — mit Ihrer
Windows-Sprache bereits ausgewählt. Damit sind drei Dinge auf einmal gesetzt:
das Fenster, die Spracherkennung und die Sprache, in der der Renningenieur
spricht und zuhört. Später lässt sich das im Reiter Sprache ändern.

**Es installiert sich mit Administratorrechten, und das mit Absicht.** Windows
verwirft eingespeiste Tastenanschläge, die an ein Programm mit höheren Rechten
als der Absender gehen, und Simulationen laufen oft erhöht. Ohne das sieht alles
so aus, als funktioniere es, und nichts erreicht jemals das Spiel.

### Beim ersten Start werden zwei Dinge geladen

Im Installationsprogramm steckt nichts Großes, deshalb werden Sie beim ersten
Öffnen gefragt, ob Folgendes geholt werden soll:

- **das Sprachmodell**, etwa 250 MB, das aus Ihrer Stimme Text macht
- **eine aufgenommene Stimme** für den Ingenieur, etwa 45 MB, sofern eine in
  Ihrer Sprache veröffentlicht ist

Beides einmalig. Das Modell liegt außerhalb des Installationsverzeichnisses,
damit ein Update es nie erneut kostet. Wenn Sie „Jetzt nicht“ sagen, erledigen
die Reiter Sprache und Einstellungen dasselbe, wann immer Sie wollen.

Das portable ZIP hat kein Installationsprogramm und damit auch keine
Sprachabfrage — es fragt stattdessen beim ersten Start dasselbe.

## Eine Taste wählen

**Einstellungen → Auslöser.** Drücken Sie *Taste drücken…* und dann die
gewünschte Taste.

![Der Auslöser-Bereich im Reiter Einstellungen](images/trigger.png)

Die Taste wird **im Vorbeigehen geschluckt**, das Spiel sieht sie also nie —
Sie können daher eine nehmen, die das Spiel bereits benutzt. `F13` ist die
Vorgabe, weil die meisten Tastaturen keine haben und nichts sonst darauf hört.

**Eine Lenkradtaste funktioniert.** Bilden Sie sie mit
[JoyToKey](https://joytokey.net/) auf eine Tastaturtaste ab und belegen Sie
diese hier. SimPitRadio liest Lenkräder nicht direkt aus; der Grund steht in
[den Notizen des Ingenieurs](engineer.md#einstellungen-je-simulation): Ein Fanatec-Kranz
meldete 79 Eingänge und über keine von vier verschiedenen Bibliotheken je einen
Tastendruck, und einen Steam Controller überhaupt zu lesen hieß, ihn Steam
wegzunehmen.

## Mikrofon einstellen

**Audio → Mikrofon.** Eingang wählen, Auslöser halten und den Pegelbalken
beobachten — er zeigt das Signal *nach* der Verstärkung, also das, was Whisper
tatsächlich bekommt. Zielen Sie auf Spitzen bei etwa drei Vierteln.

![Der Reiter Audio](images/audio.png)

**Die Ausgabe sollte nicht das Gerät Ihrer Simulation sein.** Der Ingenieur,
der Coach und der Aufnahmeton spielen alle hier ab; auf denselben Ausgang wie
das Spiel gerichtet, landet der Piepton in der Aufnahme.

Drücken Sie **4 s aufnehmen und transkribieren**, um zu hören, was verstanden
wurde. Während eines Tests wird nirgends etwas getippt.

## Etwas sagen

Taste halten, sagen, was Sie sagen wollen, loslassen.

1. Die Taste wird geschluckt.
2. Die Aufnahme startet **sofort** — bevor die Chatbox öffnet, damit nichts aus
   den ersten Hundertstelsekunden verloren geht.
3. Die Chat-Tasten öffnen die Chatbox des Spiels.
4. Beim Loslassen geht der Clip an Whisper, auf Ihrer eigenen CPU.
5. Der Text wird eingetippt und die Sendetasten werden ausgelöst.

Der Reiter Status zeigt, worauf der Hook scharfgeschaltet ist und wann der
Auslöser zuletzt gesehen wurde. Aktualisiert sich *Letzter Auslöser* nie, liegt
es an der Taste oder am Hook, nicht an der Transkription.

![Die Statuskarte](images/status.png)

## Und dann, wenn Sie mehr wollen

Nichts hiervon ist standardmäßig aktiv.

| | |
| --- | --- |
| [Textchat](text-chat.md) | Das Diktat selbst: Profile, Prüfen vor dem Senden, was tun, wenn nichts getippt wird |
| [Der Ingenieur](engineer.md) | Eine Stimme mit Namen, die Ihre Rundenzeiten vorliest, Autos daneben ansagt und Fragen beantwortet |
| [Der Coach](coaching.md) | Ihre Linie nach jeder Kurve gegen die eines Rivalen gezeichnet, mit dem, was zu ändern ist |
| [Stimme im Funk](voice-chat.md) | Die anderen Fahrer Ihrer Session hören, und nur die in Ihrer Nähe |
| [Sprachpakete](voicepacks.md) | Die Stimme des Ingenieurs aufnehmen oder installieren |

## Wenn etwas nicht stimmt

**Sehen Sie zuerst im Reiter Status nach.** Das ist die eine Stelle, die zeigt,
was die App glaubt: die scharfgeschaltete Taste, das fokussierte Programm, das
verwendete Profil und ein laufendes Protokoll.

![Das Protokoll im Reiter Status](images/log.png)

- **Es wird nichts getippt** — siehe [Es wird nichts getippt](text-chat.md#es-wird-nichts-getippt).
- **Es wird nichts gesprochen** — siehe [Es wird nichts gesprochen](engineer.md#es-wird-nichts-gesprochen).
- **Es wird nichts gezeichnet** — siehe [Es wird nichts gezeichnet](coaching.md#es-wird-nichts-gezeichnet).

Das Protokoll wird auch in eine Datei geschrieben. **Status → Protokollordner
öffnen** bringt Sie hin, und es ist das Erste, was einem Fehlerbericht beiliegen
sollte.
