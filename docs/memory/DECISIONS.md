# Decision Log (evolution-aware)

> The major decisions that shaped the system, told as *evolution* — not just what was chosen,
> but what it replaced and why. This complements the root [`../../DECISIONS.md`](../../DECISIONS.md)
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
- See [`canon/01-capability-architecture.md`](./canon/01-capability-architecture.md).

## D-02 · The World A / World B DNA split (2026-06-21)
- **Decision:** two engineering worlds that **never mix**. *World A* = offline learning (no login,
  no server, no tracking, #FreeForever). *World B* = opportunity infrastructure (accounts, PII,
  POPIA, moderation, server) = **iKhaya**.
- **Why:** they are genuinely different engineering problems with different risk, cost, and trust
  profiles. Mixing them would contaminate the free/offline/no-data promise of the learning apps.
- **The bridge:** the Money & Empowerment pillars span both — an offline app *teaches* the
  capability for free, then *hands off* to iKhaya to connect the learner to real opportunity.
- See [`canon/02-world-a-world-b-dna.md`](./canon/02-world-a-world-b-dna.md).

## D-03 · Web-first delivery (2026-06-12)
- **Before:** Google Play as the primary release channel (the "release machine").
- **Change:** ship each learning app as an offline, installable **Cloudflare Pages PWA**, then
  surface it as a card on the People's Home site.
- **Why:** Play review was slow and morale-sapping; the apps were already React+Vite, so PWA
  conversion was cheap; PWAs reach the low-connectivity SA audience better (install once, run offline).
- **Tail:** Science Sprouts (already granted production access) is the **last app on Play ever**
  (2026-06-21); after it, the Play machine is retired.
- See [`canon/04-delivery-model.md`](./canon/04-delivery-model.md).

## D-04 · Ages, never grades (standing, reaffirmed 2026-06-21)
- **Decision:** present everything by **AGE**. CAPS/IGCSE alignment is internal only; grade labels
  must never render in UI. Smoke test intent: zero `Grade|GR[0-9]` strings.
- **Plus (2026-06-21):** **every learning app's age ceiling reaches 17** (ages-not-grades). This is
  what forced Science Sprouts (3–12) to extend to 13–17.
- **Why:** grades gatekeep and shame; age is universal and dignified, and fits learners who missed
  schooling. It's a core part of "technology should empower, not gatekeep."
- See [`canon/03-product-rules.md`](./canon/03-product-rules.md).

## D-05 · #FreeForever, offline, no-data — for learning apps (standing)
- **Decision:** learning apps carry no ads, no IAP, no paywalls, no accounts, require no internet,
  and collect no data. Forever.
- **The one exception / fork:** **iKhaya's backend cost.** World B needs servers, so it's the one
  place "free forever" needs a sustainability answer — **to be resolved before iKhaya's 2027 launch.**
- See [`canon/03-product-rules.md`](./canon/03-product-rules.md), [`platform/ikhaya.md`](./platform/ikhaya.md).

## D-06 · SIFISO stays a separate app from Tech Makers (2026-06-20)
- **Decision:** keep SIFISO (The Golden Hand) separate; don't merge into Tech Makers.
- **Why:** different audience and depth; merging would bolt heavy Pyodide+Monaco onto Tech Makers'
  light bundle. (Module-over-new-app has limits — when DNA/weight genuinely differ, keep them apart.)

## D-07 · "Learn Python" → "The Golden Hand" (2026-06-23)
- **Decision:** rename ecosystem-wide; keep the repo slug + URL (`sifiso-learn-python`).
- **Why:** it was always a five-app journey, not a Python course; the name should tell the truth.
  Slug/URL kept to avoid breaking the Cloudflare link. See [`HISTORY.md`](./HISTORY.md).

## D-08 · Micro Founders = a Venture *Journey*, not parallel age-muscles (2026-06-23)
- **Decision:** the spine is a **5-stage sequence** (Spot→Cost→Sell→Build→Pitch) with sequential
  unlock — deliberately *unlike* Truth Seekers' parallel age-muscle shape.
- **Why:** founding is *directional* (you can't cost what you haven't spotted); reasoning skills are
  *independent* (any order). The two apps modelling differently teaches the difference between a
  *set of skills* and a *journey*. Age survives as a within-stage difficulty dial.
- **Boundary:** Micro Founders = *make* money (venture); Mzansi Money = *manage* money (literacy).
- See [`apps/micro-founders.md`](./apps/micro-founders.md), [`../../MICRO_FOUNDERS.md`](../../MICRO_FOUNDERS.md).

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

---

> **Open decisions (not yet resolved):**
> - The **#FreeForever funding fork** for iKhaya (the one place free-forever needs an answer).
> - Whether **Digital Creator Academy** ever becomes a real app (parked).
> - The eventual relationship between the various Golden Hand framings (offline prototype vs any
>   server-backed direction) — see [`apps/the-golden-hand.md`](./apps/the-golden-hand.md).
