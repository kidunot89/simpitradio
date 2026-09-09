# Translating SimPitRadio

**If you speak one of these languages, you can improve this in about five
minutes, and you would be doing something nobody on this project can do.**

Every translation here was produced without a fluent speaker of the language.
They are almost certainly wrong in places, and wrong in the way that is
hardest to catch from the outside: fluent-looking, correctly spelled, and
saying the wrong thing. A native speaker reading one line and going "nobody
says that" is worth more than any amount of re-checking from here.

## What these files are

One JSON file per language, plus `template.json`, which is the English source
every other file is keyed against.

```json
{
  "Engineer on": "Ingenieur an",
  "Corner threshold": "Kurvenschwelle"
}
```

The **key is English and must not change** — it is what the program looks the
string up by. Change only the value.

## How to send a fix

1. Edit the file for your language here on GitHub — the pencil icon.
2. Describe what was wrong. "This is the word for a racing corner, not a
   street corner" tells us more than the diff does.
3. Open the pull request.

A bot carries it to the repository the app is actually built from and closes
the one here, because this repository is generated and its `main` is replaced
on every publish — a merge here would land and then vanish. Your change comes
back down on the next publish, with you credited on the commit.

## What is worth fixing

**Racing vocabulary above all.** These are read out over engine noise to
somebody driving, and the register matters: an engineer says "box this lap",
not "please enter the pit lane at your convenience". If your language has a
word the drivers actually use, that is the word.

**Anything too long.** Several of these appear on buttons and in a narrow
window. A translation that is correct and twice the length of the English
gets cut off.

**Terms that should not have been translated.** Some things are proper nouns
or on-screen names from the sim, and reading them translated is confusing.

## Things that are deliberate

**Voice commands stay in English.** The recogniser listens for the English
phrase, so `focus on {driver}` is what you say whatever the window is set to.
Translating those would stop them working.

**Numbers are digits outside English.** `"9"` rather than `"nove"` is not an
untranslated string — the app hands numbers to your system's speech voice,
which already says them correctly in your language.

**`{}` and `{name}` are placeholders.** Keep them exactly, including the
spelling inside the braces. They can move within the sentence, which is often
necessary — `"{driver} is ahead"` may need the name last in your language.

## The voice packs are made from these files

The spoken packs are generated from these exact strings, so a wording fix here
changes what the engineer says out loud, not just what the window shows. That
is the main reason a fix is worth sending rather than living with.

## If a string is missing

The file may have fewer entries than `template.json`. Anything absent falls
back to English rather than breaking, so adding a missing key is a perfectly
good contribution on its own.
