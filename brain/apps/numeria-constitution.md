# ⚖️ MA-0 — The Numeria Constitution

> **Status: 📝 DRAFT — awaiting founder Freeze.** Drafted 2026-07-20.
>
> **The immutable foundation for every future implementation decision in Numeria**, the experience
> layer of the Math Adventure RPG web Community Edition. Once frozen, this document may change only
> through a **formal roadmap revision** — not by an implementation decision, not by an AI session, and
> not by a later milestone finding it inconvenient.
>
> **Nothing in MA-1…MA-5 may be built until this is founder-frozen.** Blueprint → Freeze → Build.
>
> Parent document: [`numeria-roadmap.md`](./numeria-roadmap.md).

---

## Mission

Build learners' confidence in mathematical thinking through exploration, mastery, and the sense of
belonging to a world. A learner should never feel they are completing mathematics exercises. They
should feel they are **travelling through Numeria and earning their place in it.**

Where Number Kingdom tells a young child *"numbers are friendly"*, Numeria tells a growing learner
*"mathematics is a world worth exploring."* The child has grown. The world has grown with them.

---

## Educational Principles (constitutional)

Offline First · Audio First · Confidence Before Correction · No Failure States · No Timers ·
Learning Through Play · **Ages Before Grades** · Environment as Reward · Discovery Before
Memorisation · Privacy by Design · **#FreeForever**.

---

## The Ideal Numerian Graduate

> 📝 **Drafted by AI for founder ratification.** This is educational philosophy and belongs to the
> founder; the wording below is a starting point, not a decision.

Mathematics is the **vehicle**, not the destination. Numeria's purpose is not to produce learners who
can compute — it is to produce a particular kind of person, for whom mathematics happens to be how
they got there.

**A Numerian graduate:**

- **Is not afraid of a hard problem.** Difficulty reads as interesting, not as threat.
- **Thinks before answering,** and can say *"I don't know yet"* without shame.
- **Treats being wrong as information,** not as failure — because Numeria never treated it as failure.
- **Persists** past the first attempt, having learned that the second attempt is where understanding
  usually lives.
- **Sees structure** — notices that things repeat, connect, and explain one another.
- **Belongs.** They do not feel they were let into mathematics; they feel it was always theirs.

### Graduate Identity Statement

> **"I am someone who can work out things I do not yet understand."**

That sentence is the destination. Every province, every story beat, and every word the Guide speaks
is measured against whether it makes that sentence truer for the learner.

**Ownership note:** this section is defined here, in the world's constitution, and is **referenced —
never redefined — elsewhere.** The Guide *models* these qualities; the Guide does not own them.
See [`numeria-guide-constitution.md`](./numeria-guide-constitution.md).

---

## Educational Invariants (founder addition, 2026-07-20)

**Rules that can never be broken, regardless of how spectacular the animation becomes.** These are
not implementation details — they are constitutional guarantees a future contributor can rely on
without asking permission.

1. **Mathematics is always the primary interaction.** Never a reward for sitting through content.
2. **Every animation has a pedagogical purpose** — it satisfies the Four-Purpose Test below.
3. **Reward animations are shorter than learning interactions.** If the celebration outlasts the
   thinking, the balance has inverted.
4. **Learners are never forced to watch long cinematics to continue learning.**
5. **Every animated sequence is skippable, or brief enough that skipping is unnecessary** — wherever
   learning flow would otherwise be interrupted.
6. **Offline capability remains a first-class requirement.** No Numeria feature may introduce a
   network dependency, at any point, for any reason.

---

## The Four-Purpose Test

> **Every story element must either teach, motivate, orient, or celebrate. If it does none of those
> four, it does not belong in Numeria.**

| Purpose | Example |
|---|---|
| **Teach** | A concept animation showing a fraction taken from a whole |
| **Motivate** | A bridge rebuilding itself as problems are solved |
| **Orient** | The guide explaining why the learner travels to the next province |
| **Celebrate** | An achievement animation after mastering a skill |

An idea that exists only because it looks impressive fails the test. This is deliberately an
**objective filter**, not a matter of taste — any contributor can apply it alone, and any reviewer
can reject with it.

---

## The core doctrine

**Story supports learning; it never competes with it.**

This is a scar, not an aspiration. Math Adventure RPG's "Expert Approved" badge was **rejected on
2026-06-17 for text volume and disruptive sounds.** A storytelling layer is the single most likely
way to re-trigger that failure. Story scenes stay brief; they are optional or reward-gated where
appropriate; gameplay remains the primary learning experience; animation explains or celebrates — it
never buries the mathematics under dialogue.

---

## Experience Principles

The learner never navigates a menu — they travel through a world. They never select a difficulty —
they arrive in a province. They never earn abstract points — **Numeria responds to them.**

---

## Navigation Principles

One province at a time · **back is never destructive** · no dead ends · no way to become lost ·
**exit is gentle** (an audible or animated farewell, never a silent jump) · a learner can always
resume where they left off · nav targets 64×64px, never below the 44×44px floor · full desktop parity
at ≥768px.

---

## Platform Principles

- **Web only.** Numeria exists in the Community Edition. It is inert in the `play-store` profile.
- **The Stable Build Principle is absolute here.** The Play edition's gameplay, saves, progression,
  content and UX do not change because of Numeria. Verified by bundle hash after every milestone.
- **Numeria consumes the platform; it does not modify it.** `@tph/core` is advisory/consume-only.
- **Numeria's story system stays app-local** (`src/web/numeria/`) until DNA Principle 11's two-app
  trigger fires. *Package what's proven, not what's imagined.* See **D-16**.

---

## World Structure

**Eleven constitutional provinces.** Ten are existing regions of `src/game/levelContent.ts` — nothing
invented to fill the map. The eleventh, **Meadow Gate**, is the threshold, and the only one created
rather than revealed:

🌼 **Meadow Gate** *(the threshold, ages 3–5)* · 🏫 Central Numeria (Academy of Numbers) ·
🏪 Western Numeria (Merchant's Guild) · 🐉 Northern Numeria (Dragon's Tower) ·
🌟 The Highlands (Star Observatory) · 🏦 The Western Reach (Merchant Republic) ·
🏗️ Industrial Numeria (Engineers' Citadel) · 🌩️ The Storm Highlands (Storm Observatory) ·
🏔️ The Far Peaks (The Pinnacle) · ⚙️ The Forge Deeps (The Geometry Forge) ·
🏆 The Summit (The Summit Academy).

**Meadow Gate** (founder, 2026-07-20) — *"You don't begin by entering a fortress. You begin by walking
through a meadow."* It is where the Welcome Moment lands.

The world opens on the **Academy of Numbers** and closes on the **Summit Academy** — the same
institution, at the beginning and end of mastery. Future content must belong within this structure
unless a **formal roadmap revision** introduces a new province.

### The Academy is part of Numeria (founder, 2026-07-20)

> **The Academy is Numeria's highest institution of learning.**

Numeria spans the full 3–17 range. Younger learners **travel through** the world; older learners **do
not leave it — they graduate within it.** The Academy keeps its own tone as an *institution within*
the world, not as an exception to it. Learning is continuous, not segmented.

---

## The Companion and the Guide are two entities

**Constitutional (founder, 2026-07-20).** A player-renamed companion **cannot serve as canonical
narration** — the world cannot refer to a character whose name it does not know. The roles are
fundamentally different jobs and are never merged:

| | **Companion** | **Guide** |
|---|---|---|
| Identity | chosen by the learner, **renameable** | **fixed** |
| Role | emotional support | narrator |
| Behaviour | reacts to gameplay, celebrates achievements | introduces provinces, explains the world, welcomes the learner, appears in Story Theatre |

The existing companion (`src/game/Companion.tsx` — six emotions, 24 lines, default **"Sparky" 🐉**)
remains exactly what it is: **the learner's own.** Sparky is not made to do both jobs.

The Guide's purpose, archetype, voice, appearance principles, moments, and architectural cost are
defined in [`numeria-guide-constitution.md`](./numeria-guide-constitution.md) — which **extends this
document and never redefines it.** Where the two disagree, **this constitution is authoritative.**

### 🔓 Guide identity — FOUNDER DECISION PENDING

Deliberately unnamed. **Once the guide is named, that character becomes part of Numeria's identity for
years** — it warrants a dedicated design discussion, not a name chosen in passing.

Ecosystem convention constrains whoever it turns out to be: **each world gets its own guide.**
Ollie/Fifi/Lulu belong to Early Literacy, 🐿 Pip to Number Kingdom, Nova to Space Explorer.
Personalities are never borrowed and never overwritten — **so Numeria may not use Pip.**

The guide, once named: invites rather than instructs · never judges · never uses negative language ·
never becomes a second teacher inside the question flow · speaks only from **scripted pools, never
generative AI**.

---

## The Welcome Moment

Required by **DNA Principle 18**, which applies to every World-A app — and from which **Math
Adventure RPG is currently absent.** Numeria closes that gap.

Shown **once, ever** (persisted flag) · emotionally warm and **narrated** · the single "begin" tap
doubles as the browser's first user gesture and therefore **unlocks audio** · remembered as the
memory of *arriving in a world*, not opening an app.

> **"Welcome to Numeria."**

---

## Wrap, Don't Rewrite

The educational logic is preserved. `src/mathEngine.ts`, the `phases.ts` progression, the 65 levels,
and the save format are **frozen**. Numeria's work is presentation · navigation · environmental
storytelling · emotional engagement.

**Rewriting proven educational mechanics requires a separate architectural review.**

---

## Definition of Success

Numeria is complete when learners no longer perceive Math Adventure RPG as "doing maths" — instead
they experience **returning to Numeria**, a world where mathematics is the way you travel, and where
the mathematics itself remains the hero.

---

## Related
- [`numeria-roadmap.md`](./numeria-roadmap.md) — MA-1…MA-5 and the full constraint set
- [`../PROJECT_DNA.md`](../PROJECT_DNA.md) — Principles 13, 17, 18
- [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) → **D-16**
