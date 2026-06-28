# Decision Log (evolution-aware)

> The major decisions that shaped the system, told as *evolution* — not just what was chosen,
> but what it replaced and why. This complements the root [`../DECISIONS.md`](../decisions/DECISIONS.md)
> (the operational decision list); this version emphasises the *thinking that changed*.
>
> **Append, don't rewrite.** Superseding a decision = a new dated entry referencing the old one.

---

## D-01 · The People's Home is a capability *system*, not a list of apps (2026-06-21)
- **Before:** a v1 blueprint of ~40 independent apps — a backlog.
- **Change:** reclassify everything as **Capability → Implementation (App/Module/Service) → DNA**.
  Result: ≈10 deep offline learning apps + one opportunity platform (iKhaya) + a shared core.
- **Why:** 40 products is unbuildable by a solo developer and conceptually wrong — most "apps"
  were *modules* of a few deep products. The system has a *shape*, not a length.
- **Consequence:** **module-over-new-app discipline** — prefer a module inside an existing app;
  only spin a new product when capability *and* DNA both warrant it. This is what stops the
  blueprint drifting back toward 40 products.
- See [`architecture/01-capability-architecture.md`](./architecture/01-capability-architecture.md).

## D-02 · The World A / World B DNA split (2026-06-21)
- **Decision:** two engineering worlds that **never mix**. *World A* = offline learning (no login,
  no server, no tracking, #FreeForever). *World B* = opportunity infrastructure (accounts, PII,
  POPIA, moderation, server) = **iKhaya**.
- **Why:** they are genuinely different engineering problems with different risk, cost, and trust
  profiles. Mixing them would contaminate the free/offline/no-data promise of the learning apps.
- **The bridge:** the Money & Empowerment pillars span both — an offline app *teaches* the
  capability for free, then *hands off* to iKhaya to connect the learner to real opportunity.
- See [`architecture/02-world-a-world-b-dna.md`](./architecture/02-world-a-world-b-dna.md).

## D-03 · Web-first delivery (2026-06-12)
- **Before:** Google Play as the primary release channel (the "release machine").
- **Change:** ship each learning app as an offline, installable **Cloudflare Pages PWA**, then
  surface it as a card on the People's Home site.
- **Why:** Play review was slow and morale-sapping; the apps were already React+Vite, so PWA
  conversion was cheap; PWAs reach the low-connectivity SA audience better (install once, run offline).
- **Tail:** Science Sprouts (already granted production access) is the **last app on Play ever**
  (2026-06-21); after it, the Play machine is retired.
- See [`canon/04-delivery-model.md`](./vision/02-delivery-model.md).

## D-04 · Ages, never grades (standing, reaffirmed 2026-06-21)
- **Decision:** present everything by **AGE**. CAPS/IGCSE alignment is internal only; grade labels
  must never render in UI. Smoke test intent: zero `Grade|GR[0-9]` strings.
- **Plus (2026-06-21):** **every learning app's age ceiling reaches 17** (ages-not-grades). This is
  what forced Science Sprouts (3–12) to extend to 13–17.
- **Why:** grades gatekeep and shame; age is universal and dignified, and fits learners who missed
  schooling. It's a core part of "technology should empower, not gatekeep."
- See [`canon/03-product-rules.md`](./vision/01-product-rules.md).

## D-05 · #FreeForever, offline, no-data — for learning apps (standing)
- **Decision:** learning apps carry no ads, no IAP, no paywalls, no accounts, require no internet,
  and collect no data. Forever.
- **The one exception / fork:** **iKhaya's backend cost.** World B needs servers, so it's the one
  place "free forever" needs a sustainability answer — **to be resolved before iKhaya's 2027 launch.**
- See [`canon/03-product-rules.md`](./vision/01-product-rules.md), [`platform/ikhaya.md`](./platform/ikhaya.md).

## D-06 · SIFISO stays a separate app from Tech Makers (2026-06-20)
- **Decision:** keep SIFISO (The Golden Hand) separate; don't merge into Tech Makers.
- **Why:** different audience and depth; merging would bolt heavy Pyodide+Monaco onto Tech Makers'
  light bundle. (Module-over-new-app has limits — when DNA/weight genuinely differ, keep them apart.)

## D-07 · "Learn Python" → "The Golden Hand" (2026-06-23)
- **Decision:** rename ecosystem-wide; keep the repo slug + URL (`sifiso-learn-python`).
- **Why:** it was always a five-app journey, not a Python course; the name should tell the truth.
  Slug/URL kept to avoid breaking the Cloudflare link. See [`HISTORY.md`](./history/HISTORY.md).

## D-08 · Micro Founders = a Venture *Journey*, not parallel age-muscles (2026-06-23)
- **Decision:** the spine is a **5-stage sequence** (Spot→Cost→Sell→Build→Pitch) with sequential
  unlock — deliberately *unlike* Truth Seekers' parallel age-muscle shape.
- **Why:** founding is *directional* (you can't cost what you haven't spotted); reasoning skills are
  *independent* (any order). The two apps modelling differently teaches the difference between a
  *set of skills* and a *journey*. Age survives as a within-stage difficulty dial.
- **Boundary:** Micro Founders = *make* money (venture); Mzansi Money = *manage* money (literacy).
- See [`apps/micro-founders.md`](./apps/micro-founders.md), [`../MICRO_FOUNDERS.md`](../MICRO_FOUNDERS.md).

## D-09 · The Passport pattern over a central shared store (2026-06-27)
- **Decision:** carry a learner's progress *between* separate, offline apps via a **downloadable
  JSON file** (export → import), reusing the TPH export-envelope idea — **not** a central server
  store, and **not** shared `localStorage` (separate origins can't see each other's storage).
- **Why:** it's the only mechanism that survives *separate origins + offline + no-server* all at
  once. A central store would violate World-A's no-server/no-data rule.
- **Status:** first real impl in Our World; adopted in Math Adventure (PRs #1/#2) on `@tph/core`.
  Full `@tph/core` extraction deferred until it has multiple real consumers.
- See [`platform/peoples-home-passport.md`](./platform/peoples-home-passport.md).

## D-10 · Migrate the strategy brain into versioned docs (2026-06-21 → 2026-06-27)
- **Decision:** the ecosystem's reasoning must live in git, not in machine-local AI memory or a
  single plan file.
- **Why:** it was the most critical, least-protected asset — one wiped machine from being lost.
- **Realisation:** the root doc set (BLUEPRINT/ECOSYSTEM/ROADMAP/DECISIONS) began it; this
  `docs/memory/` system completes it as the canonical, evolution-aware institutional memory.

## D-11 · The People's Home founding decision — leave Google Play, build a home (during Science Sprouts build, 2025/2026)

- **Before:** Google Play was the delivery channel. Math Adventure RPG was published there.
  Science Sprouts was next in the pipeline.
- **The moment:** while building Science Sprouts, two things crystallised:
  1. Google Play has policies the founder disagrees with — distribution control, approval power,
     the ability to delist, the implied ownership of the relationship between builder and learner.
  2. The vision was larger than "publishing my apps" — it needed to be a *home* for the people:
     a place to learn, build, and achieve, built for them, not inside someone else's store.
- **The decision:** Science Sprouts becomes the last Play Store app, ever. The People's Home is
  founded — not as a technical framework, but as a values statement.
- **The founding purpose (verbatim from founder, 2026-06-28):**
  > *"I wanted to build a home for my apps and the people — where they'll learn, build, and achieve."*
- **Consequence:** every structural decision downstream flows from this moment:
  PWA-first (no store gatekeeping), #FreeForever (no paywall gatekeeping), offline-first
  (no connectivity gatekeeping), no accounts (no data gatekeeping), South Africa first
  (no geography gatekeeping). The "one belief" — *technology should empower society, not gatekeep it* —
  is this decision, made into a principle.
- See [`history/HISTORY.md`](./history/HISTORY.md) → "Origins" section.

## D-12 · Wire AI, don't activate it — AI must not create per-learner runtime cost (2026-06-28)

- **Context:** iKhaya Phase 9 wired in Claude-powered AI matching (consent page, proxy endpoint,
  two-tier intelligence engine). Phase 10 shipped without setting `ANTHROPIC_API_KEY` — the
  feature exists architecturally but is dormant.
- **The principle:** AI is used to **build** The People's Home (Claude Code, ChatGPT planning).
  That cost falls on the builder, once, per feature. That is acceptable.
  AI must **not run as a per-learner feature** in production, because that cost scales with every
  user — and #FreeForever means learners never pay, which means the builder absorbs it all.
  At scale that is unsustainable.
- **The rule:** wire AI capabilities into the architecture. Build the infrastructure. Build the
  consent flows. Build the proxy. But do not activate the API key until a sustainable model exists
  that does not violate #FreeForever. Local/offline alternatives (tag-based matching, on-device
  inference) are the real #FreeForever product. AI is the upgrade path for when the economics allow.
- **What "sustainable" means:** a grant, NGO funding, an organisational payment model
  (organisations pay to *post* opportunities; learners never pay), or on-device models that
  have zero API cost. Any of these unlocks the AI tier without taxing learners.
- **The exception that is not an exception:** using AI to *build* the product is fine.
  Claude Code, ChatGPT planning, AI-assisted scaffolding — these are build-time costs,
  not runtime costs. They do not violate #FreeForever.
- See [`PROJECT_DNA.md`](./PROJECT_DNA.md) → Principle 17.

---

> **Open decisions (not yet resolved):**
> - The **#FreeForever funding fork** for iKhaya (the one place free-forever needs an answer).
> - Whether **Digital Creator Academy** ever becomes a real app (parked).
> - The eventual relationship between the various Golden Hand framings (offline prototype vs any
>   server-backed direction) — see [`apps/the-golden-hand.md`](./apps/the-golden-hand.md).
