# Project Timeline

> The chronological evolution of The People's Home. How the thinking and the build
> actually unfolded. Dates are absolute. Where a precise date is not known, the entry says
> `Unknown` or gives the best-known window.
>
> This is the *story*; for the reasoning behind each turn see [`DECISIONS.md`](./decisions/DECISIONS.md),
> and for incidents see [`HISTORY.md`](./history/HISTORY.md).

---

## Origins (pre-2026) — `Unknown` precise dates

- **Math Adventure RPG** is the seed app — a numeracy RPG for children, React + Vite, later
  wrapped with Capacitor for Android. The first product and the template the rest inherit from
  (narration engine, ages-not-grades discipline, offline-first).
- **SIFISO — The Golden Hand** (then "Learn Python") existed as the *original prototype of the
  whole idea*: "one shell, five apps." It quietly proved the People's Home shape before the
  platform had a name.
- The umbrella vision — **iKhaya AI** / **ARISAN SIFISO Holdings** / a learning system from
  *childhood to opportunity* — predates the formal blueprint.

## 2026 — the build year

### Early June 2026
- **~06-09 — Keystore rotation** (Math Adventure). Upload key rotated to `upload-new.jks`;
  `keystore.properties` switched; v2.0/code5 AAB signed with the new key. (See [`HISTORY.md`](./history/HISTORY.md).)
- **06-09 — Play target-audience** declared (5&under → 16–17), to match the app's 3–17 content.
- **06-08 — People's Home website** first committed (static HTML/CSS umbrella site).

### Mid June 2026 — the two defining pivots
- **06-11 — Tech Makers** built (Creation/Technology pillar; Capacitor/React).
- **06-12 — THE WEB-FIRST PIVOT.** Stop prioritising Google Play (slow review, morale cost).
  Ship every learning app as an offline, installable **Cloudflare Pages PWA** + a card on the
  site. This is the hinge of the whole delivery model. (See [`canon/04-delivery-model.md`](./vision/02-delivery-model.md).)
- **06-17 — "Expert Approved" badge rejected** for Math Adventure on Play (too much text for
  young ages; disruptive sounds). The fix carries forward to the PWA.
- **06-20 — SIFISO stays a separate app** from Tech Makers (different audience/depth; avoid
  bolting Pyodide+Monaco onto Tech Makers' light bundle).
- **06-21 — THE CAPABILITY ARCHITECTURE (v2 BLUEPRINT).** The biggest conceptual reframe:
  ~40 imagined apps collapse into a **capability system** — ≈10 deep offline apps + iKhaya +
  TPH Core — classified by **Capability → Implementation → DNA**. The World A / World B split is
  formalised. (See [`architecture/01`](./architecture/01-capability-architecture.md), [`architecture/02`](./architecture/02-world-a-world-b-dna.md).)
- **06-21 — Google Play track CLOSED.** Science Sprouts is the *last app on Play, ever*; it was
  already granted production access, so it's finished out. Everything after ships web-first only.
- **06-21 — Critical-information risk identified.** The "strategy brain" was only in machine-local
  AI memory + a plan file. Migration into versioned docs (BLUEPRINT/ECOSYSTEM/ROADMAP/DECISIONS)
  begins. *(This memory system, 2026-06-27, is the completion of that migration.)*

### Late June 2026 — shipping the pillars
- **06-23 — "Learn Python" renamed → "The Golden Hand"** ecosystem-wide (repo/URL slug kept).
  Recognised as a five-app-in-one system, not a Python course.
- **06-23 — Micro Founders** blueprint locked + shipped: a **5-stage Venture Journey** (Spot→Cost→
  Sell→Build→Pitch), deliberately *not* Truth Seekers' parallel-muscle shape. Pillar 05 live.
- **06-23 — Mzansi Money vs Micro Founders** boundary set: *manage* money vs *make* money.
- **~06-24 — Truth Seekers** Phase 2: purged the borrowed Atelier engine scaffold, became fully
  reasoning-native, ~doubled case content. Pillar 04 live (13–17).
- **06-24 — Mzansi Money** shipped on the Micro Founders chassis. Pillar 06 (money-wisdom) live.
- **06-25 — Science Sprouts → age 17.** Teen "Science Academy" tier added (ported exam-studio
  engine). The **age-ceiling-17 rule is now satisfied** across Curiosity.
- **06-26 — Everyday Foundations** shipped: the adult "second front door." 4 of 5 areas deep.
  Foundations adult on-ramp satisfied.
- **06-27 — Our World** shipped: the belonging journey (Place·People·Planet). **With it, every
  World-A pillar has ≥1 live app.** The build-the-apps phase closes.
- **06-27 — People's Home Passport** in Math Adventure (PRs #1, #2): the cross-app shared-state
  mechanism (downloadable JSON), adopting the shared `@tph/core` envelope. Math Adventure becomes
  a real consumer of the pattern.
- **06-27 — THIS MEMORY SYSTEM authored** — the full institutional memory, completing the
  strategy-brain migration started 06-21.

---

## What the timeline shows

Two moves define 2026: the **web-first pivot** (06-12, *how* we ship) and the **capability
architecture** (06-21, *what* the system is). Everything after 06-21 is disciplined execution of
that architecture, pillar by pillar, finishing in a ~2-week sprint that put a live app in every
World-A pillar. The frontier now moves from *apps* to *platform (TPH Core)* and *opportunity (iKhaya)*.

## The next chapters (planned)
- **2026 H2** — TPH Core extraction; deepen passes; isiZulu review (~December); iKhaya one-suburb beta.
- **2027** — iKhaya / People's Home flagship launch; the #FreeForever funding fork resolved.
