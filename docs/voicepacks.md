# Voice packs

The engineer sounds like a person only if it has recordings of one. A voice
pack is that: a folder of WAV files, one per phrase, that the engineer plays
instead of speaking through the Windows synthesiser.

Anything it says that is not in the pack — your name, a lap time, a driver it
has never heard of — is still spoken by the Windows voice. A pack does not have
to be complete to be worth having.

## Three ways to get one

**Install a published one.** *Settings → Voice* lists the packs published
for download and installs one on request, verifying its checksum before it
unpacks anything. This is the route for a language other than your own.

**Record it yourself**, in the window. This is the route with no ceiling and
the one the app is built around: *Settings → Voice → Create a voice model*.

**Generate a base with Piper**, offline, and re-record over the parts you care
about. Useful if you want something correct and pleasant immediately, or would
rather not read 171 phrases before driving.

They are not exclusive. A Piper pack is an ordinary pack, so any phrase in it
can be replaced with your own take later.

### Why not voice cloning

This was tried first and abandoned, and the reason is worth knowing before you
go looking for it.

A cloned voice was generated for this project from nearly three minutes of
clean reference audio. Put back through the app's own speech recogniser, every
take of "five" came back as "bye", "four" as "boy", and "zero" as "yo".

The inventory is why. **141 of its 171 phrases are one or two words**, and
short text is exactly where a cloning model is at its worst: XTTS generates
autoregressively, deciding for itself when to stop, and with a two-word phrase
there is almost nothing constraining that decision. Piper is a VITS-style model
— one forward pass from phonemes to waveform, with no sampling loop to wander
off. It cannot say a different word, which on this inventory matters more than
timbre does.

Crew Chief solves the same problem the same way: its packs are *recorded*, and
its 11,176 driver names and 1,052 number clips were read by a person.

## Recording your own

*Settings → Voice → Create a voice model* opens a recorder: a phrase to read, a
countdown, a take, and playback to check it.

It is less work than it sounds. The whole inventory is **about forty minutes at
three takes each**, and it resumes — so it can be done in sittings, and a pack
covering half the phrases works from the moment you save it.

A few things decide whether the result is usable:

- **Off to the side of your mouth**, a couple of finger widths away — not in
  front of it. A boom mic directly in the airflow clips on every *p* and *b*,
  and clipping cannot be undone afterwards.
- **A quiet room.** A fan or a PC under the desk ends up in every clip, and
  every clip is played back to you mid-race through a headset.
- **Consistent distance.** Do not lean around between takes. Clips recorded at
  four different distances sound like four different people.
- **Turn Windows' microphone boost off.** It is a compressor, and it pumps the
  room noise up between words.

Read them the way an engineer would say them on the radio — flat, unhurried,
slightly bored. The engineer is not performing.

## Generating a base with Piper

Piper runs offline, from the packaging scripts rather than inside the app:

```
pip install -r packaging/requirements-voices.txt
python -m piper.download_voices --download-dir models/piper en_GB-alan-medium
python packaging/make_piper_pack.py --name Piper
```

To build with a particular model:

```
python packaging/make_piper_pack.py --name Piper --model models/piper/en_GB-alan-medium.onnx
```

**Offline, and not in the app, on purpose.** Piper is fast enough on a CPU to
be tempting to call at speak time. That would put a 63MB model and an ONNX
runtime inside a build whose last four broken releases were all native
dependencies that failed to get collected. A pack is a folder of WAVs;
generating it here costs the app nothing and cannot break a build.

It is not *your* voice, and nothing pretends otherwise. It is a base that is
correct and pleasant, over which any phrase can be re-recorded in the window.

**Japanese needs one more package, and fails confusingly without it.** The
Japanese model asks Piper for `pyopenjtalk` to turn text into phonemes, and
without it every phrase produces no audio — reported as
`wave.Error: # channels not specified`, which is the empty output file rather
than the real cause. Upstream `pyopenjtalk` ships source only and wants CMake
and a C++ compiler; `pyopenjtalk-plus` is a fork that ships wheels under the
same import name, and it is in the requirements file above.

## What a pack looks like

A pack is a folder with a `voice` subfolder inside it holding the WAVs — the
layout `crew-chief-autovoicepack` writes, so **a Crew Chief pack drops straight
in**. The outer folder is separate so a pack can carry a licence and its source
recordings without those being mistaken for phrases.

```
voices/
  Norman/
    voice/
      go_ahead.wav
      box_this_lap.wav
      ...
```

WAV only. It is what every generator emits, what the standard library reads,
and it needs no decoder in a build that already fights native dependencies.

Filenames come from the phrase, lowercased, with punctuation **dropped** rather
than replaced — so "that's enough" and "thats enough" are the same clip.
Turning an apostrophe into a separator would give `that_s_enough`, and a pack
recorded against either spelling would silently miss the other.

## Where packs live

**Settings → Voice** is where they are all listed: what is installed, what is
bundled, and what can be downloaded. Packs live beside your config, in
`voices/`, not under the install directory — an update
replaces the install directory wholesale, and a pack is a lot of audio you
chose to put there. **Settings → Voice → Open voice pack folder** opens it.

Drop a folder in, reopen the tab, and it appears in the picker.

## The phrase list

**Settings → Voice → Write phrase list** exports every phrase the engineer can
say, as a CSV, in the engineer's own language — because a pack is recorded in
the language it will be spoken in.

It is generated from the app rather than kept by hand, so it cannot drift from
what the engineer actually says. Use it if you are recording outside the app,
or scripting a generator of your own.

## Nothing plays

**Check a pack is selected.** *Engineer → Voice → Voice* has to point at the
pack rather than at *(no pack)*.

**Check the output device.** *Audio → Output* should be your headset — the same
one you use for voice chat, not the sim's output.

**A missing phrase is not a fault.** Anything not in the pack falls back to the
Windows voice, so a half-recorded pack sounds like two people rather than
failing. That is intentional: it is what makes a pack usable before it is
finished.
