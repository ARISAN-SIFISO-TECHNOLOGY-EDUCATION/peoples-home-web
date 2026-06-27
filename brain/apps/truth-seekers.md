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

## Future direction
Extend down to younger ages once TPH Core matures; deepen the six-module map (Media Detective,
Decision Maker, Debate SA). A natural early adopter of extracted TPH Core + the Passport.

## Related
- [`micro-founders.md`](./micro-founders.md) (the deliberate shape contrast) ·
  [`../canon/04-delivery-model.md`](../vision/02-delivery-model.md) (the chassis lineage it started).
