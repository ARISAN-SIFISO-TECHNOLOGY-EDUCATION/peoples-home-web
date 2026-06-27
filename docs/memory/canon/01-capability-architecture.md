# Canon 01 — The Capability Architecture

> How The People's Home is *shaped*. The reframe that turned an unbuildable backlog into a
> buildable system. Distilled from [`../../../BLUEPRINT.md`](../../../BLUEPRINT.md) (v2, 2026-06-21)
> with the evolution made explicit.

---

## The evolution

- **v1 (retired):** ~40 independent apps. A backlog. Unbuildable by a solo developer, and
  conceptually wrong — most of those "apps" were really *modules* of a few deep products.
- **v2 (2026-06-21, current):** the same vision re-expressed as a **capability system** —
  ≈10 deep offline learning apps + one opportunity platform (iKhaya) + a shared core.

> **The People's Home is not a collection of apps. It is a capability system.**
> Read the blueprint as *architecture* (the map of the territory), not a backlog (the list of
> what to build next). Sequencing lives in the [roadmap](../../../ROADMAP.md); the architecture
> governs *where each thing belongs*.

---

## The model: Capability → Implementation → DNA

Every item is classified three ways:

1. **Capability** — what a person *gains* (the real unit of value).
2. **Implementation** — the lightest delivery: **App** · **Module** (inside an app) · **Service**
   (shared platform). *Prefer the lightest.*
3. **DNA** — which of two engineering worlds it lives in (see [`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md)).

This single discipline collapses ~40 future apps → **≈10 deep learning products + iKhaya + a shared core.**

### Module-over-new-app discipline
The rule that keeps the collapse from un-collapsing: **prefer a module inside an existing app over
a new repo.** Only spin a new product when the capability *and* the DNA genuinely warrant it.
*(Example: Truth Seekers is ONE app with six modules, not six apps.)*

---

## The six capability pillars

| # | Pillar | Capability gained | Lead app(s) |
|---|---|---|---|
| 1 | 🧮 **Foundations** | Basic participation in society (numeracy, literacy) | Math Adventure · ReadAfrica · Everyday Foundations |
| 2 | 🌱 **Curiosity & Knowledge** | Understanding the world | Science Sprouts · Our World |
| 3 | 🔧 **Creation & Technology** | Turn consumers into creators | Tech Makers · The Golden Hand |
| 4 | 🧠 **Thinking & Reasoning** | Judgment — telling true from false | Truth Seekers |
| 5 | 🚀 **Real-World Empowerment** | Build a venture; turn capability into impact | Micro Founders → iKhaya |
| 6 | 💰 **Money & Opportunity** | Connect learning to economic mobility | Mzansi Money → iKhaya |

> Pillars 5 and 6 **span both worlds**: an offline app *teaches*, then *hands off* to iKhaya.
> That handoff is **"the bridge"** ([`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md)).

---

## Top-level architecture

```
THE PEOPLE'S HOME
        │
   TPH CORE  ── shared SERVICES (not apps)
        │      Identity · Progress · Rewards · Lore · Offline Engine ·
        │      Parent / Mentor / Community Dashboards
        │      (seeded today as the TPH Core SDK embedded in ReadAfrica)
        │
   ┌────┴──── WORLD A — Offline Learning (no login · offline · #FreeForever) ────┐
   │  Foundations · Curiosity · Creation · Reasoning · (Money·learn) · (Empower·learn)
   └─────────────────────────────────────────────────────────────────────────────┘
        │
   ┌────┴──── WORLD B — Opportunity Infrastructure (= iKhaya platform) ──────────┐
   │  Opportunity Hub · Community & Mentor Services
   └─────────────────────────────────────────────────────────────────────────────┘
```

Carried end-to-end by shared rails: **Identity · Progress · Rewards · Lore · Offline Engine ·
Parent Dashboard** — see [`05-tph-core-and-passport.md`](./05-tph-core-and-passport.md).

---

## The whole ecosystem on one page (classification)

| Item | Implementation | DNA / Home |
|---|---|---|
| Math Adventure RPG | App | Offline Learning |
| ReadAfrica | App | Offline Learning |
| Everyday Foundations | App (multi-module) | Offline Learning |
| Science Sprouts | App | Offline Learning |
| Our World | App (multi-module) | Offline Learning |
| Tech Makers | App | Offline Learning |
| SIFISO — The Golden Hand | App (5-in-1) | Offline Learning |
| Truth Seekers | App (6 modules) | Offline Learning |
| Mzansi Money | App | Offline Learning |
| Micro Founders | App | Offline Learning |
| Digital Creator Academy | App | *Future — parked* |
| Opportunity Hub | Platform module | iKhaya / World B |
| Community & Mentor Services | Platform module | iKhaya / World B |
| TPH Core (identity/progress/…) | Shared services | Platform |

**≈ 10 offline learning apps + 1 opportunity platform (iKhaya) + shared core** — an institutional
platform, not 40 products.

---

## Related
- [`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md) — the DNA split in depth.
- [`../../../BLUEPRINT.md`](../../../BLUEPRINT.md) — the full operational blueprint (source).
- Per-app deep memories: [`../apps/`](../apps/).
