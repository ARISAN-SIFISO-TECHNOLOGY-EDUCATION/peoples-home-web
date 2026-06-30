# Canon 01 — The Capability Architecture

> How The People's Home is *shaped*. Distilled from [`../../BLUEPRINT.md`](../../BLUEPRINT.md)
> (v3, 2026-06-29). Updated each time the blueprint evolves.

---

## The evolution

- **v1 (retired):** ~40 independent apps. A backlog. Unstructured and unbuildable as listed.
  Conceptually wrong — most "apps" were really *modules* of a few deep products.
- **v2 (2026-06-21):** ≈10 deep offline learning apps + one opportunity platform (iKhaya) +
  a shared core. The right move for the build phase. Produced all 10 live World-A apps and the
  iKhaya platform (ikhaya.pages.dev). The module-over-app discipline kept scope manageable.
- **v3 (2026-06-29, current):** **40 apps across 8 capability categories** — a structured
  long-term ecosystem. Unlike v1 (chaotic backlog), v3 has a clear taxonomy: 8 categories ×
  5 apps, unified by a shared platform. The 10 live v2 apps are the first wave and map into
  this structure. The module-over-app discipline still applies *within* each app — not every
  slot requires its own repo today.

> **The People's Home is not a collection of apps. It is a capability system.**
> Read the blueprint as *architecture* (the map of the territory), not a sprint backlog.

---

## The model: Capability → Implementation → DNA

Every item is classified three ways:

1. **Capability** — what a person *gains* (the real unit of value).
2. **Implementation** — the lightest delivery: **App** · **Module** · **Service**.
   *Prefer the lightest — not every blueprint slot needs its own repo today.*
3. **DNA** — which of two engineering worlds it lives in (see
   [`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md)).

---

## The eight capability categories

| # | Category | Capability gained | Lead app(s) |
|---|---|---|---|
| 1 | 🧮 **Foundations** | Basic participation in society | Math Adventure · ReadAfrica · (Early Numeracy · Early Literacy · Parent Companion) |
| 2 | 🌱 **Curiosity & Knowledge** | Understanding the world | Science Sprouts · (Nature · Space · Body · African Discoveries) |
| 3 | 🔧 **Creation & Technology** | Turn consumers into creators | Tech Makers · (Design Studio · Robotics · AI Explorer · Digital Creator) |
| 4 | 🧠 **Thinking & Reasoning** | Judgment — telling true from false | Truth Seekers · (Logic Lab · Debate Academy · Problem Solver · Research Skills) |
| 5 | 💰 **Money & Opportunity** | Financial capability | Mzansi Money · (Side Hustle Lab · Budget Coach · Smart Shopper · Financial Wellness) |
| 6 | 🚀 **Real-World Empowerment** | Build a venture; capability → impact | Micro Founders · (Career Explorer · Leadership · Community Builder · Life Skills) |
| 7 | 🏠 **iKhaya Ecosystem** *(World B)* | Connect capability to real opportunity | Opportunity Hub · (Skills Passport · Job Ready · Employer Connect · Local Opps) |
| 8 | 🤝 **Community & People** *(World B)* | Strengthen families and communities | Parent Hub · Teacher Hub · Volunteer Hub · Community Projects · People's Forum |

> Categories 1–6 are World A (offline learning). Categories 7–8 are World B (iKhaya platform —
> accounts, server, POPIA). Categories 5 and 6 **span both worlds**: the offline app teaches,
> then hands off to iKhaya. That handoff is **"the bridge."**

---

## Top-level architecture

```
THE PEOPLE'S HOME
        │
   TPH CORE  ── shared SERVICES (not apps)
        │      Identity · Progress · Achievements · Badges · Households ·
        │      Caregiver Dashboard · Offline Engine · Learning Analytics ·
        │      Avatar Evolution · Cross-App Journey · Core SDK (@tph/core)
        │
   ┌────┴──── WORLD A — Offline Learning (#FreeForever) ───────────────────────┐
   │  Categories 1–6 (30 apps · no login · offline · no tracking)
   └────────────────────────────────────────────────────────────────────────────┘
        │         "the bridge" — capability hands off to opportunity
   ┌────┴──── WORLD B — Opportunity Infrastructure (iKhaya) ───────────────────┐
   │  Categories 7–8 (10 apps / modules · accounts · server · POPIA)
   └────────────────────────────────────────────────────────────────────────────┘
```

---

## The 40 apps at a glance

| # | App | Category | Status |
|---|---|---|---|
| 1 | Math Adventure RPG | Foundations | ✅ LIVE |
| 2 | ReadAfrica | Foundations | ✅ LIVE |
| 3 | Early Numeracy | Foundations | 🔮 Future |
| 4 | Early Literacy Games | Foundations | 🔮 Future |
| 5 | Parent Companion | Foundations | 🔮 Future |
| 6 | Science Sprouts | Curiosity | ✅ LIVE |
| 7 | Nature Explorer | Curiosity | 🔮 Future |
| 8 | Space Explorer | Curiosity | 🔮 Future |
| 9 | Human Body Explorer | Curiosity | 🔮 Future |
| 10 | African Discoveries | Curiosity | 🔮 Future |
| 11 | Tech Makers | Creation | ✅ LIVE |
| 12 | Design Studio | Creation | 🔮 Future |
| 13 | Robotics Lab | Creation | 🔮 Future |
| 14 | AI Explorer | Creation | 🔮 Future |
| 15 | Digital Creator | Creation | 🔮 Future |
| 16 | Truth Seekers | Thinking | ✅ LIVE |
| 17 | Logic Lab | Thinking | 🔮 Future |
| 18 | Debate Academy | Thinking | 🔮 Future |
| 19 | Problem Solver | Thinking | 🔮 Future |
| 20 | Research Skills | Thinking | 🔮 Future |
| 21 | Mzansi Money | Money | ✅ LIVE |
| 22 | Side Hustle Lab | Money | 🔮 Future |
| 23 | Personal Budget Coach | Money | 🔮 Future |
| 24 | Smart Shopper | Money | 🔮 Future |
| 25 | Financial Wellness | Money | 🔮 Future |
| 26 | Micro Founders | Empowerment | ✅ LIVE |
| 27 | Career Explorer | Empowerment | 🔮 Future |
| 28 | Leadership Academy | Empowerment | 🔮 Future |
| 29 | Community Builder | Empowerment | 🔮 Future |
| 30 | Life Skills | Empowerment | 🔮 Future |
| 31 | Opportunity Hub | iKhaya | ✅ LIVE |
| 32 | Skills Passport | iKhaya | 📋 Planned |
| 33 | Job Ready | iKhaya | 📋 Planned |
| 34 | Employer Connect | iKhaya | 📋 Planned |
| 35 | Local Opportunities | iKhaya | 📋 Planned |
| 36 | Parent Hub | Community | 🔮 Future |
| 37 | Teacher Hub | Community | 🔮 Future |
| 38 | Volunteer Hub | Community | 🔮 Future |
| 39 | Community Projects | Community | 🔮 Future |
| 40 | People's Forum | Community | 🔮 Future |

---

## Existing live apps not yet reconciled to a v3 slot

These apps shipped during v2 and don't have a clean 1:1 v3 mapping. Each will be resolved in
a future architecture pass — they are not forgotten, just in-progress.

| App | v2 role | Closest v3 slot(s) |
|---|---|---|
| Everyday Foundations | Adult "second front door" — literacy, numeracy, digital skills, civic knowledge | Spans Foundations (#3/#4) and Empowerment (#30 Life Skills) |
| Our World | Belonging journey — Place · People · Planet (SA geography, African history, cultures) | African Discoveries (#10) |
| SIFISO — The Golden Hand | 5-in-1: Python · AI · Quiz · Startup · Commons | AI Explorer (#14) + Micro Founders (#26) |

---

## Related

- [`../../BLUEPRINT.md`](../../BLUEPRINT.md) — the full operational blueprint (source of truth).
- [`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md) — the DNA split in depth.
- [`03-tph-core-and-passport.md`](./03-tph-core-and-passport.md) — the shared platform.
- Per-app memories: [`../apps/`](../apps/).
