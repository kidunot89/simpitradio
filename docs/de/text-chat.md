# Textchat

Das, wofür SimPitRadio gebaut wurde. Auslöser halten, sagen, was Sie sagen
wollen, loslassen. Es steht getippt in der Chatbox des Spiels, beide Hände
weiterhin am Lenkrad.

Alles andere in der App ist daraus gewachsen. Der Ingenieur, der Coach und der
Sprachchat teilen sich denselben Auslöser und denselben Clip. Textchat ist das,
was mit den Worten geschieht, wenn nichts anderes sie beansprucht hat.

## Was passiert, während Sie die Taste halten

1. **Die Taste wird geschluckt.** Das Spiel sieht den Auslöser nie, also darf es
   eine Taste sein, die das Spiel ebenfalls benutzt.
2. **Die Aufnahme startet sofort**, bevor die Chatbox geöffnet wird und nicht
   danach. Das Öffnen dauert einige hundert Millisekunden, und alles in dieser
   Zeit Gesagte wäre sonst verloren.
3. **Die Chat-Tasten werden gesendet**, um die Chatbox des Spiels zu öffnen, und
   die App wartet `pre_delay_ms`, bis diese den Fokus hat.
4. **Sie lassen los.** Die Aufnahme endet und der Clip geht an das Sprachmodell,
   auf Ihrer eigenen CPU.
5. **Der Text wird eingetippt**, danach werden die Sendetasten ausgelöst.

Stellen sich die Worte als Befehl für den Ingenieur oder den Coach heraus, werden
sie stattdessen beantwortet und nichts wird getippt. Diese Entscheidung ist
bewusst eng gefasst. Derselbe Auslöser schickt Nachrichten an alle in Ihrer
Session, also ist ein Befehl, den die App erfindet, eine Nachricht, die
stillschweigend nie ankommt. Siehe [Mit ihm sprechen](engineer.md#mit-ihm-sprechen).

## Ausschalten

**Textchat → An das Spiel senden** ist der Schalter, zu dem man mitten im Rennen
greift, wenn eine Session öffentlich wird. Aus wird der Auslöser nur noch Stimme
und Ingenieur: keine Chat-Tasten, kein Tippen, nichts gesendet.

Es gibt einen zweiten Schalter je Spiel, unter Profile. „Hat dieses Spiel eine
Chatbox“ ist eine Tatsache über das Spiel und keine Entscheidung, die Sie jede
Session neu treffen. Assetto Corsa offline hat keinen Chat zu öffnen, also
schickte jeder Druck ein Enter ins Spiel, das dort etwas anderes bedeutete.
Einmal setzen und vergessen. Der app-weite Schalter gewinnt weiterhin: Dort aus
ist überall aus.

## Eine Nachricht prüfen, bevor sie rausgeht

Standardmäßig wird die Nachricht gesendet, sobald sie getippt ist. Das
Sprachmodell verhört sich, und in einer öffentlichen Session ist ein Fehler das
Problem aller, darum hat jedes Profil einen Schalter **Automatisch senden**.

Ist er aus, wird die Nachricht in die Chatbox getippt und dort stehen gelassen.
Ihr Auslöser entscheidet dann, was mit ihr geschieht, ohne das Lenkrad
loszulassen:

| Geste | Was sie tut |
| --- | --- |
| **Tippen** | Senden |
| **Zweimal tippen** | Verwerfen |
| **Halten** | Verwerfen und neu aufnehmen |

Der Reiter Status zeigt **wartet auf Senden**, solange eine Nachricht dort steht.

Wenn Sie Tasten übrig haben, belegt **Einstellungen → Auslöser** auch direkt
Tasten mit *Wartende Nachricht senden* und *Wartende Nachricht verwerfen*. Die
wirken sofort, ohne Doppeltipp-Fenster, und ergänzen die Gesten, statt sie zu
ersetzen.

**Ein Tippen kann nicht sofort ausgeführt werden**, denn bis das
Doppeltipp-Fenster schließt, könnte es die erste Hälfte eines Doppeltippens sein.
Diese Wartezeit ist `review.double_tap_ms`, etwa eine Drittelsekunde. Auf `0` in
der Konfiguration wird sofort gesendet und das Verwerfen per Doppeltipp
aufgegeben. `review.tap_ms` ist die Grenze zwischen Tippen und Halten.

**Ein Druck bei wartender Nachricht startet sofort die Aufnahme**, bevor klar
ist, ob es ein Tippen oder ein Halten wird. Abzuwarten würde die ersten Worte
einer Neuaufnahme verschlucken; der Puffer wird verworfen, wenn es doch ein
Tippen war.

## Profile

Welches Profil gilt, entscheidet die Anwendung mit Fokus, sodass mehrere
Simulationen gleichzeitig eingerichtet sein können und die richtige ohne
Nachfrage verwendet wird.

Die wichtigste Einstellung ist **Chat-Öffnungsverzögerung** (`pre_delay_ms`). Die
Chatbox braucht ein paar Frames zum Öffnen und für den Fokus, und zu frühes
Tippen verliert die ersten Zeichen. Beginnen Sie bei 350 ms und erhöhen Sie,
falls Nachrichten abgeschnitten ankommen.

| Einstellung | Wofür sie da ist |
| --- | --- |
| **Chat-Öffnungsverzögerung** | Wie lange nach dem Öffnen der Chatbox gewartet wird, bevor getippt wird. Die Stellschraube bei abgeschnittenen Nachrichten |
| **Chat-Öffnen-Tasten** | Was die Chatbox öffnet. Bei den meisten Simulationen Enter |
| **Sendetasten** | Was sie abschickt. Meist wieder Enter |
| **Abbrechen-Tasten** | Was die Box ohne Senden schließt, zum Verwerfen einer wartenden Nachricht |
| **Tastenhaltezeit** | Wie lange jede Taste gehalten wird. Spiele lesen Eingaben einmal pro Frame, ein Druck kürzer als ein Frame ist ein Druck, den das Spiel nie sieht |
| **Tippverzögerung** | Der Abstand zwischen den Zeichen |
| **Maximale Zeichenzahl** | Längere Nachrichten werden gekürzt. Die meisten Simulationen haben ein eigenes Limit |
| **Automatisch senden** | Aus, um vor dem Senden zu prüfen. Siehe oben |
| **Session-Plugin** | Liest, wer in der Session ist, damit Namen richtig transkribiert werden und zu Erwähnungen werden. Auf *automatisch* lassen |

### Unicode oder Scancodes

**Tippmodus** entscheidet, wie Zeichen ins Spiel gelangen. *Unicode* sendet das
Zeichen selbst und kommt mit jedem Tastaturlayout und jedem Alphabet zurecht.
Manche Spiele ignorieren das und lesen stattdessen Hardware-Scancodes. Dafür
wechseln Sie auf *scancode*, das tippt, als wären die Tasten physisch gedrückt
worden.

Scancodes sind auf das beschränkt, was eine US-Tastatur erzeugen kann, also
überleben Akzentzeichen und nicht-lateinische Alphabete das nicht. Probieren Sie
zuerst Unicode. Die Einstellung existiert, weil „das Spiel ignoriert, was wir
tippen“ eine Konfigurationsänderung sein musste und keine Codeänderung.

Die beiden sind auch unterschiedlich getaktet, und genau darum sind es getrennte
Modi. Scancode-Tasten werden `key_hold_ms` gehalten, weil Spiele Eingaben einmal
pro Frame lesen. Getippter Text nicht. Er läuft über die Nachrichtenschlange, wo
40 ms pro Zeichen eine Nachricht mit 200 Zeichen acht Sekunden dauern ließen.

## Namen und Vokabular

Das Sprachmodell transkribiert, was es hört, und Fahrernamen sind genau das,
worin es am schlechtesten ist. Das Session-Plugin liest, wer in Ihrer Session
ist, und speist diese Namen ein, sodass „Estre“ als „Estre“ herauskommt und
nicht als „Ester“.

**Vokabular** ergänzt Ihre eigenen Wörter obendrauf: Sponsorennamen, einen
Teamnamen, die tatsächliche Schreibweise der Nicknames Ihrer Freunde. Alles,
was Sie sich immer wieder korrigieren sehen, lohnt sich einzutragen.

## Es wird nichts getippt

**Sehen Sie zuerst im Reiter Status nach.** Er zeigt, worauf der Hook gerade
scharfgeschaltet ist und wann der Auslöser zuletzt gesehen wurde. Aktualisiert
sich *Letzter Auslöser* nie, liegt es am Auslöser oder am Hook und nicht an der
Transkription.

**Es muss als Administrator laufen.** Windows verwirft eingespeiste Eingaben, die
an einen Prozess mit höherer Integritätsstufe als der Absender gehen, und
Simulationen laufen oft erhöht. Der installierte Build fragt das automatisch an.

**Prüfen Sie, ob das Profil passt.** Der Reiter Status protokolliert den Namen
der fokussierten Anwendung; ist er in keinem Ihrer Profile, wird das Standardprofil
verwendet, und dessen Chat-Tasten passen womöglich nicht zu diesem Spiel.

**Prüfen Sie die Chat-Öffnungsverzögerung.** Nachrichten, denen die ersten
Zeichen fehlen, sind jedes Mal ein zu niedriges `pre_delay_ms`.

**Prüfen Sie, ob das Spiel Unicode ignoriert.** Öffnet sich die Chatbox und es
erscheint nichts darin, probieren Sie den Tippmodus *scancode*.
