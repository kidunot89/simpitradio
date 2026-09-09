# Getting started

Install it, tell it which key to listen for, and say something. Everything else
in these pages is optional.

![The SimPitRadio window on the Status tab](images/window.png)

## Install

Download the installer from the
[releases page](https://github.com/kidunot89/simpitradio/releases/latest) and run
it. Windows will warn you: the builds are not code-signed, so SmartScreen shows
"Windows protected your PC" and you have to choose **More info → Run anyway**.
That is what an unsigned installer looks like, and signing costs money the
project does not spend.

Setup asks one question — **which language** — with your Windows language
already chosen. That sets three things at once: the window, the speech
recognition, and the language the race engineer speaks and listens in. You can
change it later on the Language tab.

**It installs as administrator, on purpose.** Windows throws away injected
keystrokes aimed at a program running with more privilege than the sender, and
sims often run elevated. Without this, everything appears to work and nothing
ever reaches the game.

### The first launch downloads two things

Nothing large ships in the installer, so the first time you open it you are
asked to fetch:

- **the speech model**, about 250MB, which is what turns your voice into text
- **a recorded voice** for the engineer, about 45MB, if one is published in
  your language

Both are one-off. The model lives outside the install directory so an update
never costs it again. If you say "not now", the Language and Settings tabs do
the same job whenever you like.

The portable zip has no installer and therefore no language question, so it
asks the same thing on first launch instead.

## Pick a key

**Settings → Trigger.** Press *Press a key…* and then press the one you want.

![The trigger section of the Settings tab](images/trigger.png)

The key is **swallowed on its way past**, so the game never sees it — which
means you can use one the game already uses. `F13` is the default because most
keyboards do not have one and nothing else is listening for it.

**A wheel button works.** Map it to a keyboard key with
[JoyToKey](https://joytokey.net/) and bind that key here. SimPitRadio does not
read wheels directly, and the reason is in
[the engineer's notes](engineer.md#per-sim-settings): a Fanatec rim enumerated
79 inputs and never reported a press through any of four different libraries,
and reading a Steam Controller at all meant taking it away from Steam.

## Set your microphone

**Audio → Microphone.** Pick the input, hold the trigger, and watch the level
bar — it shows the signal *after* gain, which is what Whisper actually
receives. Aim for it to peak around three quarters.

![The Audio tab](images/audio.png)

**Output should not be your sim's device.** The engineer, the coach and the
recording cue all play here, and pointing it at the same output the game uses
puts the beep into the recording.

Press **Record 4s and transcribe** to hear what it heard. Nothing is typed
anywhere during a test.

## Say something

Hold the key, say what you want to say, let go.

1. The key is swallowed.
2. Recording starts **immediately** — before the chat box opens, so nothing
   said in the first few hundred milliseconds is lost.
3. The chat keys open the game's chat box.
4. On release the clip goes to Whisper, on your own CPU.
5. The text is typed in and the send keys are fired.

The Status tab shows what the hook is armed with and when the trigger was last
seen. If *Last trigger* never updates, the problem is the key or the hook, not
the transcription.

![The Status card](images/status.png)

## Then, if you want more

Nothing below is on by default.

| | |
| --- | --- |
| [Text chat](text-chat.md) | The dictation itself: profiles, reviewing before sending, what to do when nothing is typed |
| [The engineer](engineer.md) | A named voice that reads your lap times, calls cars alongside, and answers questions |
| [The coach](coaching.md) | Your line drawn against a rival's after every corner, with what to change |
| [Voice on the radio](voice-chat.md) | Hearing the other drivers in your session, and only the ones near you |
| [Voice packs](voicepacks.md) | Recording or installing the voice the engineer speaks in |

## When something is wrong

**Check the Status tab first.** It is the one place that shows what the app
believes: the armed key, the focused executable, the profile in use, and a live
log.

![The log on the Status tab](images/log.png)

- **Nothing is typed** — see [Nothing is typed](text-chat.md#nothing-is-typed).
- **Nothing is spoken** — see [Nothing is spoken](engineer.md#nothing-is-spoken).
- **Nothing is drawn** — see [Nothing is drawn](coaching.md#nothing-is-drawn).

The log is also written to a file. **Status → Open log folder** gets you there,
and it is the first thing worth attaching to an issue.
