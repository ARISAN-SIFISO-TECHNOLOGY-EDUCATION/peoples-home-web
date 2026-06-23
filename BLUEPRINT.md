# THE PEOPLE'S HOME
## National Capability Blueprint — v2 (Capability Architecture)

> **Status:** Rewritten 2026-06-21. v1 listed ~40 independent apps; v2 reorganises the same
> vision as a **capability system** — a small set of deep products, each with internal modules,
> split cleanly by engineering DNA. **The People's Home is not a collection of apps. It is a
> capability system.**
>
> **Read this as architecture, not a backlog.** The *map of the territory*, not the list of what
> to build next. Sequencing lives in the roadmap; this governs *where each thing belongs*.

---

## Mission
To provide every South African with a complete pathway to **learn, think, build, earn, and create
opportunity** — regardless of age, income, location, or formal education.

---

## The model: Capability → Implementation → DNA
Every item is classified three ways:
1. **Capability** — what a person *gains* (the real unit of value).
2. **Implementation** — the lightest way to deliver it: **App** · **Module** (inside an app) ·
   **Service** (shared platform).
3. **DNA** — which of two engineering worlds it lives in (they do not mix):

| | **World A — Offline Learning** | **World B — Opportunity Infrastructure** |
|---|---|---|
| Examples | Math Adventure, ReadAfrica, Truth Seekers | Jobs, mentors, funding, community |
| Login | none | accounts / profiles |
| Server | none | yes |
| Data | no tracking, on-device | relationships, PII, POPIA, moderation |
| Internet | not required | required |
| Status | **our proven strength** | a different engineering problem (= iKhaya) |

This single discipline collapses **~40 future apps → ~10 deep learning products + one opportunity
platform (iKhaya) + a shared core.**

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

**Rule:** every learning app's age ceiling reaches **17** (ages-not-grades). The Money &
Empowerment pillars *span both worlds*: an offline app **teaches**, then **hands off to iKhaya**
to connect the learner to real opportunity — that handoff is "the bridge."

---

# WORLD A — the offline learning products

## PILLAR 1 · FOUNDATIONS
**Capability:** Basic participation in society.
**Target:** Children · Youth · Adults who missed schooling · Elders.

| App | DNA | Modules |
|---|---|---|
| **Math Adventure RPG** *(live)* | Offline | Numeracy 3–17 |
| **ReadAfrica** *(live)* | Offline | Literacy 3–17 |
| **Everyday Foundations** *(new — the adult / never-schooled on-ramp)* | Offline | Literacy (Everyday English) · Numeracy (Everyday Maths) · Digital Skills (Digital Basics) · Civic Knowledge (Citizen Essentials: IDs/SASSA/municipal/rights) · Languages of SA (isiZulu·isiXhosa·Sesotho·English) |

## PILLAR 2 · CURIOSITY & KNOWLEDGE
**Capability:** Understanding the world.

| App | DNA | Modules |
|---|---|---|
| **Science Sprouts** *(live — extend to 17)* | Offline | Science · Ask Why (question-driven) · Nature Explorer (environment/conservation) |
| **Our World** *(new humanities app)* | Offline | Explore SA (geography) · History Alive (SA & African history) · World Explorer (cultures & global awareness) |

## PILLAR 3 · CREATION & TECHNOLOGY
**Capability:** Turn consumers into creators.

| App | DNA | Modules |
|---|---|---|
| **Tech Makers** *(live)* | Offline | Maker Studio · Coding arc (block → web → projects) · Robotics (electronics/automation basics) |
| **SIFISO — The Golden Hand** *(live)* | Offline | A five-step journey: Golden Learn (Python) · Golden AI (AI literacy) · Golden Quiz (mastery) · Golden Startup (*1M Startups*) · Golden Commons (*Each One, Teach One*). Web (HTML/CSS/JS) step planned. |

*Parked (future, undecided):* **Digital Creator Academy** (video/audio/graphics) — a genuine
capability but media-tooling is heavy and off-stack. **App Builder Lab / Open Source Builder** are
candidate *capstone modules* inside Tech Makers / The Golden Hand, not separate apps.

## PILLAR 4 · THINKING & REASONING
**Capability:** Judgment — telling true from false.

| App | DNA | Modules |
|---|---|---|
| **Truth Seekers** *(next for execution — v1 teens 13–17)* | Offline | Logic Lab · Media Detective (misinformation/manipulation) · Systems Thinking (cause & effect) · Decision Maker (scenarios) · Problem Solver (real-world sims) · Debate SA (civil argument) |

## PILLAR 5 · REAL-WORLD EMPOWERMENT *(spans World A → B)*
**Capability:** Build a venture; turn capability into impact.

| Implementation | DNA | Contents |
|---|---|---|
| **Micro Founders** *(app — the course)* | Offline | Startup Journey · Project Builder · Leadership Lab |
| *(handoff)* → **Community & Mentor Services** | **iKhaya / World B** | Mentor Network · Community Builder · Cooperative Builder · Civic Action · Impact Tracker |

## PILLAR 6 · MONEY & OPPORTUNITY *(spans World A → B — "the bridge")*
**Capability:** Connect learning to economic mobility.

| Implementation | DNA | Contents |
|---|---|---|
| **Mzansi Money** *(app — financial literacy)* | Offline | Budgeting · Saving · Debt & Interest · Banking · Financial Wellness · **Job Ready** (CVs/interview prep — offline, links into iKhaya) |
| *(handoff)* → **Opportunity Hub** | **iKhaya / World B** | The 6 navigators (University · TVET · Bursary · Career · Learnership · Internship) + Side Hustle Hub · Tender Starter · Funding Finder · Freelancer Toolkit |

---

# WORLD B — Opportunity Infrastructure (one platform: **iKhaya**)
Everything that needs accounts, profiles, relationships, notifications, POPIA and moderation lives
**inside iKhaya** — never as standalone offline apps. iKhaya carries the running backend cost (the
one #FreeForever exception, to be resolved before its 2027 flagship launch).

- **Opportunity Hub** — navigators + job/funding/hustle surfaces (above).
- **Community & Mentor Services** — mentors, communities, cooperatives, civic action, impact (above).

The offline learning apps **teach the capability for free, forever**; iKhaya is where a ready
learner **connects to real opportunity**. That clean seam is the whole "education → pathway" thesis.

---

# TPH CORE — shared services (not apps)
The connective tissue across every product. Already seeded as the **TPH Core SDK embedded in
ReadAfrica**; extraction to a shared package and adoption across the apps is the platform track.

- **Shared Identity · Shared Progress · Shared Rewards · Shared Lore · Shared Offline Engine**
- **Dashboards:** Parent · Mentor · Community

---

# Community layer (across all pillars)
The People's Home community supports every stage of the journey. **Members:** Learners · Parents ·
Teachers · Builders · Founders · Job Seekers · Elders · Community Leaders. (Community *features* are
World B — they live in iKhaya / TPH Core, not in the offline apps.)

---

# The whole ecosystem on one page (classification)

| Item | Implementation | DNA / Home |
|---|---|---|
| Math Adventure RPG | App | Offline Learning |
| ReadAfrica | App | Offline Learning |
| Everyday Foundations *(new)* | App (multi-module) | Offline Learning |
| Science Sprouts | App | Offline Learning |
| Our World *(new)* | App (multi-module) | Offline Learning |
| Tech Makers | App | Offline Learning |
| SIFISO — The Golden Hand | App (5-in-1: Learn/AI/Quiz/Startup/Commons) | Offline Learning |
| Truth Seekers | App (6 modules) | Offline Learning |
| Mzansi Money | App | Offline Learning |
| Micro Founders | App | Offline Learning |
| Digital Creator Academy | App | *Future — undecided* |
| Opportunity Hub | Platform module | iKhaya / World B |
| Community & Mentor Services | Platform module | iKhaya / World B |
| TPH Core (identity/progress/…) | Shared services | Platform |

**≈ 10 offline learning apps + 1 opportunity platform (iKhaya) + shared core** — an institutional
platform, not 40 products.

---

# LONG-TERM OUTCOME
A child can begin with Math Adventure RPG. A young person can learn Python. A job seeker can find
opportunities. A founder can build a business. An elder can learn digital literacy — **all within
one home.**

> ## One Home. Many Journeys. One Future.
