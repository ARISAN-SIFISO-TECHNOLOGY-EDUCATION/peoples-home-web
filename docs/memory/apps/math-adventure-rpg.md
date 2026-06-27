# Math Adventure RPG

> 🧮 **Foundations** · ages **3–17** · **LIVE** (web PWA + Android, maintenance) ·
> repo `…/math-adventure-rpg` · https://math-adventure-rpg.pages.dev/
> The **seed app** — the first product, and the template the whole ecosystem inherits from.

---

## What it is
A numeracy role-playing game. Children (and up to 17) progress through an RPG — a bright "Kids'
Adventure" for ages 3–12 and a darker, exam-prep **"Academy"** for 13–17 — solving age-appropriate
maths to advance, with a companion, narration, badges, streaks, and a break timer.

## Why it exists
Numeracy is the floor of **Foundations** — "basic participation in society." Math Adventure makes
it a game a child *wants* to play, offline and free, with no grade labels to shame anyone.

## Original vision
A single offline maths RPG for children. It started Play-first (Android via Capacitor) before the
web-first pivot.

## Design iterations / how the thinking evolved
- **Two experiences under one roof.** The home screen splits into 🎮 *Kids' Adventure* (3–12, RPG)
  and 🎓 *The Academy* (13–17, IGCSE-style exam prep, dark theme). This *within-app* split is itself
  a small model of the whole ecosystem (one shell, multiple journeys).
- **The exam-studio extraction.** The Academy is powered by a **content-free, reusable exam-prep
  framework** (`src/exam-studio/`) with a strict dependency rule (`exam-studio ← senior content ←
  App`). This framework was later **ported into Science Sprouts** for its teen Science Academy tier —
  the first real proof that a deep app's engine can be reused across the ecosystem.
- **Orphaned phases.** The old RPG once reached phases 5–9 (ages 13–17); when the Academy took over
  the teen years, those phases were left **unreachable** (the engine clamps to ≤ phase 4). They're
  legacy/retirement candidates — *do not extend them.*
- **Passport adoption (2026-06-27).** Math Adventure became a real consumer of the
  [Passport](../platform/peoples-home-passport.md) pattern (PRs #1/#2), adopting the shared
  `@tph/core` envelope.

## Architectural decisions (& rejected alternatives)
- **Ages, never grades.** CAPS/IGCSE alignment is internal; UI shows ages only. This rule was *born*
  here and became ecosystem-wide ([`../canon/03-product-rules.md`](../canon/03-product-rules.md)).
- **The robust narration engine (`useNarration`).** Waits for `voiceschanged`, pins an installed
  voice, falls back isiZulu→English. **This is the canonical narration the whole ecosystem must
  copy** — Science Sprouts shipped silent by using the naive `speak()` instead.
  *Rejected:* the naive `speechSynthesis.speak()` (unreliable across devices).

## Current state
Live web PWA + on Play (maintenance-only). The **"Expert Approved" badge was rejected** (2026-06-17,
text volume + disruptive sounds) — that fix carries to the PWA. See [`../HISTORY.md`](../HISTORY.md).

## Future direction
Maintenance + the "Expert Approved" fixes; serve as the reference implementation for narration and
the Passport as TPH Core is extracted. Not a candidate for big new feature work — its job is to be
the dependable floor and the template.

## Related
- [`../canon/03-product-rules.md`](../canon/03-product-rules.md) (rules born here) ·
  [`../platform/peoples-home-passport.md`](../platform/peoples-home-passport.md) ·
  [`science-sprouts.md`](./science-sprouts.md) (reused its exam-studio engine).
- Code: this repo's own `CLAUDE.md` is the authoritative engineering guide.
