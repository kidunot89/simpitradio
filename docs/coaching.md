# The coach

Pick somebody to study, and every time you finish a segment of the circuit the
panel draws your line against theirs and the coach tells you what to do
differently.

> *Tosa, you gave up mid-corner speed because you were still on the brake at
> the apex, and they apex later so their exit straightens out sooner.*

It reads your pedals, your wheel and your gear rather than only the clock, so
what it says is a cause rather than a restatement of the timing screen. Lock a
wheel or put one off the road and it says so immediately, while you can still
feel what you did.

The coach is not the engineer. It has its own voice, its own volume and its own
notifications, and every call is announced in that voice so you always know
which of the two is talking to you. **Coaching → Who** sets it up; ticking
*Use the engineer as the coach* gives them one voice if you would rather.

## Quick start

1. Drive three or four laps. The coach needs to work the circuit out first —
   see [Where the segments come from](#where-the-segments-come-from).
2. Hold push-to-talk and say **"coach me"**.
3. Say **"study Estre"**, or **"focus on P3"**, or **"focus on me"** to be
   measured against your own best.
4. Drive. After each corner the panel draws it and the coach talks.

Nothing here is a tick-box you set before a session. Coaching is asked for out
loud when you want it and stands down when you say so, because whether you want
to be talked at through a corner is a decision you make lap by lap.

## Talking to it

Every phrase below is two words or more, so the coach's name is optional in
front of them.

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
line becomes your own ideal lap — not a lap you have driven, but the best you
have managed through each corner, assembled. An empty practice session still
has somebody to race, and it is the honest opponent when there is nobody else
on track.

## Where the segments come from

**The circuit is worked out from your own laps, not from a database.** Every
lap driven in the session — yours and everybody else's — is pooled onto a grid
five metres apart, and the median of what came through each point is where the
road is. Four laps have to cross a point before it is trusted, and half the
circuit has to be known before a road is built at all.

That is why it works on any track in any sim, including ones nobody has ever
catalogued. Where a catalogue does exist you get names: "Tosa" rather than
"turn seven". Where one does not, you get numbers and everything else works
exactly the same.

The pooling is done twice. The first pass has no road to measure against, so it
uses the car's own heading to work out which way is across the track — and a
car weaving is never pointing along the road, so the answer is wrong in the
same direction on every lap. Once there is a road, its own direction is the
right reference and the second pass corrects it. On a synthetic circle driven
with a three-metre weave, the first pass put the road two and a half metres
wide of where it actually was.

### What counts as a segment

A segment is a corner plus the run into it and the run out, because that is
what you drive.

- The **run-up** goes back to where you got on the brakes, capped at 250m. It
  is not a fixed length — brake later and the segment starts later.
- The **run-out** is 50m past the exit, enough to show where the car came out
  and where it was pointed.
- **Two corners you brake once for are one segment.** Club and Vale is one
  thing to drive and one thing to look at; so is Sebring's hairpin pair.
- **Bends you take flat are skipped.** A corner held above 90% throttle has no
  braking point to move and no entry speed to carry, so it is treated as a
  straight. It stays on the map and keeps its name — it is simply not put in
  front of you. Turn on **Straights and flat-out sections** under *What gets
  coached* to see them anyway.

Merging and skipping both need a reference lap. Without one the coach has no
grounds to decide that two corners are really one, so it leaves them apart.

## What it says

**Coaching → What gets coached → Driver level** decides how much. All three
levels look at the same corner and find the same fault; they drop clauses
rather than findings.

| Level | What you get |
| --- | --- |
| **beginner** | All of it — what was better, what was worse, what caused it, and what to do |
| **intermediate** | No consequence. The fault and the fix, assuming you know what understeer at the apex does to an exit |
| **advanced** | No fix either. What was good and what was wrong; being told "brake earlier" is usually being told something you already know |

Some of what it measures, and the thresholds it uses, so you know when it is
staying quiet on purpose:

- Two speeds have to differ by half a metre per second — under 2 km/h —
  before it is worth mentioning. Below that the two of you did the same thing
  and the difference is where the laps happened to be sampled.
- Using the road means reaching 85% of its half-width, not all of it. A driver
  putting a wheel exactly on the white line every lap is a driver taking track
  limits, and the line that wins is the one that gets close.
- A pedal counts as pressed at 5% travel, and the wheel counts as turned at 5%
  of lock. Sim pedals and wheels rarely rest at exactly zero.

## Notifications

**Coaching → Notifications** turns the coach's three kinds of call on and off
independently:

- **Segment analysis** — the read-out after each corner.
- **Mistakes as they happen** — a locked wheel, a trip off the road, called
  immediately rather than saved up.
- **Where they were quicker** — once a lap.

These are separate from the engineer's Behaviours on purpose, so turning the
coaching down does not turn the spotter down with it. All three still need
coach mode running; none of them says anything until you have asked to be
coached.

## The diagram

![Curva Parabolica, your line against a rival's](images/segment_parabolica.png)

Monza's Parabolica, drawn from a real session. The pale run is braking, the
dark run is on the power; the circle is where each car got on the brakes and
the triangle where it got back on the throttle, pointing the way round.

The panel is a queue of three: one arriving, one being talked about in the
middle, and one on its way out. Position is progress, so a glance tells you
where the coach is up to. The cards float over the game — there is no panel
behind them, only the diagrams themselves.

Your line is drawn in **orange through red**, a rival's in **indigo through
cyan**. Hue says whose line it is; **lightness says what the feet were doing**
— palest on the brakes, darkest on the power. Both lines are dashed, and the
two patterns are offset by half a period, so where the cars take exactly the
same line each shows through the other's gaps instead of one hiding the other. Each
driver's name is written into whichever corner of the card is emptiest, in that
driver's own colour, so you never have to remember which ramp is whose.

The road is a dark ribbon between two white lines, taken from the sim's own
track-edge reading rather than guessed from the racing line — so a wheel put
outside the line is drawn outside the line.

![The diagram queue](images/diagram_queue.png)

Three cards: one arriving, the one being talked about in the middle, one on
its way out. The middle card is the one the coach is speaking about.

### What it looks like from the seat

![Tosa and the corner before it, drawn over the cockpit at Imola](images/incar_tosa.jpg)

Imola, mid-session. Two cards are up at once — the corner just finished and
the one before it — and both name themselves from the circuit's catalogue
rather than by number. The cards sit over the game with nothing behind them,
so the only thing added to the screen is the drawing.

![A corner at Daytona with both lines and their speeds](images/incar_daytona.jpg)

The same thing on a circuit nobody has catalogued: the corner is called `T5`
instead of being named, and everything else works identically — the road from
the sim's own track-edge reading, both lines dashed and offset so neither
hides the other, and the speeds at entry, apex and exit.

**Coaching → Segment diagram** places it, sizes it, sets its opacity and
chooses which way the queue runs. **Show the panel** puts three sample corners
up so you can drag it where you want it and size it against the real thing.

It draws over a game running borderless or windowed. Nothing draws over
exclusive fullscreen — that is a property of the display mode, not a setting.

## The trail-braking trainer

A piano note each time a tyre reaches the edge of grip under braking, so the
release becomes something you can hear rather than something you infer from a
lap time afterwards.

Releasing the brake is the hardest thing in the car to learn by feel: the pedal
gives back almost nothing, the target moves as the car slows and as lock goes
on, and a driver can spend a season a long way under the limit without ever
finding out. One note per release step, not a continuous tone — a tone that
tracked slip would be a buzzer you learn to ignore, and it would say "you are
here" rather than "act now".

| What you hear | What it means |
| --- | --- |
| Three to six notes, descending | A clean release |
| One note, then silence | You came off the brake too fast |
| No notes at all | The limit was never found |
| A low note outside the scale | A tyre locked |

| To do this | Say |
| --- | --- |
| Start | **train on the brakes** · *let's start training on the brakes* · *brake training* |
| Stop | **end brake training** · *stop training on the brakes* |

It learns your car's rolling radius over the first few braking zones, so it
works in any class and with the brake bias anywhere you like. **Coaching →
Trail-braking trainer** sets whether it arms with the session and how loud the
notes are. Its volume is separate from the coach's because the two are mixed
rather than queued — a note sounds over whatever is being said, and a note only
has to be noticed where speech has to be understood.

## Nothing is drawn

**Give it a few laps.** Under four laps through a stretch of circuit there is
no road there, and with less than half the circuit known there is no road at
all. This is the usual answer.

**Check the sim publishes a position.** The lines are drawn from X/Z
coordinates and the track edge. A sim that does not publish them still gives
you lap times, mistakes and the spoken analysis; it cannot give you a picture.
See [What each sim can do](engineer.md#what-each-sim-can-do).

**Check it is not exclusive fullscreen.** Borderless or windowed only.

**Check you actually asked.** Coaching is off until you say so, and it says
"coaching on" back when it starts.
