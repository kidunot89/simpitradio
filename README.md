<img src="docs/images/logo.png" alt="" width="96" align="left">

# SimPitRadio

Hold a button, say it, and it goes into the game's chat box.

<br clear="left">

Hold the trigger, say what you want, let go. SimPitRadio opens the chat box,
types what you said and sends it, with both hands still on the wheel. The
speech model runs on your own CPU. Nothing you say leaves your machine.

The trigger is meant to be a button on the wheel. Bind one directly, or put F13
on it with your wheel's own software or JoyToKey, and SimPitRadio sees an
ordinary key.

Two things have grown on top of text chat, both off until you switch them on.
An **engineer** talks to you and answers what you ask it. A **coach** draws the
segment you have just driven against a rival's line and says what to change.

## Roadmap

**Where it is today.** Text chat works in any game with a chat box you open
with a key. One sim is verified: Le Mans Ultimate, which ships with a profile
and is the only one the engineer and the coach have been measured against.
Session plugins exist for iRacing, Assetto Corsa, Automobilista 2 and Project
CARS, and all four are unverified. Each is written from its sim's published
memory layout and checked against a block built by hand, which proves the
offsets agree with each other and proves nothing about the running game.
iRacing is the one the profile picker labels experimental, because nobody
working on SimPitRadio owns a copy of it. Any other sim does text chat once you
add a profile, which takes about a minute: see
[Adding your sim](#adding-your-sim).

### Next to be verified

- **Automobilista 2.** The plugin is written and reads the shared memory block.
  What it has never had is a session in the running game to check it against.
  Verifying it means sitting in the car and confirming the driver list, the
  standings and the flags against what is on screen.
- **Assetto Corsa EVO.** Covered by the Assetto Corsa plugin, which reads the
  same shared pages as Competizione. EVO moved some of them, so the layout has
  to be read against a running copy rather than assumed.

Neither is a large job. Both are mostly a matter of somebody sitting in the car
with the app open. The engineer asks more of a sim than text chat does: where
every car is, lap and sector times, flags, fuel, and for the coach the
across-track offset. A plugin can supply the first few and not the rest, and
[Session plugins](#session-plugins) says what each flag means.

### Languages

The app speaks English. Everything it says already goes through a catalogue and
is extracted to `apps/client/src/pitradio/locale/template.json`, so a language is
a translated copy of that file dropped into the same folder. The app finds it and
offers it without a release. What is missing is the translations themselves:

**German · French · Italian · Spanish · Portuguese · Polish · Korean ·
Japanese · Dutch**

Two things are worth knowing before starting one. Text chat is a separate
question: Whisper already transcribes all of these and the Language tab picks
the model for it, so speaking to the app in your own language works today. The
engineer's voice is a folder of recordings, so a translated catalogue with no
voice pack behind it falls through to the Windows voice for whatever the pack
does not hold. See [docs/voicepacks.md](docs/voicepacks.md).

### More sim profiles and plugins

So more games work without you adding anything. A profile is what lets
SimPitRadio type into a game's chat box. A session plugin is what lets the
engineer know who is on track around you. The quickest way to get your sim on
the list is
[an issue](https://github.com/kidunot89/simpitradio/issues/new/choose) saying
what it is called.

### AI Coaching

The coach you have looks at the segment you have just driven and says what went
wrong in it. It runs on your machine and it has no memory. Every corner is
judged on its own.

The AI coach watches across corners, laps and sessions, and looks for the thing
you do every time. A driver who brakes fractionally too late into every
right-hander, or who unwinds the wheel a beat early on every exit, has one habit
and not forty mistakes. Hearing about it forty times does not fix it. The AI
coach names the habit, then works on it with you: what to change, whether the
change is taking, and when it has stuck.

It also drives. Given an offline practice session it sets a quick lap in your
own car on your own setup, so there is a reference lap to work towards when
nobody faster is on track.

### AI Engineer

The engineer you have answers a fixed set of questions from what the sim
publishes: the fastest lap, who is ahead, how much fuel is left. Everything it
can be asked is known in advance, because everything it can say is a recording.

The AI engineer reads the telemetry as the race happens and answers in its own
words. Whether that stop works. What the weather is doing to your tyres. What
the car has been telling you for the last ten laps. Whether to cover the stop in
front. You ask it the way you would ask a person, and the answer comes from what
is going on rather than from a list.

Both need a model too large to run on the machine already running the sim, so
both run on rented GPU hardware and are billed by the hour you use. **Nothing
else about SimPitRadio changes.** Everything described below runs on your own
machine, with no account and no connection, and always will.

![The SimPitRadio window](docs/images/window.png)

---

## Install

Download the latest `simpitradio-setup-*.exe` from
[Releases](https://github.com/kidunot89/simpitradio/releases) and run it.

**Windows will warn you about it.** Two separate things cause this, and both
are expected:

- **SmartScreen: "Windows protected your PC".** These builds aren't
  code-signed, so Windows has no publisher to attribute them to. Choose **More
  info → Run anyway**.
- **Antivirus may flag or quarantine it.** SimPitRadio installs a global keyboard
  hook and synthesises keystrokes. That is a keylogger's behavioural signature.
  It is also precisely what text chat requires. There is no way to swallow your
  trigger key and type into a game without it.

If you'd rather not take that on trust, every release publishes
[`SHA256SUMS`](https://github.com/kidunot89/simpitradio/releases) so you can check that
what you downloaded is what was built. Every release is also a portable `.zip`,
if you would rather not run an installer at all.

### It needs to run as administrator

The installed build asks for this on its own. A Windows rule called UIPI is
why: a process at normal privilege cannot send input to a window owned by an
elevated one. If your sim or its launcher runs elevated and SimPitRadio does
not, **every keystroke is silently discarded.** No error, no exception, nothing
typed. It is the commonest cause of "it does nothing".

The Status tab says so when the app is not elevated.

---

## First run

1. Open SimPitRadio. On first launch it downloads the speech model (~250MB,
   once). The window shows the progress.
2. Go to **Audio**, pick your microphone, and press **Record 4s and
   transcribe**. Nothing is typed anywhere. It proves the microphone and the
   model work. If the level bar barely moves while you speak, raise
   **Microphone gain**; the bar shows the signal after gain, which is what
   Whisper receives.
3. Set the trigger. See below.
4. Start your sim, hold the trigger, say something, release.

### About F13

The default trigger is **F13**, because no sim binds it. Holding it can never
also do something in the game while you are talking.

Almost no keyboard has an F13 key and you do not need one. Put it on the wheel:
assign F13 to a button with **your wheel's own software**, or map one with
**[JoyToKey](https://joytokey.net/)**, and SimPitRadio sees an ordinary keypress.
Reach for that if your wheel came with software you already run, which most do.

SimPitRadio can also **bind a wheel button directly**, with nothing in between.
See below. Either route works. The direct one needs no other software, and the
F13 one works with any device at all, including one SimPitRadio cannot open.

Whatever you pick, **Settings → Trigger** shows what is bound now, and you never
have to type a key name. **Press a key…** binds whatever you press next,
including a combination like `Ctrl+F12`, and swallows the press, so binding Enter
does not also actuate whatever is behind the window.

### Binding a wheel or gamepad button

**SimPitRadio reads wheels and gamepads directly.** Open **Settings → Trigger**,
click **Capture a wheel button**, and press the button you want to talk with.
It is bound, and it survives a restart.

The device is opened shared rather than seized, so the game keeps receiving the
button as well. You can bind one the sim already uses, though a spare one is
tidier. Presses arrive in about **4ms**.

**If the button does nothing:**

- **Press it during the fifteen seconds the capture is listening.** Buttons
  already held down when capture starts are ignored, so a rotary or a switch
  that rests in the "on" position has to be moved rather than found.
- **Check the Status tab.** Press the button. The **Last trigger** row stamps
  the time the moment a press is seen. If it updates, the binding works and
  whatever is wrong is in Settings.
- **Run as administrator.** The installed build self-elevates.

**Or wire the wheel to a keyboard key instead**, which is the other route from
[About F13](#about-f13) and the one to reach for if your wheel's own software is
already running, or if the device does not appear here at all: map the button
with **[JoyToKey](https://joytokey.net/)** and SimPitRadio sees an ordinary
keypress. It has always worked and still does.
- **Run both as administrator.** SimPitRadio's installed build self-elevates. If
  JoyToKey is not elevated, Windows will not let its synthetic keypresses reach
  an elevated SimPitRadio, and nothing happens with no error at all.
- **Does the key work from the keyboard?** Bind the trigger to something you can
  press yourself, like `scrolllock`, and test that first. It separates a JoyToKey
  problem from a SimPitRadio one.

**Why the keyboard route is still here.** Reading the wheel directly was tried
four times before it worked: SDL3, SDL2, XInput and the Windows multimedia API.
Between them they could not read a Fanatec rim, which enumerated 79 inputs and
never reported a press, or a Steam Controller, which was only visible if you
took the device away from Steam and broke the owner's own shortcuts. All four
were removed. SimPitRadio now opens the wheel through DirectInput and shares it
with the game rather than seizing it, and the same rim reports 108 buttons. A
device DirectInput cannot open still reaches the keyboard hook through JoyToKey.

To try it at a desk with no wheel plugged in, `scrolllock` and `pause` are good
choices: on most keyboards, rarely bound by sims.

Whatever you pick is **swallowed**. It never reaches the game, so do not use a
key the sim needs.

Closing the window minimises to the tray and the trigger keeps working. Quit
from the tray menu to stop the app.

---

## Checking a message before it goes out

By default the message goes out as soon as it is typed. Whisper does mishear
things, and in a public session a mistake is everyone's problem, so each profile
has a **Send automatically** toggle (Profiles → *your sim*).

With it off, the message is typed into the chat box and left there. The trigger
then decides what happens to it, with your hands still on the wheel:

| Gesture | What it does |
| --- | --- |
| **Tap** | Send it |
| **Tap twice** | Clear it |
| **Hold** | Clear it and record a replacement |

The status bar shows **waiting to send** while a message is sitting there.

If you have buttons to spare, **Settings → Trigger** binds keys straight to
*Send waiting message* and *Clear waiting message*. Those act at once, with no
double-tap window to wait out, and they work alongside the gestures.

A single tap might turn out to be the first half of a double, so sending waits
for the double-tap window to close. That is about a third of a second. Set
`review.double_tap_ms` to `0` in the config to send immediately and give up
clearing by double tap. `review.tap_ms` is the line between a tap and a hold.

---

## Using SimPitRadio

> Screenshots are generated from the running app by
> `python packaging/screenshots.py`, each cropped to the control being
> described, so they stay correct as the layout moves.

### The Status tab: is it listening?

![Status](docs/images/status.png)

Everything that answers "why did nothing happen?" is on this tab.

- **Listening for.** What the hook is armed with now, read from the hook rather
  than from the config file. A key you saved that never applied shows up here as
  the old one.
- **Last trigger.** Stamped the moment the key is detected, before any audio or
  transcription work. If this updates and nothing else does, SimPitRadio saw your
  key and whatever is wrong is downstream. If it does not update, the key never
  reached it.
- **Focused app.** The executable name, which is the profile key. It is how you
  add a sim.

Below it, the live log:

![Log](docs/images/log.png)

`pre-keys sent` means the chat box was asked to open. `transcribed` shows what
Whisper heard, before any mention matching. `sent N chars` closes the cycle.

### Settings → Trigger

![Trigger](docs/images/trigger.png)

Three key bindings. All are optional except the trigger itself.

| Binding | What it does |
| --- | --- |
| **Trigger key** | hold to talk; swallowed, so it never reaches the game |
| **Send waiting message** | sends a message left in the chat box |
| **Clear waiting message** | discards it |

**Press a key…** binds whatever you press next, including `Ctrl+F12`, and
swallows it, so binding Enter does not also actuate whatever is behind the
window.

A wheel or gamepad button can be captured here directly, or mapped to a key with
JoyToKey first. See
[Binding a wheel or gamepad button](#binding-a-wheel-or-gamepad-button).

### Settings → Appearance

![Appearance](docs/images/appearance.png)

Light, dark, or follow the desktop. Applies on the next start.

### Profiles, one per sim

![Profiles](docs/images/profiles.png)

The setting that matters most is **Chat open delay**. The chat box needs a few
frames to open and take focus, and typing into it too early loses the opening
characters. Start at 350ms and raise it if messages arrive with the front
missing.

Turn **Send automatically** off to read a message before it goes out. See
[Checking a message before it goes out](#checking-a-message-before-it-goes-out).

**Session plugin** reads who is in the session, so names transcribe correctly and
become mentions. Leave it on *automatic* unless you have a reason.

### Language

![Language](docs/images/language.png)

SimPitRadio picks your desktop's language the first time it runs. Whisper has no
per-language models: the `.en` builds are English-only and the rest are
multilingual. Choosing a language and a size here works the model out for you,
and changing it downloads the new model on save.

### Audio

![Audio](docs/images/audio.png)

Pick the microphone, then **Record 4s and transcribe**. Nothing is typed
anywhere. It proves the microphone and the model work. If the level bar barely
moves while you speak, raise **Microphone gain**. The bar shows the signal
*after* gain, which is what Whisper receives.

### Engineer

A named voice that talks back: your lap times, cars alongside, flags, fuel,
damage, and the answer when you ask it something. Two voice packs ship with it,
Norman and Claudia. Anything a pack does not hold falls through to the Windows
voice, which always includes drivers' names.

Give it somebody to focus on and it tells you, corner by corner, how your lap
compared:

> Chief, focus on P3
>
> *Targeting N.Tandy. Best lap, one twenty five point two seven.*
>
> *Turn one, N.Tandy was faster on the exit, six tenths.*

It uses the same trigger as everything else. **Engineer → Enable** turns it on.
**Behaviours** on the same tab chooses which of its calls it makes, lap times,
the spotter, flags and damage, each with its own repeat interval.

![Voice](docs/images/voice.png)

How it sounds is set in **Settings → Voice**. The coach can share that voice or
have its own. Out of the box they are two people, Norman engineering and Claudia
coaching, so you can hear which of them is talking without listening to the
words.

**[docs/engineer.md](docs/engineer.md)** is the full guide: everything it says,
what each sim can answer, other languages, and installing a recorded voice
pack.

### Coaching

![Coaching](docs/images/coaching.png)

Pick somebody to study and, every time you finish a segment, the panel draws
your line against theirs and the coach says what to do differently.

> *Tosa, you gave up mid-corner speed because you were still on the brake at
> the apex, and they apex later so their exit straightens out sooner.*

It reads your pedals, your wheel and your gear as well as the clock, so what it
says is the cause and not the lap time again. Lock a wheel or put one off the
road and it says so at once, while you can still feel what you did.

#### Turning it on

Coaching starts on a command rather than a tick-box. You ask for it when you
want it and it stands down when you say so. Hold the trigger and say any of
these. They are all two words or more, so the coach's name is optional.

| To do this | Say |
| --- | --- |
| Start coaching | **coach me** · *lead me to it* · *show me the lines* · *start coaching* |
| Stop | **stop coaching** · *stop the coaching* · *no more lines* |
| Choose who to measure against | **study Estre** · *focus on P3* · *keep an eye on the LMP2 leader* |
| Measure against your own best | **focus on me** · *study my best* · *focus on my ideal lap* |
| Go back to picking automatically | **default focus** · *automatic focus* |
| Hear what is running | **what coaching is on** |
| Redraw the corner you just did | **last corner** · *that corner* |

**You do not have to choose a rival.** Ask it to focus on *you* and the second
line becomes your own ideal lap: your best through each corner, stitched into
one lap you have never actually driven. An empty practice session still has
somebody to race, and on your own best there is nowhere to hide.

Every call comes in the coach's voice rather than the engineer's, so you can
always hear which of the two is talking.

#### The trail-braking trainer

![Trail-braking trainer](docs/images/brake_trainer.png)

A piano note each time a tyre reaches the edge of grip under braking, so the
brake release is something you hear instead of something you work out from a lap
time afterwards. Three to six notes down a braking zone is a clean release. One
note and then silence means you came off the brake too fast.

| To do this | Say |
| --- | --- |
| Start | **train on the brakes** · *let's start training on the brakes* · *brake training* |
| Stop | **end brake training** · *stop training on the brakes* |

It learns your car's rolling radius over the first few braking zones, so it
works in any class and with the bias anywhere you like. **Coaching →
Trail-braking trainer** sets whether it arms with the session and how loud the
notes are.

#### What gets coached

**The circuit is worked out from your own laps.** After a few laps SimPitRadio
knows the shape of the road and cuts it into segments, so it works on any track
in any sim, including one nobody has ever catalogued. Where there is a catalogue
you get names: "Tosa" rather than "turn seven".

A segment is a corner plus the run into it and the run out, because that is what
you drive:

- The **run-up** goes back to where you got on the brakes, capped at 250m. The
  length moves with you. Brake later and the segment starts later.
- The **run-out** is 50m past the exit, enough to show where the car came out
  and where it was pointed.
- **Two corners you brake once for are one segment.** Club and Vale is one thing
  to drive and one thing to look at. So is Sebring's hairpin pair.
- **Bends you take flat are skipped.** There is no braking point to move and no
  entry speed to carry. They stay on the map and keep their names, and turning on
  **Straights and flat-out sections** puts them in front of you anyway.

![Coach notifications](docs/images/coach_notifications.png)

**Coaching → Notifications** turns each kind of call on and off on its own: the
**segment analysis** after each corner, **mistakes as they happen** such as a
locked wheel or a trip off the road, and **where they were quicker** once a lap.
These are separate from the engineer's Behaviours, so turning the coaching down
leaves the spotter where it was.

#### The diagram

The panel holds three segment diagrams: one arriving, one being talked about in
the middle, one on its way out. Where a diagram sits is how far the coach has
got, so a glance is enough. The diagrams float over the game with nothing behind
them.

Your line is drawn in **orange through red** and a rival's in **indigo through
cyan**, and the shade says what your feet were doing. The hot end of each ramp is
braking, the middle coasting, the light end on the power. The road is a dark
ribbon between two white lines, drawn from the sim's own track-edge reading, so a
wheel you put outside the line is drawn outside the line.

![Segment diagram settings](docs/images/segment_diagram.png)

**Coaching → Segment diagram** places it, sizes it, and sets which way it
runs. **Show the panel** puts three sample corners up so you can drag it where
you want it and size it against the real thing.

### History

![History](docs/images/history.png)

Every message, with what was heard and what was typed. **Re-send** retypes one
after a three-second countdown. The countdown is there so you can focus the game
first. Without it the message goes into SimPitRadio's own window.

### Voice chat

Hold the same trigger and the other SimPitRadio users in your session hear you.
It is off until you switch it on.

Proximity is decided on **your** machine from the sim's own data, and nothing
about where you are is ever sent. A driver a straight away is quieter than one
alongside. See **[docs/voice-chat.md](docs/voice-chat.md)**.

---

## Adding your sim

Profiles are keyed on the game's executable name, and SimPitRadio tells you what
that is:

1. With the sim focused, tap the trigger key once.
2. Alt-tab to SimPitRadio. The **Status** tab shows **Focused app**, which is
   the executable name.
3. Go to **Profiles → Add**, and it offers that name.
4. Set the keys your sim uses for chat. For most sims that is Enter to open and
   Enter to send.

Then tune it. The setting that matters is **Delay after opening chat**
(`pre_delay_ms`). The chat box needs a few frames to open and take focus, and if
SimPitRadio starts typing too early the opening characters vanish. Start at
350ms and raise it if you lose the beginning of messages.

Config changes take effect on the next trigger, with no restart. The file lives
at `%APPDATA%\pitradio\config.json` if you would rather edit it directly. The
window and a text editor write the same file.

**Got a sim working?** A profile that works is worth more to other people than
almost anything else here. Open an issue with the executable name and the keys.

---

## Nothing is typed into the game

Work down this list. It is ordered by how often each one is the answer.

1. **Is SimPitRadio running as administrator?** See above. This is most of them.
2. **Is the game in borderless windowed mode?** Exclusive fullscreen swallows
   synthetic input in some titles. Try borderless before anything else here.
3. **Does the chat box open at all?** Check the log (Status → Open log folder).
   If you see `pre-keys sent` but no text appears, the keys are reaching the
   game and the problem is the typing. If the chat box never opens, the
   `pre_keys` are wrong for that sim.
4. **Are the first characters missing?** Raise `pre_delay_ms`.
5. **Does the chat box open but stay empty?** The game is ignoring Unicode
   input. Set that profile's **Text injection** to `scancode`, which types
   character by character using real key presses. It is slower and limited to
   what your keyboard layout can produce, and some games accept nothing else.
6. **Still nothing?** A few games read input below the level `SendInput` can
   reach, usually for anti-cheat. The
   [Interception driver](https://github.com/oblitum/Interception) is the only
   real workaround, and it is a kernel driver, so treat it as a last resort.
   SimPitRadio does not use it.

The log records the executable name and a timing for every stage of every
trigger: when the chat box opened, how long transcription took, when the message
went. It turns "it felt wrong" into something you can read.

---

## Session plugins

A session plugin reads live data from a sim. Today that means the driver list,
which SimPitRadio uses two ways. It feeds the names to Whisper so they are
transcribed correctly, and it rewrites them in the message: say "tell Tandy to
box" and send `tell @Tandy to box`.

**Le Mans Ultimate ships with one**, reading LMU's shared memory with nothing
installed game-side. Assign it in **Profiles → Session plugin**; the bundled LMU
profile already has it. The choice lives on the profile, so a plugin that suits
two games can be assigned to both.

However you say the name, the mention comes out in the form sims put on screen:

| You say | It sends |
| --- | --- |
| "Geoff Taylor is quick" | `@G.Taylor is quick` |
| "tell Taylor to box" | `tell @G.Taylor to box` |
| "Geoff is quick" | `@G.Taylor is quick` |
| "de Vries is catching" | `@N.de Vries is catching` |

That is why the name is replaced rather than prefixed. `@G.Taylor` is what every
other driver has on their own screen, so they know at once who is meant.

You can also name somebody by their **standings position**, which is often easier
than a name you cannot pronounce or did not catch:

| You say | It sends |
| --- | --- |
| "tell P3 to move over" | `tell @N.de Vries to move over` |
| "P1 is pulling away" | `@M.Verstappen is pulling away` |
| "third place is quick" | `@N.de Vries is quick` |

A position nobody is in, "P40" in a twenty-car race, is left as you said it.
Turn this off under **Profiles → Le Mans Ultimate options**.

First names that double as racing speech are never matched on their own. "Max
attack", "nick the inside line" and "will do" stay as they are, and all three are
still recognised inside a full name. Turn first-name matching off with
`mentions.match_first_names`.

The `@` is plain text. Neither LMU nor rFactor 2 chat supports markup, so there
is no bold and the game attaches no meaning to it. It is a human convention, like
writing somebody's name in caps.

Feeding the names to Whisper is the half that matters more. Whisper mangles a
proper noun it has no reason to expect, and telling it who is in the session
beats any amount of matching after the fact.

A plugin can expose its own options, which appear in the profile editor once the
plugin is assigned. They are stored per profile, so one plugin can be set up
differently for two games.

Plugins are compiled into the app, so there is no way to add one after
installing and adding a sim means a new release. Say which sim and what it
publishes in [an issue](https://github.com/kidunot89/simpitradio/issues/new/choose).

---

## Accuracy

The **Vocabulary** tab feeds Whisper a list of words to expect. It ships with
corner names, series terms and radio phrases, and it measurably improves proper
nouns. Add your regular team mates' names, your series' jargon and the tracks you
run often.

Below the editable list is the **runtime vocabulary**: the terms the session
plugin supplies for the session you are in, and the exact prompt Whisper receives
once the two are combined. If a name keeps coming out wrong, that is where you
see whether it was ever offered in the first place.

Transcription runs on the **CPU, deliberately.** The GPU belongs to the sim. A
model grabbing VRAM mid-corner costs frames and a few hundred milliseconds of CPU
transcription does not.

### Other languages

The **Language** tab configures which languages you want and how large a model
to use for each. Add a language, pick a size, press **Save and download**, and
the models are fetched into the cache.

**Whisper has no per-language models**, and that shapes the choices. There are
English-only builds (`tiny.en` … `medium.en`) and multilingual builds (`tiny` …
`large-v3`), and every multilingual build handles all the languages. Picking a
size per language still buys you something: multilingual `small` is weaker than
`small.en`, so a second language often wants a bigger model than English does.
"Medium Spanish, small English" means `medium` when transcribing Spanish and
`small.en` when transcribing English.

Only one language is active at a time. The others stay configured and
downloaded, so switching is instant.

Sizes trade accuracy against latency, and latency is what you feel mid-stint:

| Size | Download | Notes |
| --- | --- | --- |
| tiny | ~75 MB | fastest, least accurate |
| base | ~145 MB | fast |
| small | ~480 MB | the default; a good balance on CPU |
| medium | ~1.5 GB | noticeably slower on CPU |
| large | ~3 GB | often too slow to use between corners |

Replace the **Vocabulary** text when you change language. It ships as English
racing terms, and a prompt in the wrong language works against you.

---

## Updates

![Updates](docs/images/updates.png)

SimPitRadio checks GitHub for new releases and can install them itself. Automatic
installs are **off by default** and always held back while a sim is in focus.
Restarting the app mid-stint would be worse than updating a day later.

**What the verification does and does not prove.** Downloads are checked against
the `SHA256SUMS` published with the release before anything runs. That proves the
download arrived intact. It proves nothing about who produced it. The builds are
unsigned, so if the repository or a release were compromised the updater would
install whatever was there, with administrator rights. That is why auto-install
is opt-in. Code signing would fix it properly and is the obvious next step.

Updating closes SimPitRadio, installs, and reopens it. Your config, your logs and
the cached speech model live outside the install directory, so none of them are
touched and an update never re-downloads the model.

Turn the check off entirely with `--no-update-check`, or in
`config.json` under `updates`.

---

## Privacy

- The speech model runs entirely on your machine. Audio is never uploaded and
  never written to disk.
- The app makes two kinds of network request: downloading the speech model on
  first run, and checking GitHub for updates.
- Transcription history is held in memory and goes when you quit.
- The keyboard hook acts on the trigger and on nothing else. Every other key is
  passed straight through untouched.

---

## Reporting a fault

[Open an issue](https://github.com/kidunot89/simpitradio/issues/new/choose), and say
what the Status tab shows. Almost everything in this app fails silently, so the
log is usually the only thing that says why.

Two contributions are worth more than any bug report, and neither needs code:

- **A profile for a sim.** The Status tab shows the executable name; that plus
  your sim's chat keys is a complete contribution.
- **A translation.** Every string in the interface is one entry in one JSON
  file, and a partial translation is fine.

---

## Licence

SimPitRadio is made by **AxisTaylor, LLC** and is proprietary software. Installing or
using it means accepting the [end-user licence](LICENSE.md).

Releases up to and including **v0.3.0** were published under the MIT
licence and stay that way for anyone who has them. That grant cannot be
withdrawn and is not being withdrawn. Later releases are under the licence
above.

Copyright © 2026 AxisTaylor, LLC. All rights reserved.
