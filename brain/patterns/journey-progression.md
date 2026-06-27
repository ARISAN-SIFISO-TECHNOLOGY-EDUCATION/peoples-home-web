# Pattern: Journey Progression

> The learner has one persistent thing — a venture, a plan, a passport — that
> grows as they move through numbered stages. Not a course with chapters. A journey.

---

## What it is

A linear or semi-linear progression through named stages, where the learner carries
a single **through-line artifact** across all stages. The artifact is personalised,
persistent (in localStorage), and accumulates meaning as the learner advances.

Stages are named (not numbered in the UI). Progress is shown as "you are here in
your journey" — never as a percentage complete.

---

## Why we use it

### Problem: "course" framing breaks engagement

A traditional course ("Chapter 4 of 12: 33% complete") feels like school. Percentages
invite comparison and failure. Chapters feel arbitrary.

### Solution: the journey metaphor

A journey has a destination that matters. The learner is building *their own thing* —
a venture, a money plan, a passport book, a portfolio of discoveries. The stages are
milestones in their personal story, not units in a curriculum.

**Psychological effect:** the learner never "fails" a journey. They are always "on their
way." This matches the design philosophy of The People's Home: empowering, not remedial.

---

## How it is implemented

### Core structure

```typescript
type Stage = {
  id: string;
  name: string;         // "Spot it" not "Stage 1"
  tagline: string;      // one-line description of this stage's job
  unlocked: boolean;
  completed: boolean;
};

type JourneyState = {
  learnerName: string;
  throughLine: ArtifactType;   // the venture, plan, passport, etc.
  stages: Stage[];
  currentStageId: string;
};
```

### Persistence

Journey state lives in `localStorage` under a namespaced key:
`tph-<app-id>-journey`.

The People's Home Passport can export/import this state (via downloadable JSON)
to carry it between devices or into iKhaya.

### Stage transitions

- Stage N unlocks when Stage N-1 is completed (linear gate)
- Some apps allow partial unlock (preview next stage) to reduce anxiety
- Completion is defined by the stage's own logic — not a single quiz

---

## Where it is used

| App | Through-line | Stages |
|---|---|---|
| Micro Founders | "My Venture" — one business idea | Spot it · Cost it · Sell it · Build it · Pitch it |
| Mzansi Money | "My Money Plan" — one financial plan | Earn · Budget · Save · Borrow · Protect & Grow |
| SIFISO — The Golden Hand | Five nested journeys in one app | Learn → AI → Quiz → Startup → Teach Others |
| Our World | "My Passport" — a stamp book | My Home · six Journeys (Place, People, Planet arcs) |

---

## Rules and constraints

1. **Never show percentages for journey progress.** Use stage names, landmarks, or
   "you are here" visualisations.

2. **The through-line artifact must be the learner's own.** It carries their name,
   their choices, their SA context. It is not a shared template.

3. **Stages must be named meaningfully**, not "Stage 1" / "Stage 2."

4. **Persist to localStorage immediately** on any state change. The learner must
   never lose progress due to a browser refresh.

5. **The journey must be completable offline.** No stage should gate on a network
   call (this is a corollary of the offline-first pattern).

---

## Differences from "course" patterns

| Dimension | Journey Progression | Traditional Course |
|---|---|---|
| Unit name | Named stage ("Spot it") | Numbered chapter ("Chapter 3") |
| Progress language | "You are here in your journey" | "33% complete" |
| Learner artifact | One personal through-line | Generic exercises |
| Failure model | No failure — always in progress | Failed/incomplete |
| Completion feeling | "I built something" | "I passed a test" |

---

## Evolution

**2026-06-23 — First implemented in Micro Founders** (5-stage Venture Journey).
The pattern was named here and deliberately chosen over a chapter structure.

**2026-06-24 — Adopted in Mzansi Money** using the Micro Founders chassis.

**2026-06-25+ — Our World uses it** for the Passport/Journeys structure.

**SIFISO — The Golden Hand** was always journey-structured (5 nested journeys)
but was retroactively named under this pattern when Micro Founders made it explicit.
