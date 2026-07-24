# Truth Seekers

> 🧠 **Thinking & Reasoning** · ages **13–17** (first) · **LIVE** (web PWA) ·
> repo `…/truth-seekers` · https://truth-seekers.pages.dev/
> The app that built the **"Atelier" chassis** the later apps all inherit.

---

## What it is
A reasoning app: judgment — telling true from false. Five "muscles": **Fact Finders · Logic Builders**
(fallacies) **· Data Detectives** (stats) **· System Builders** (bias slider) **· Truth Makers**
(evidence board), across ~24 SA scenarios.

## Why it exists
Pillar 4 — judgment. In an age of misinformation, the capability to reason, spot manipulation, and
weigh evidence is foundational citizenship. Truth Seekers makes that a trainable set of skills.

## Original vision
A 13–17 reasoning app covering logic, media literacy, systems thinking, decision-making, problem-
solving, and civil debate (the BLUEPRINT lists six modules).

## Design iterations / how the thinking evolved
- **A merge of two codebases.** It combined a **Gemini-built "Atelier" UI base** (phone-frame UI,
  bead-path nav, `tone()` audio, Welcome front-door, picker, Co-Pilot) with a **Claude reasoning
  scaffold's content/exam-studio soul.** Phase 1 stripped grades + server deps and got it building.
- **Phase 2 (2026-06-24): went fully reasoning-native.** The borrowed Atelier *engine scaffold*
  (its STACK/POUR/ROLL/MAKE verbs) was **purged** and case content was ~doubled. The lesson: a
  borrowed chassis is fine for *UI*, but the *engine* must be native to the app's true subject.
- **Parallel muscles, not a sequence.** Reasoning skills (fallacies / stats / bias) are *independent*
  competencies — attackable in any order. This shape was later *deliberately contrasted* with Micro
  Founders' sequential journey to teach the difference between *a set of skills* and *a journey*.

## Architectural decisions (& rejected alternatives)
- **The Atelier chassis became the ecosystem chassis.** Micro Founders → Mzansi Money → Everyday
  Foundations → Our World all descend from it. *Rejected:* bespoke UI per app (unsustainable solo).
- **Teens-first; defer 3–12.** Early ages deferred *until TPH matures* — same call as Micro Founders.
  *Rejected:* trying to span 3–17 on day one.

## Current state
Live web PWA, 13–17, fully reasoning-native after Phase 2.

## Relationship to Critical Thinker — ⚠️ FOUNDER-STATED INTENT, *not* current architecture

> **Founder-Stated Intent (2026-07-24):** The Founder intends for Critical Thinker to evolve into the
> research, taxonomy, calibration, and editorial programme that informs future versions of Truth
> Seekers. As of 2026-07-24, **no architectural or technical dependency exists** between the two
> projects. They have separate corpora, taxonomies, content models, tooling, and implementation
> histories. This statement records **strategic direction only** and must not be interpreted as
> describing the current architecture.

**Verified 2026-07-24** before recording — the intent was plausible and fitted the vision, so it was
checked rather than assumed:

| | Critical Thinker (`sifiso-s-critical-thinking`) | Truth Seekers |
|---|---|---|
| Item model | `{topic, stage, difficulty, concepts, thinking_habits, context, transfer, evidence_type}` — 8 axes, validator-enforced | `{muscle, itemNoun, setup, items[], trap, tip}` — no tagging axes |
| Organised by | topic × stage × difficulty, against coverage targets | **age** — one muscle per year, 13→17 |
| Audience | includes `workplace_meetings` | teens 13–17 only |
| Stack | vanilla JS, static host | React + TS + Vite |
| Corpus | 45 items (`spot-025`, `analyze-010`…) | separately authored SA scenarios |

All ten of Critical Thinker's taxonomy axis and topic names (`thinking_habits`, `evidence_type`,
`transfer`, `TAXONOMY`, `logical_fallacies`, …) return **zero hits** in this codebase. No shared
corpus, taxonomy, item format or tooling.

**Consequence for evidence:** the two projects have **distinct evidence trails**. External review of
Truth Seekers content produces **G6 educational-review** evidence for this flagship, but does **not**
discharge Critical Thinker's audit condition 3 — that requires participants exercising *its* processes,
which this app does not use. Shared *methods* are fine; shared *credit* is not. If Truth Seekers ever
adopts Critical Thinker's taxonomy or editorial process, that becomes a new architectural fact to be
recorded with evidence and an explicit migration decision — not inferred after the fact.

⚠️ **Two local folders, and only one is this app.** `the-truth-seekers/` is this repo (git remote
`ARISAN-SIFISO-TECHNOLOGY-EDUCATION/truth-seekers.git`, `main`, pushed 2026-06-24). A separate
`truth-seekers/` folder has **no `.git`** and holds the *superseded* pre-Phase-2 scaffold — the
`exam-studio` ancestor named under "Design iterations" above. This is the likely origin of the false
claim that *"Truth Seekers has no GitHub remote"*, corrected 2026-07-21: a **true observation about
the wrong artefact became a false conclusion about the system.** Recorded for the D-17 condition 2
documentation sweep.

## Future direction
Extend down to younger ages once TPH Core matures; deepen the six-module map (Media Detective,
Decision Maker, Debate SA). A natural early adopter of extracted TPH Core + the Passport.

## Related
- [`micro-founders.md`](./micro-founders.md) (the deliberate shape contrast) ·
  [`../canon/04-delivery-model.md`](../vision/02-delivery-model.md) (the chassis lineage it started).
