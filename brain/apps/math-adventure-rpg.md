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
- **Two editions + platform seam (2026-07-10).** The single codebase is formalised into two
  **editions** — **Google Play = Stable/LTS** (maintenance only) and **Web = Community Edition**
  (the innovation lab) — governed by the **Stable Build Principle** (Play gameplay/saves/progression/
  content/UX never change without founder approval). Delivery is gated by explicit build **profiles**
  (`play-store | community | development | demo`, superseding bare `WEB_BUILD`, backward-compatible),
  adopted **seam-first**: add `src/platform/` (profiles → `PLATFORM` → feature flags → adapters) +
  `src/web/` now; extract shared code into `src/core/` incrementally later. Math Adventure is the
  first app to carry this model — it becomes the template for every TPH app with both a store and a
  web edition. See [`math-adventure-release-policy.md`](./math-adventure-release-policy.md) and D-15.
  *(Note: this app's web experience layer — Living World, Story Theatre — is its **own**; it is
  **not** early-numeracy's "Number Kingdom," which belongs to a different app.)*

## Architectural decisions (& rejected alternatives)
- **Ages, never grades.** CAPS/IGCSE alignment is internal; UI shows ages only. This rule was *born*
  here and became ecosystem-wide ([`../canon/03-product-rules.md`](../vision/01-product-rules.md)).
- **The robust narration engine (`useNarration`).** Waits for `voiceschanged`, pins an installed
  voice, falls back isiZulu→English. **This is the canonical narration the whole ecosystem must
  copy** — Science Sprouts shipped silent by using the naive `speak()` instead.
  *Rejected:* the naive `speechSynthesis.speak()` (unreliable across devices).

## Current state
Live web PWA + on Play (maintenance-only). The **"Expert Approved" badge was rejected** (2026-06-17,
text volume + disruptive sounds) — that fix carries to the PWA. See [`../HISTORY.md`](../history/HISTORY.md).

## Future direction
Two tracks, split by edition (2026-07-10, see the [Release Policy](./math-adventure-release-policy.md)):
- **Google Play (Stable/LTS):** maintenance + the "Expert Approved" fixes only. Still the dependable
  floor, the reference implementation for narration/Passport, and the ecosystem template.
- **Web (Community Edition):** *now the first app slated for active enhancement* — the innovation lab
  where web-only experiences (Living World, Story Theatre, advanced animation, large-screen/keyboard)
  are developed and validated, then **graduated** to a future Play release. This reverses the earlier
  "not a candidate for big new feature work" note **for the web edition only**; the Play edition
  stays frozen under the Stable Build Principle.

## Related
- [`../canon/03-product-rules.md`](../vision/01-product-rules.md) (rules born here) ·
  [`../platform/peoples-home-passport.md`](../platform/peoples-home-passport.md) ·
  [`science-sprouts.md`](./science-sprouts.md) (reused its exam-studio engine).
- Code: this repo's own `CLAUDE.md` is the authoritative engineering guide.
