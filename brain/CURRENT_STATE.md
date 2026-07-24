# Current State

> A snapshot of where everything stands. **Read this before doing any work.**
> For live build configs / URLs see [`../ECOSYSTEM.md`](../ECOSYSTEM.md);
> for the running status board see [`../ROADMAP.md`](../ROADMAP.md).
>
> **As of:** 2026-07-10.

---

## The headline — the Portfolio Launch, 9 August 2026 (decided 2026-07-21)

**The date is set: `2026-08-09`.** The public launch of The People's Home **portfolio** — not a
website launch, not a single-product release, but the initial collection of flagship educational
experiences presented together as the first public expression of The People's Home. Decision:
[`decisions/DECISIONS.md`](./decisions/DECISIONS.md) → **D-17**. Evidence:
[`launch-readiness-2026-08-09.md`](./launch-readiness-2026-08-09.md).

**Launch as planned, with four conditions:** prioritise the real-child play-tests and record the
evidence · resolve the documentation inconsistencies the review found · complete founder approvals ·
**defer MA-2**.

**What the readiness review concluded.** The portfolio is **technically ready but evidentially thin.**
All six flagships type-check clean and serve real content; nothing is broken. But the §4 seven-gate
bar had **never been applied to the six apps that will be the public face** — they were *designated*
by D-14, and §4 was written in the same change to govern *future* promotions. Accessibility and
educational review are unevidenced across the launch face.

**The critical path is not Numeria.** One un-run **real-child play-test** blocks all nine Early
Numeracy phase freezes at once, plus Early Literacy, African Discoveries and Space Explorer. It is an
*experiential* gate — observation, not automatable, closable only by the founder. MA-1 (Numeria Living
World) shipped 2026-07-21; **MA-2 is deferred** on this evidence.

> ⚠️ **Known-stale below.** The sections that follow are the 2026-07-10 snapshot and have not been
> reconciled — the review found `ECOSYSTEM.md` missing three live apps (Everyday Foundations entirely;
> Mzansi Money and Our World lack repo/URL rows) and repo visibility misrecorded. Remediation is
> condition 2 of D-17 and deliberately **not** yet done: the review does not fix what it finds.

---

## Prior headline — the Community Release (2026-07-10)

The project has entered its **release to the community**. The People's Home site is being **curated
to six flagships — one per pillar** (Math Adventure RPG · African Discoveries · Tech Makers · Truth
Seekers · Mzansi Money · Micro Founders), with every other app kept **listed** in a three-tier
roadmap (🌟 Available Today → 🏗 Currently Growing → 🌱 Future Collection) rather than as a flat
"live" list. In parallel, **Math Adventure RPG** is formalised into **two editions** — a frozen
**Google Play LTS** and a **web Community Edition** innovation lab — governed by the **Stable Build
Principle**. The operating model is captured in the new [`community-release.md`](./community-release.md)
Constitution and [`apps/math-adventure-release-policy.md`](./apps/math-adventure-release-policy.md).
See [`decisions/DECISIONS.md`](./decisions/DECISIONS.md) → **D-14, D-15**.

> The authoritative *current* live set is the operational layer — [`../ROADMAP.md`](../ROADMAP.md) /
> [`../ECOSYSTEM.md`](../ECOSYSTEM.md). The tables below are the *build-phase* snapshot and lag the
> newest apps (Space Explorer, African Discoveries — both LIVE) and the Early Numeracy → Number
> Kingdom work; reconcile against the operational docs.

## Prior headline (build phase, 2026-06-27)

**Every World-A pillar now has at least one live app.** With **Our World** shipping on
2026-06-27, the BLUEPRINT's "current" learning products are all live as offline Cloudflare
Pages PWAs, each surfaced as a card on the People's Home site. The project has moved from
*"build the apps"* into *"deepen them + build the platform + build iKhaya."* Since then: **Space
Explorer** (Curiosity) and **African Discoveries** (Curiosity) were brought in-house and shipped
LIVE; **Early Numeracy** is mid-transformation into **🌈 Number Kingdom** and was pulled back to
not-live-but-listed on the site (UI rework, 2026-07-06).

---

## World A — learning apps (all LIVE as offline PWAs)

| App | Pillar | One-line state | Memory |
|---|---|---|---|
| Math Adventure RPG | Foundations | Numeracy 3–17. Live web PWA + on Play (maintenance). The original app. | [apps/math-adventure-rpg](./apps/math-adventure-rpg.md) |
| ReadAfrica | Foundations | Literacy 3–17. Hosts the **TPH Core SDK** (embedded). | [apps/read-africa](./apps/read-africa.md) |
| Science Sprouts | Curiosity | Science **3–17** ✅ (teen Science Academy tier added). **Last app on Google Play, ever.** | [apps/science-sprouts](./apps/science-sprouts.md) |
| Tech Makers | Creation | Maker/coding arc 3–17. | [apps/tech-makers](./apps/tech-makers.md) |
| SIFISO — The Golden Hand | Creation | 5-app-in-one journey (Learn→AI→Quiz→Startup→Commons). Offline Python via Pyodide. | [apps/the-golden-hand](./apps/the-golden-hand.md) |
| Truth Seekers | Reasoning | Teens 13–17, fully reasoning-native after Phase 2. | [apps/truth-seekers](./apps/truth-seekers.md) |
| Micro Founders | Empowerment | Teens 13–17, 5-stage Venture Journey. | [apps/micro-founders](./apps/micro-founders.md) |
| Mzansi Money | Money | Teens 13–17, 5-stage Money Journey. | [apps/mzansi-money](./apps/mzansi-money.md) |
| Everyday Foundations | Foundations | Adult "second front door." 4 of 5 areas deep. | [apps/everyday-foundations](./apps/everyday-foundations.md) |
| Our World | Curiosity | Belonging journey (Place·People·Planet). Shipped 2026-06-27. | [apps/our-world](./apps/our-world.md) |

## Foundations — youngest-learner on-ramps

| App | Pillar | One-line state | Memory |
|---|---|---|---|
| Early Numeracy | Foundations | Number-sense 3–7. Phase 1 shell built (2026-06-30); **not yet deployed** (PWA-ready). | [apps/early-numeracy](./apps/early-numeracy.md) |
| Early Literacy | Foundations | Emergent literacy 3–7 ("Village"). Built externally (Gemini); Phases 1–4 + nav. **✅ LIVE as installable offline PWA — https://early-literacy.pages.dev/ (2026-07-02).** AI dropped for #FreeForever; repo moved to the org; senior audit run + **Phase-1 critical fixes applied** (removed hidden Google audio calls, audio-context leak, error boundary). Remaster backlog Phases 2–5 in memory. ⚠️ "TPH Core" naming collision open. | [apps/early-literacy](./apps/early-literacy.md) |

## World B — opportunity infrastructure (iKhaya)

| Surface | State | Memory |
|---|---|---|
| iKhaya core | Prototype ~4/10 (Lovable). 2026 goal: one-suburb closed beta. 2027 flagship launch. | [platform/ikhaya](./platform/ikhaya.md) |
| iKhaya Learn | AI-tutored web/coding portal 13–17, freemium. Server-backed (different DNA). | [platform/ikhaya-learn](./platform/ikhaya-learn.md) |

## Platform

| Piece | State | Memory |
|---|---|---|
| TPH Core SDK | Embedded in ReadAfrica; **extraction to a shared package is now the lead platform item.** | [platform/tph-core](./platform/tph-core.md) |
| People's Home Passport | Cross-app shared state via downloadable JSON (export→import). First real impl in Our World. | [platform/peoples-home-passport](./platform/peoples-home-passport.md) |

> **Note on the Math Adventure passport work (this repo, 2026-06-27):** PRs #1 and #2 landed
> the Passport in Math Adventure and adopted the shared `@tph/core` envelope. This makes Math
> Adventure a real consumer of the passport pattern — see
> [platform/peoples-home-passport](./platform/peoples-home-passport.md).

---

## What is *next* (the live edge of the work)

1. **TPH Core SDK extraction** — pull it out of ReadAfrica into a shared package and adopt it
   across apps. *Now the lead item* (the build-the-apps phase is done).
2. **Deepen passes** — the apps shipped with one journey/area authored deep and the rest
   "Coming soon." Filling those out is the post-2026 backlog (more Journeys in Our World, more
   areas in Everyday Foundations, age-band depth, bespoke activities).
3. **iKhaya** — steady background track toward a one-suburb beta; **the #FreeForever funding
   fork must be resolved before its 2027 launch** (see [platform/ikhaya](./platform/ikhaya.md)).
4. **isiZulu native-speaker review** — every app ships English-first with isiZulu as DRAFT;
   a batched review is deferred to ~December 2026.

## Known debts / risks

- ~~**Keystore off-machine backup** — outstanding, high priority.~~ — ✅ **CLOSED 2026-07-23**
  (work spanning the evening of 2026-07-22 into the early hours of 2026-07-23). The signing `.jks`
  files are backed up off-machine and integrity-verified. **This closes R1 — the only risk the
  launch readiness review rated *existential*** — satisfying the review's own condition 1
  ([`launch-readiness-2026-08-09.md`](./launch-readiness-2026-08-09.md) §8) and priority #2 of §9.
  ⚠️ **It does not close any of D-17's four conditions**, whose condition 1 is the real-child
  play-tests. Two separate numbered lists; do not conflate them.
  The technical evidence (verification method, location, filenames) is deliberately **not** recorded
  here: it lives in the implementation repository, which remains its single source of truth. This
  layer records portfolio state only.
  Standing debt for context: [`HISTORY.md`](./history/HISTORY.md) and the root
  [`DECISIONS.md`](../decisions/DECISIONS.md) → "Critical-information risk."
- **"Expert Approved" badge** (Math Adventure) was rejected on Play; the fix (less text for young
  ages, calmer sounds) carries over to the PWA.
- **The strategy brain** used to live only in machine-local AI memory + the plan file. This
  memory system is the durable home for it — keep it current.
