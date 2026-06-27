# Science Sprouts

> 🌱 **Curiosity & Knowledge** · ages **3–17** ✅ · **LIVE** (web PWA) ·
> repo `…/science-sprouts` · https://science-sprouts-65b.pages.dev/ ·
> local `C:\Users\sifis\mobile-projects\science-sprouts`
> Notable as **the last app on Google Play, ever.**

---

## What it is
A science-learning app — CAPS-aligned science for children, extended in 2026 with a teen
**"Science Academy"** tier for 13–17. Modules: Science · Ask Why (question-driven) · Nature Explorer
(environment/conservation).

## Why it exists
Curiosity — "understanding the world" — is Pillar 2. Science Sprouts is its anchor: it turns the
*why does this happen?* instinct into structured science learning, offline and free.

## Original vision
A children's (3–12) CAPS science app, SA-first.

## Design iterations / how the thinking evolved
- **The age-ceiling forced a teen tier.** When the rule *"every learning app reaches 17"* was set
  (2026-06-21), Science Sprouts (3–12) was the app that *violated* it. The fix (2026-06-25): add a
  data-driven teen **Science Academy** — a **5-school arc (13 Explorers → 17 Thinkers), 15 topics /
  45 levels** — built on the **exam-studio engine ported from Math Adventure**. This both satisfied
  the rule and proved the engine-reuse thesis a second time.
- **The silent-launch incident.** An earlier build shipped with **broken audio** because it used the
  naive `speak()` instead of Math Adventure's `useNarration`. This became a standing house rule and a
  release gate. See [`../HISTORY.md`](../history/HISTORY.md).

## Architectural decisions (& rejected alternatives)
- **Reuse Math Adventure's exam-studio engine** for the teen tier rather than hand-authoring teen
  content from scratch. *Rejected:* a bespoke teen science engine (duplicated effort).
- **Stay on Play to completion** — uniquely. Because SS had already been *granted production access*,
  the decision was to finish it out as the **final Play release** rather than abandon a working
  pipeline. *Rejected:* yanking it to web-only mid-rollout (wasteful). After SS, Play is retired.

## Current state
Live web PWA, science **3–17** (age-ceiling rule satisfied across Curiosity). **Rolling out to Play
production (2026-06-21)** as the last-ever Play release; Play track now closed.

## Future direction
Web-first maintenance; deepen the teen Academy and the Nature Explorer/Ask Why modules. Pairs with
**Our World** as the two Curiosity apps. The isiZulu DRAFT review applies here too.

## Related
- [`our-world.md`](./our-world.md) (its Curiosity companion) ·
  [`math-adventure-rpg.md`](./math-adventure-rpg.md) (exam-studio engine source) ·
  [`../canon/04-delivery-model.md`](../vision/02-delivery-model.md) (the Play wind-down).
