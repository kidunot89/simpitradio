# Erste Schritte

Installieren, sagen, auf welche Taste gehört werden soll, und etwas sagen.
Alles danach ist optional.

![Das SimPitRadio-Fenster im Reiter Status](images/window.png)

## Installation

Laden Sie das Installationsprogramm von der
[Releases-Seite](https://github.com/kidunot89/simpitradio/releases/latest) herunter
und führen Sie es aus. Windows wird warnen: Die Builds sind nicht signiert, also
zeigt SmartScreen „Der Computer wurde durch Windows geschützt“ und Sie müssen
**Weitere Informationen → Trotzdem ausführen** wählen. So sieht ein unsigniertes
Installationsprogramm aus, und eine Signatur kostet Geld, das dieses Projekt
nicht ausgibt.

Das Setup stellt eine Frage. **Welche Sprache**, mit Ihrer Windows-Sprache
bereits ausgewählt. Damit sind drei Dinge auf einmal gesetzt: das Fenster, das
Sprachmodell und die Sprache, in der der Ingenieur spricht und zuhört. Der
Reiter Sprache ändert das später.

**Es installiert sich mit Administratorrechten, und das mit Absicht.** Windows
verwirft eingespeiste Tastenanschläge, die an ein Programm mit höheren Rechten
als der Absender gehen, und Simulationen laufen oft erhöht. Ohne das sieht alles
so aus, als funktioniere es, und nichts erreicht jemals das Spiel.

### Beim ersten Start werden zwei Dinge geladen

Im Installationsprogramm steckt nichts Großes, deshalb werden Sie beim ersten
Öffnen gefragt, ob Folgendes geholt werden soll:

- **das Sprachmodell**, etwa 250 MB, das aus Ihrer Stimme Text macht
- **ein Sprachpaket** für den Ingenieur, etwa 45 MB, sofern eines in Ihrer
  Sprache veröffentlicht ist

Beides einmalig. Das Modell liegt außerhalb des Installationsverzeichnisses,
damit ein Update es nie erneut kostet. Sagen Sie „Jetzt nicht“, holen die
Reiter Sprache und Einstellungen es, wann immer Sie wollen.

Der portable Build hat kein Installationsprogramm und keine Sprachabfrage —
er fragt stattdessen beim ersten Start.

## Eine Taste wählen

**Einstellungen → Auslöser.** Drücken Sie *Taste drücken…* und dann die
gewünschte Taste.

![Der Auslöser-Bereich im Reiter Einstellungen](images/trigger.png)

Die Taste wird **im Vorbeigehen geschluckt**, das Spiel sieht sie also nie —
Sie können daher eine nehmen, die das Spiel bereits benutzt. `F13` ist die
Vorgabe, weil die meisten Tastaturen keine haben und nichts sonst darauf hört.

**Eine Lenkradtaste funktioniert ebenso.** Drücken Sie in der Zeile
**Lenkradtaste** auf *Taste drücken…* und dann die gewünschte Taste.
SimPitRadio öffnet das Lenkrad, ohne es dem Spiel wegzunehmen — die Simulation
liest also weiter jede Taste, auch diese. Halten, um zu sprechen, genau wie bei
der Tastatur. Beide bleiben gleichzeitig scharfgeschaltet, sodass Sie beide
belegen und jeweils die nähere nutzen können.

Der andere Weg führt über die eigene Software Ihres Lenkrads oder über
[JoyToKey](https://joytokey.net/): Legen Sie `F13` auf eine Taste und belegen
Sie hier `F13`. Greifen Sie darauf zurück, wenn auf dem Lenkrad bereits eine
Software läuft, der Sie vertrauen, oder wenn SimPitRadio das Gerät nicht öffnen
kann.

## Mikrofon einstellen

**Audio → Mikrofon.** Eingang wählen, Auslöser halten und den Pegelbalken
beobachten. Er zeigt das Signal *nach* der Verstärkung, also das, was das
Sprachmodell bekommt. Zielen Sie auf Spitzen bei etwa drei Vierteln.

![Der Reiter Audio](images/audio.png)

**Die Ausgabe sollte nicht das Gerät Ihrer Simulation sein.** Der Ingenieur,
der Coach und der Aufnahmeton spielen alle hier ab; auf denselben Ausgang wie
das Spiel gerichtet, landet der Piepton in der Aufnahme.

Drücken Sie **4 s aufnehmen und transkribieren**, um zu hören, was verstanden
wurde. Während eines Tests wird nirgends etwas getippt.

## Etwas sagen

Auslöser halten, sagen, loslassen.

1. Die Taste wird geschluckt.
2. Die Aufnahme startet **sofort**, bevor die Chatbox öffnet. Nichts, was in
   den ersten Hundertstelsekunden gesagt wird, geht verloren.
3. Die Chat-Tasten öffnen die Chatbox des Spiels.
4. Beim Loslassen geht der Clip an das Sprachmodell, auf Ihrer eigenen CPU.
5. Der Text wird eingetippt und die Sendetasten werden ausgelöst.

Der Reiter Status zeigt, worauf der Hook scharfgeschaltet ist und wann der
Auslöser zuletzt gesehen wurde. Aktualisiert sich *Letzter Auslöser* nie, liegt
es an der Taste oder am Hook, nicht an der Transkription.

![Die Statuskarte](images/status.png)

## Und dann, wenn Sie mehr wollen

Der Ingenieur, der Coach und der Sprachchat sind alle aus, bis Sie sie einschalten.

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

- **Es wird nichts getippt.** Siehe [Es wird nichts getippt](text-chat.md#es-wird-nichts-getippt).
- **Es wird nichts gesprochen.** Siehe [Es wird nichts gesprochen](engineer.md#es-wird-nichts-gesprochen).
- **Es wird nichts gezeichnet.** Siehe [Es wird nichts gezeichnet](coaching.md#es-wird-nichts-gezeichnet).

Das Protokoll wird auch in eine Datei geschrieben. **Status → Protokollordner
öffnen** bringt Sie hin, und es ist das Erste, was einem Fehlerbericht beiliegen
sollte.
