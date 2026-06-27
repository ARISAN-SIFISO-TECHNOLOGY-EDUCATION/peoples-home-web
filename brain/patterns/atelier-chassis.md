# Pattern: Atelier Chassis

> A shared "studio" scaffold — originally conceived as a reusable engine for
> activity-based learning. Used in Truth Seekers. Deliberately NOT used in Micro
> Founders (see decision below).

---

## What it is

The Atelier Chassis is a React scaffold that provides:
- A structured "activity studio" layout (header / activity area / response area)
- Navigation between parallel activity tracks (e.g., 5 reasoning muscles)
- Scenario presentation: prompt → options → reveal
- Progress tracking per-track in localStorage
- A shared visual language across the app's activity types

The name "Atelier" (French: workshop/studio) reflects the metaphor: the learner
enters a studio, works on something real, and produces an output.

---

## Why it exists

Truth Seekers has five distinct "reasoning muscles" that share the same interaction
model: present a scenario, show options, reveal the right reasoning, track progress.
Rather than building five separate activity UIs, the Atelier provides one engine
that five muscles plug into.

---

## Where it is used

| App | Status | Notes |
|---|---|---|
| Truth Seekers | Native | Phase 2 (2026-06-24) purged the scaffold and made Truth Seekers fully reasoning-native — but the Atelier structure remains as the organising metaphor |
| Micro Founders | Rejected | Explicitly chose NOT to use Atelier (see decision below) |

---

## The Micro Founders decision (why NOT to use Atelier)

On 2026-06-23, when building Micro Founders, the Atelier chassis was considered and
rejected for the following reasons:

1. **Different pedagogical shape:** Truth Seekers is about parallel reasoning muscles
   (you can work on any of the 5 at any time). Micro Founders is about a linear
   5-stage Venture Journey where Stage N gates Stage N+1. Atelier's parallel
   navigation is wrong for a sequential journey.

2. **Different artifact type:** Atelier is about scenario-response activities.
   Micro Founders needs "My Venture" — a persistent, evolving business that the
   learner builds. That's a data model, not an activity scaffold.

3. **Different language:** Atelier language is "reasoning studio / case / scenario."
   Micro Founders language is "venture / stage / pitch." Forcing one scaffold on both
   would produce confusing conceptual bleed.

**The result:** Micro Founders was built with the Journey Progression pattern instead.
See [`journey-progression.md`](./journey-progression.md).

This decision is recorded here as a pattern anti-pattern: the Atelier is a good engine,
but only for parallel-activity, reasoning-focused apps. Do not use it for
sequential-journey, artifact-building apps.

---

## Rules and constraints

1. **Use Atelier for parallel-track, scenario-response apps only.**
   If the app has sequential stages with a growing artifact, use Journey Progression instead.

2. **Truth Seekers' Phase 2 rewrite made it "reasoning-native"** — meaning the Atelier
   scaffold was restructured to be deeply reasoning-specific, not generic. If you borrow
   code from Truth Seekers, you are borrowing reasoning-specific code, not a generic chassis.

3. **The name "Atelier" is internal.** Learners see "studio" or just the activity name;
   they never see "Atelier."

---

## Evolution

**2026-06-11 — Tech Makers** (Creation pillar) was built; maker/coding arc established.

**~2026-06-20 — Truth Seekers** adopted the Atelier scaffold as its activity engine.

**2026-06-23 — Micro Founders** considered and rejected Atelier; Journey Progression
pattern was born as the alternative.

**2026-06-24 — Truth Seekers Phase 2:** Purged the generic Atelier scaffold, rebuilt
as fully reasoning-native. The Atelier name remains as the organisational metaphor
(five reasoning "studios") but the code is bespoke.
