# THE PEOPLE'S HOME
## National Capability Blueprint — v3 (40-App Ecosystem)

> **Version history:**
> - v1 — ~40 independent apps. A backlog. Unstructured and unbuildable as described.
> - v2 (2026-06-21) — collapsed to ≈10 deep apps + iKhaya + shared core. Produced the 10 live
>   World-A apps and the iKhaya platform. The right move for the build phase.
> - v3 (2026-06-29, current) — **40 apps across 8 capability categories**, with a clear taxonomy
>   and shared platform. Unlike v1 (chaotic backlog), v3 is a structured long-term architecture.
>   The 10 live apps from v2 are the first wave and map into this structure. The module-over-app
>   discipline still applies *within* each app — but the 40 slots are the canonical long-term map.
>
> **Read this as architecture, not a sprint backlog.** The map of the territory, not the list of
> what to build next. Sequencing lives in the roadmap.

---

## Mission

> To provide every South African with a complete pathway to **learn, think, build, earn, and create
> opportunity** — regardless of age, income, location, or formal education.

## The guiding principle

> **Every app must build a human capability or unlock a real opportunity.**

---

## The model: Capability → Implementation → DNA

Every item is classified three ways:

1. **Capability** — what a person *gains* (the real unit of value).
2. **Implementation** — the lightest delivery: **App** · **Module** (inside an app) · **Service**
   (shared platform). *Prefer the lightest — not every slot below requires its own repo.*
3. **DNA** — which of two engineering worlds it lives in:

| | **World A — Offline Learning** | **World B — Opportunity Infrastructure** |
|---|---|---|
| Examples | All 35 learning apps (categories 1–7) | iKhaya (category 7) + Community & People (8) |
| Login | none | accounts / profiles |
| Server | none | yes |
| Data | no tracking, on-device | relationships, PII, POPIA, moderation |
| Internet | not required | required |
| Status | **proven, repeatable** | iKhaya platform |

---

## Top-level architecture

```
THE PEOPLE'S HOME
        │
   TPH CORE  ── shared SERVICES (not apps)
        │      Identity · Progress · Achievements · Badges · Households ·
        │      Caregiver Dashboard · Offline Engine · Learning Analytics ·
        │      Avatar Evolution · Cross-App Journey · Core SDK
        │
   ┌────┴──── WORLD A — Offline Learning ──────────────────────────────────────┐
   │  1. Foundations  2. Curiosity  3. Creation  4. Thinking  5. Money  6. Empowerment
   └────────────────────────────────────────────────────────────────────────────┘
        │             "the bridge" — capability hands off to opportunity
   ┌────┴──── WORLD B — Opportunity Infrastructure ─────────────────────────────┐
   │  7. iKhaya Ecosystem  8. Community & People
   └────────────────────────────────────────────────────────────────────────────┘
```

---

# THE 40 APPS

## Category 1 · FOUNDATIONS
**Build the ability to learn.**
**Capability:** Basic participation in society — numeracy, literacy, digital basics.
**Audience:** Children · Youth · Adults who missed schooling · Elders · Parents.

| # | App | Status |
|---|---|---|
| 1 | **Math Adventure RPG** | ✅ LIVE |
| 2 | **ReadAfrica** | ✅ LIVE |
| 3 | **Early Numeracy** | 🔮 Future |
| 4 | **Early Literacy Games** | 🔮 Future |
| 5 | **Parent Companion** | 🔮 Future |

> **Existing live app not in this table:** **Everyday Foundations** (adult "second front door" —
> literacy, numeracy, digital skills, civic knowledge for people who missed schooling). It spans
> the Foundations and Empowerment categories and will be reconciled in a future architecture pass.

---

## Category 2 · CURIOSITY & KNOWLEDGE
**Build curiosity.**
**Capability:** Understanding the world — science, nature, space, human body, African context.

| # | App | Status |
|---|---|---|
| 6 | **Science Sprouts** | ✅ LIVE |
| 7 | **Nature Explorer** | 🔮 Future |
| 8 | **Space Explorer** | 🔮 Future |
| 9 | **Human Body Explorer** | 🔮 Future |
| 10 | **African Discoveries** | 🔮 Future |

> **Existing live app not in this table:** **Our World** (Belonging journey — Place · People ·
> Planet, covering SA geography, African history, world cultures). Maps closest to African
> Discoveries (#10) and will be reconciled in a future architecture pass.

---

## Category 3 · CREATION & TECHNOLOGY
**Build creators.**
**Capability:** Turn consumers into creators — code, design, robotics, AI literacy, digital media.

| # | App | Status |
|---|---|---|
| 11 | **Tech Makers** | ✅ LIVE |
| 12 | **Design Studio** | 🔮 Future |
| 13 | **Robotics Lab** | 🔮 Future |
| 14 | **AI Explorer** | 🔮 Future |
| 15 | **Digital Creator** | 🔮 Future |

> **Existing live app not in this table:** **SIFISO — The Golden Hand** (5-in-1: Python · AI ·
> Quiz · Startup · Commons). Spans Creation (#14 AI Explorer) and Empowerment (#26 Micro Founders).
> Will be reconciled in a future architecture pass.

---

## Category 4 · THINKING & REASONING
**Build thinkers.**
**Capability:** Judgment — telling true from false, logical reasoning, argumentation, problem solving.

| # | App | Status |
|---|---|---|
| 16 | **Truth Seekers** | ✅ LIVE |
| 17 | **Logic Lab** | 🔮 Future |
| 18 | **Debate Academy** | 🔮 Future |
| 19 | **Problem Solver** | 🔮 Future |
| 20 | **Research Skills** | 🔮 Future |

> Note: Truth Seekers (#16) already contains Logic Lab, Debate SA, Problem Solver, and Systems
> Thinking as internal modules. The v3 slots (#17–20) represent standalone apps for the long term
> — until then, these capabilities live as modules inside Truth Seekers.

---

## Category 5 · MONEY & OPPORTUNITY
**Build financial capability.**
**Capability:** Numeracy applied to real life — budgeting, saving, side hustles, financial wellness.

| # | App | Status |
|---|---|---|
| 21 | **Mzansi Money** | ✅ LIVE |
| 22 | **Side Hustle Lab** | 🔮 Future |
| 23 | **Personal Budget Coach** | 🔮 Future |
| 24 | **Smart Shopper** | 🔮 Future |
| 25 | **Financial Wellness** | 🔮 Future |

---

## Category 6 · REAL-WORLD EMPOWERMENT *(spans World A → B)*
**Build independence.**
**Capability:** Build a venture; turn capability into real-world impact.

| # | App | Status |
|---|---|---|
| 26 | **Micro Founders** | ✅ LIVE |
| 27 | **Career Explorer** | 🔮 Future |
| 28 | **Leadership Academy** | 🔮 Future |
| 29 | **Community Builder** | 🔮 Future |
| 30 | **Life Skills** | 🔮 Future |

> The bridge: Micro Founders (#26) teaches venture-building offline → hands off to iKhaya
> Opportunity Ecosystem (#31–35) to connect the learner to real opportunity.

---

## Category 7 · iKHAYA — OPPORTUNITY ECOSYSTEM *(World B)*
**Build livelihoods.**
**Capability:** Connect capability to real-world opportunity — jobs, skills, employers, local economy.

| # | App / Module | Status |
|---|---|---|
| 31 | **Opportunity Hub** | ✅ LIVE (ikhaya.pages.dev) |
| 32 | **Skills Passport** | 📋 Planned |
| 33 | **Job Ready** | 📋 Planned |
| 34 | **Employer Connect** | 📋 Planned |
| 35 | **Local Opportunities** | 📋 Planned |

> iKhaya is the World-B platform. These are modules within iKhaya, not separate PWAs —
> they share the iKhaya backend, accounts, and POPIA infrastructure.
> iKhaya's #FreeForever funding fork must be resolved before the 2027 flagship launch.

---

## Category 8 · COMMUNITY & PEOPLE *(World B)*
**Strengthen families and communities.**
**Capability:** Support the people around the learner — parents, teachers, volunteers, community.

| # | App / Module | Status |
|---|---|---|
| 36 | **Parent Hub** | 🔮 Future |
| 37 | **Teacher Hub** | 🔮 Future |
| 38 | **Volunteer Hub** | 🔮 Future |
| 39 | **Community Projects** | 🔮 Future |
| 40 | **People's Forum** | 🔮 Future |

> Community & People is an entirely new category — nothing in v2 covered this. These live in
> World B (accounts, moderation) and are lowest priority behind the learning apps and iKhaya.

---

# SHARED PLATFORM (not apps)

The connective tissue across every product. Powered by the **TPH Core SDK**.

```
Shared Identity          — one person, one record, across all apps
Shared Progress          — stamps, milestones, journeys carry across apps
Achievements & Badges    — capability markers, not grades
Households               — family / shared-device mode
Caregiver Dashboard      — parents, teachers, mentors see progress
Offline Engine           — service worker pattern, shared across all World-A apps
Learning Analytics       — on-device only; no data leaves the phone
Avatar Evolution         — grows with the learner's journey
Cross-App Journey        — the thread connecting all 40 apps into one journey
The People's Home Core SDK — the shared package (@tph/core) all apps consume
```

---

# The complete journey

```
FOUNDATIONS (1–5)
│ Learn to read, count, participate.
▼
CURIOSITY (6–10)
│ Understand the world.
▼
CREATION (11–15)
│ Make things — code, design, build.
▼
THINKING (16–20)
│ Reason, judge, argue well.
▼
MONEY (21–25)
│ Handle money, spot opportunity.
▼
EMPOWERMENT (26–30)
│ Build a venture, lead, contribute.
▼
iKHAYA (31–35)
│ Connect to real opportunity — jobs, skills, livelihoods.
▼
COMMUNITY (36–40)
  Support the people around the learner.
```

---

# Status legend

| Mark | Meaning |
|---|---|
| ✅ LIVE | Shipped and accessible |
| 📋 Planned | On the roadmap for near-term build |
| 🔮 Future | Long-term canonical slot — not yet scheduled |
