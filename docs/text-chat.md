# Text chat

The thing SimPitRadio was built to do. Hold a key, say what you want to say,
let go — and it appears in the game's chat box, typed out, without your hands
leaving the wheel.

Everything else in the app grew out of this. The engineer, the coach and voice
chat all share the same key and the same recording; text chat is what happens
to the words when nothing else has claimed them.

## What happens when you hold the key

1. **The key is swallowed.** The game never sees the trigger itself, so it can
   be a key the game also uses.
2. **Recording starts immediately** — before the chat box is opened, not after.
   Opening the chat box takes a few hundred milliseconds and anything said
   during them would otherwise be lost.
3. **The chat keys are fired** to open the game's chat box, and the app waits
   `pre_delay_ms` for it to take focus.
4. **You let go.** Recording stops and the clip goes to Whisper, running on
   your own CPU.
5. **The text is typed in**, then the send keys are fired.

If the words turn out to be a command for the engineer or the coach, they are
answered instead and nothing is typed. That decision is deliberately narrow —
see [Talking to it](engineer.md#talking-to-it) — because the same key sends
messages to everyone in your session, and a command the app invents is a
message that silently never arrives.

## Turning it off

**Text chat → Sending to the game** is the switch to reach for mid-race when a
session turns public. Off, the trigger becomes voice and the engineer only:
no chat keys, no typing, nothing sent.

There is a second switch per game, under Profiles. "Does this game have a chat
box" is a fact about the game rather than a decision you make each session —
Assetto Corsa offline has no chat to open, so every press was sending an Enter
into the game that meant something else. Set that one once and forget it. The
app-wide switch still wins: off there is off everywhere.

## Checking a message before it goes out

By default the message is sent as soon as it is typed. Whisper does mishear
things, and in a public session a mistake is everyone's problem — so each
profile has a **Send automatically** toggle.

With it off, the message is typed into the chat box and left there. Your
trigger then decides what happens to it, without letting go of the wheel:

| Gesture | What it does |
| --- | --- |
| **Tap** | Send it |
| **Tap twice** | Clear it |
| **Hold** | Clear it and record a replacement |

The Status tab shows **waiting to send** while a message is sitting there.

If you have buttons to spare, **Settings → Trigger** also binds keys directly
to *Send waiting message* and *Clear waiting message*. Those act immediately,
with no double-tap window to wait out, and work alongside the gestures rather
than replacing them.

**A tap cannot be acted on straight away**, because until the double-tap window
closes it might be the first half of one. That wait is `review.double_tap_ms`,
about a third of a second. Set it to `0` in the config to send immediately and
give up clearing by double tap. `review.tap_ms` is the line between a tap and a
hold.

**A press while a message is pending starts recording at once**, before it is
known to be a tap or a hold. Waiting to find out would swallow the first words
of a re-record; the buffer is thrown away if it turns out to be a tap.

## Profiles

Which profile applies is decided by the executable that has focus, so several
sims can be set up at once and the right one is used without asking.

The setting that matters most is **Chat open delay** (`pre_delay_ms`). The chat
box needs a few frames to open and take focus, and typing too early loses the
opening characters. Start at 350ms and raise it if messages arrive truncated.

| Setting | What it is for |
| --- | --- |
| **Chat open delay** | How long to wait after opening the chat box before typing. The one to raise if messages arrive truncated |
| **Open chat keys** | What opens the chat box. Enter for most sims |
| **Send keys** | What sends it. Enter again, usually |
| **Cancel keys** | What closes the box without sending, for clearing a waiting message |
| **Key hold** | How long each key is held. Games poll input once a frame, so a press shorter than a frame is a press the game never sees |
| **Typing delay** | The gap between characters |
| **Maximum characters** | Messages longer than this are cut. Most sims have a limit of their own |
| **Send automatically** | Off to review before sending — see above |
| **Session plugin** | Reads who is in the session so names transcribe correctly and become mentions. Leave on *automatic* |

### Unicode or scan codes

**Typing mode** decides how characters reach the game. *Unicode* sends the
character itself and handles any keyboard layout and any alphabet. Some games
ignore it, because they read hardware scan codes instead — for those, switch to
*scancode*, which types as though the keys were pressed physically.

Scan codes are limited to what a US keyboard can produce, so accented
characters and non-Latin alphabets will not survive. Try unicode first; the
setting exists because "the game ignores what we type" needed to be a
configuration change rather than a code change.

The two are also timed differently, which is why they are separate modes.
Scan-code keys are held for `key_hold_ms` because games poll input once a
frame. Typed text is not — it goes through the message queue, and 40ms a
character would make a 200-character message take eight seconds.

## Names and vocabulary

Whisper transcribes what it hears, and driver names are exactly what it is
worst at. The session plugin reads who is actually in your session and feeds
those names in, so "Estre" comes out as "Estre" rather than "Ester".

**Vocabulary** adds your own words on top — sponsor names, a team name, the way
your friends' handles are actually spelled. Anything you find yourself
correcting is worth adding.

## Nothing is typed

**Check the Status tab first.** It shows what the hook is armed with right now
and when the trigger was last seen. If *Last trigger* never updates, the
problem is the key or the hook, not transcription.

**It has to run as administrator.** Windows discards injected input aimed at a
process running at a higher integrity level than the sender, and sims often
run elevated. The installed build asks for this automatically.

**Check the profile matches.** The Status tab logs the focused executable name;
if it is not one of your profiles, the default profile is being used and its
chat keys may not be right for that game.

**Check the chat open delay.** Messages arriving with the first characters
missing is `pre_delay_ms` set too low, every time.

**Check the game is not ignoring unicode.** If the chat box opens and nothing
appears in it, try *scancode* typing mode.
