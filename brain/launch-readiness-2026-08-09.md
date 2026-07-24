# Portfolio Launch Readiness Review — 9 August 2026

> **Status: 📋 REVIEW — evidence gathered 2026-07-21. ✅ Decision recorded: [D-17](./decisions/DECISIONS.md)
> — *launch as planned on 2026-08-09, with conditions* (founder, 2026-07-21).**
> The evidence below is unchanged from before the decision, deliberately: this document records what
> was *found*, D-17 records what was *decided*. Do not edit the findings to match the outcome.
> Commissioned by the founder after MA-1 shipped, to answer *"is Numeria even the bottleneck?"*
> before further investment. **This review does not fix what it finds.**
>
> **19 days remain** between this review (2026-07-21) and the stated date.

---

## 1. The milestone

> ⚠️ **Recorded here first as FOUNDER-STATED · UNDER REVIEW**, so it stopped being an unwritten
> assumption while the evidence was gathered. **Ratified same day as [D-17](./decisions/DECISIONS.md)**
> — *launch as planned, with conditions* — after this review, not before it.

The founder's definition, verbatim (2026-07-21):

> 9 August is the planned public launch of The People's Home portfolio. It is not merely a website
> launch or a single-product release. It is a portfolio launch intended to present the initial
> collection of flagship educational experiences together as the first public expression of The
> People's Home.

**Before this document, the date appeared nowhere in the repository** — not in `ROADMAP.md`,
`PROJECT_TIMELINE.md`, `CURRENT_STATE.md`, `community-release.md`, or any `apps/*.md`.

### Why "portfolio launch" changes the standard

The Community Release (2026-07-10, **D-14**) was a **presentation** decision — *curation*, explicitly
reversible, *"status is one field per app."* Low stakes by design.

A **public portfolio launch is a different act**: the first time these apps are presented to
strangers as finished work. That is precisely the situation
[`community-release.md`](./community-release.md) §4's seven gates were written for.

---

## 2. Method

Each subject is scored against **`community-release.md` §4 as it already exists** — cited, never
restated (D-13, *one owner per rule*). No new checklist was invented.

`G1 Roadmap frozen · G2 Architecture frozen · G3 Production build clean · G4 Offline verified ·
G5 Accessibility reviewed · G6 Educational review complete · G7 Founder approval`

What §4 does **not** cover — it is an *app-promotion* bar, and a portfolio launch is wider — goes to
the **risk register** (§6) rather than being bolted onto §4.

### Evidence standard

Every mark states **how it is known**, not merely whether it passes:

| Mark | Meaning |
|---|---|
| ✅ **Verified** | Checked in this session — build run, URL fetched, file read |
| 📄 **Claimed** | Asserted in the Brain, not re-verified |
| ⏳ **Open** | Genuinely outstanding |
| ❓ **Unknown** | No evidence either way (`UPDATE_PROTOCOL.md` rule 4 — *"an honest Unknown is more valuable than a plausible fabrication"*) |

This exists because `CURRENT_STATE.md` **self-declares that it lags reality**. A review that simply
restates the Brain would report the project's own optimism back to the founder as fact.

---

## 3. Portfolio health — the executive view

| Dimension | Rating | Why |
|---|---|---|
| **Engineering readiness** | 🟢 **Strong** | All six flagships type-check clean ✅; all six URLs + the site serve real content ✅; Math Adventure RPG 376/376 tests and a clean Play build ✅ |
| **Educational readiness** | 🔴 **Unevidenced** | **G6 is unmet for all six.** No educational review is recorded for any flagship, and no app has been observed with a real child |
| **Operational readiness** | 🟡 **Works, with documentation defects** | Site renders correctly and only `live` cards are clickable ✅; but the registry is wrong in four ways (§6) |
| **Governance readiness** | 🟡 **Recorded, but nothing frozen** | D-14/D-15/D-16, the Constitution and Baseline 2026.1 all exist ✅; **no roadmap or architecture is frozen anywhere in the portfolio** ⏳ |
| **Founder readiness** | 🔴 **The binding constraint** | Every remaining gate is one only the founder can close: play-tests, educational review, G7 approval, and every freeze |

### The headline finding

> **The seven-gate bar has never been applied to the six apps that will be the public face.**

The founding six were **designated** by D-14, and §4 was written *in the same change* to govern
*future* promotions (*"An app may move `growing`/`future` → `live` only when…"*). That was correct
for a reversible curation. It means the gates were never run against the current flagship set — and
a public launch is the first moment that matters.

**The gap is evidential, not technical.** Nothing is broken. What is missing is proof.

### Portfolio composition

Three of six flagships — Truth Seekers, Mzansi Money, Micro Founders — serve **ages 13–17 only**.
The launch narrative reads *"Learn Mathematics → Discover Africa → Create Technology → Think
Critically → Manage Money → Build a Business"*, but half of it is unreachable to a 7-year-old. Not a
defect; a positioning fact the founder should choose deliberately before launch day.

---

## 4. Flagship scorecard

| Subject | G1 Roadmap | G2 Arch | G3 Build | G4 Offline | G5 A11y | G6 Edu | G7 Founder |
|---|---|---|---|---|---|---|---|
| **Math Adventure RPG** | ⏳ MA-0 draft | ⏳ MA-1 just landed | ✅ tsc + 376 tests + Play build | 📄 | 📄 `a11y-audit.mjs` exists | ⏳ *Expert Approved* **rejected** 2026-06-17 | ⏳ |
| **African Discoveries** | ❓ | 📄 in-housed, scaffold stripped | ✅ tsc clean | 📄 28-entry precache | ❓ | ⏳ play-test *"not yet done"* | ⏳ |
| **Tech Makers** | ❓ | 📄 `AUDIT.md` P0/P1 closed | ✅ tsc clean | 📄 fonts self-hosted | ❓ | ❓ | ⏳ |
| **Truth Seekers** | ❓ | 📄 Phase 2 reasoning-native | ✅ tsc clean | ❓ | ❓ | ❓ | ⏳ |
| **Mzansi Money** | ❓ | ❓ | ✅ tsc clean | ❓ | ❓ | ❓ | ⏳ |
| **Micro Founders** | 📄 Blueprint LOCKED 2026-06-23 | ❓ | ✅ tsc clean | ❓ | ❓ | ❓ | ⏳ |
| **The site** | n/a | ✅ no build step | ✅ serves, deploy current | n/a | ❓ | n/a | ⏳ |

**Verified this session:** all six repos `npx tsc --noEmit` clean · all six live URLs + the site
return real content · Math Adventure RPG 376/376 with no Living World asset in the Play build · the
site's deployed commit matches `origin/main` (`740ff7b`) · only `status:'live'` cards render as
clickable links, so no *Currently Growing* or *Future Collection* app is reachable from the site.

**Two engineering facts worth naming:**

1. **Five of the six flagships have no automated tests at all** — no `test` script exists in Tech
   Makers, Truth Seekers, Mzansi Money, Micro Founders or African Discoveries. Math Adventure RPG's
   376 tests are the portfolio's entire safety net. `tsc` clean is real, but it is a type check, not
   a behaviour check.
2. **G5 and G6 are near-universally ❓.** Only Math Adventure RPG has any accessibility tooling
   (`scripts/a11y-audit.mjs`, axe-core). For an educational product for children, these two gates
   *are* the product claim — they are not ceremony.

---

## 5. Currently Growing — distance to the bar

| App | State | Gap |
|---|---|---|
| **Early Numeracy / Number Kingdom** | ⏸ Deliberately not-live since 2026-07-06 (founder unhappy with the UI). Renders a non-clickable **BUILDING** card ✅ verified | Awaiting **founder UI-redo instructions**. All 10 educational phases built & live; NK-0…NK-3 frozen, NK-4 built awaiting freeze. **Not a launch blocker** — it is correctly excluded |
| **Early Literacy** | LIVE at its own URL; **BUILDING** card, not reachable from the site | M11 isiZulu + the real-child play-test. Its own memory: *"the only **true** 'done' gate left"* |

Neither is proposed for 9 August. Both are correctly presented as in-progress. **The planned
Foundations Collection cannot form by 9 August** — Early Numeracy is blocked on a founder decision
that has not been made.

---

## 6. Portfolio risk register

Ranked by (blast radius × likelihood). These are **not** §4 gates — they are what a portfolio launch
exposes that an app-promotion bar does not.

| # | Risk | Severity | Evidence | Owner |
|---|---|---|---|---|
| **R1** | **Android keystores exist only on this machine.** Losing one = that app can never be updated on Play again | 🔴 **Existential** | `ECOSYSTEM.md`: *"gitignored, local-only, irreplaceable"*; `CURRENT_STATE.md` lists it *"outstanding, high priority"* | Founder |
| **R2** | **No app has been observed with a real child.** The core product claim is untested | 🔴 **Critical** | §7 | Founder only |
| **R3** | **G5/G6 unevidenced across the launch face** — accessibility and educational review | 🟠 **High** | §4 scorecard | Founder + review pass |
| **R4** | **`ECOSYSTEM.md` — "the map of everything" — is missing three live apps** | 🟠 **High** | **Everyday Foundations: 0 mentions.** Mzansi Money (a *flagship*) and Our World appear only in prose, with **no repo / URL / build row** ✅ verified | Docs |
| **R5** | **Repo visibility is misrecorded.** Tech Makers and Mzansi Money are **PRIVATE**; `ECOSYSTEM.md` implies public | 🟡 **Medium** | ✅ verified via `gh` | Docs |
| **R6** | **The six pillars are named three different ways** — site vision section (*"Money & Opportunity"*, *"Real-World Empowerment"*) vs site app data (*"Money & Financial Capability"*, *"Entrepreneurship"*) vs the Brain. A visitor sees both on one page | 🟡 **Medium** | ✅ `index.html:643,644` vs `:743,753` | Founder (naming) |
| **R7** | **Nothing in the portfolio is frozen.** No app roadmap, no architecture — G1/G2 cannot be satisfied as written | 🟡 **Medium** | Founder act by definition | Founder |
| **R8** | **Five of six flagships have zero automated tests** | 🟡 **Medium** | ✅ verified | Engineering |
| **R9** | **`CURRENT_STATE.md` is stale** (dated 2026-07-10) and self-declares it | 🟢 **Low** | Self-documented | Docs |
| **R10** | **Math Adventure RPG's *Expert Approved* badge was rejected** (2026-06-17, text volume + disruptive sounds); the cause carries to the PWA | 🟢 **Low** for launch | `vision/01-product-rules.md` | Product |

**Not risks, though they look like ones:** the `truth-seekers` local folder has no `.git` — but the
remote is healthy (PUBLIC, `main`, pushed 2026-06-24, matching the recorded Phase 2 work) and
Cloudflare builds from the remote ✅. Early Numeracy being not-live is a *deliberate, upheld* founder
decision, not a regression ✅.

---

## 7. The experiential gap — the portfolio's real critical path

> **One un-run gate blocks more work than any other single item in the project.**

The **real-child play-test** is outstanding for:

| Subject | What it blocks |
|---|---|
| **Early Numeracy** | **All nine phase freezes at once** — every phase in `early-numeracy-roadmap.md` reads *"blocked only on the real-child play-test"* |
| **Early Literacy** | Its own memory: *"The only **true** 'done' gate left"* |
| **African Discoveries** | *"the standing World-A human gate… Not yet done"* |
| **Space Explorer** | Same gate |
| **Every World-A app** | It is part of the standing definition of done |

Per [`patterns/experiential-gates.md`](./patterns/experiential-gates.md) this is an **experiential
gate**: satisfied by *observation*, not by an engineer working alone, and **explicitly not
automatable**. It cannot be delegated to an AI, a test suite, or a review pass.

**What this means for the portfolio:** the remaining work across multiple products is no longer
primarily engineering — it is **validation with real learners**. That is a different kind of work,
it consumes founder time rather than build time, and none of it has started.

**Cost to close:** one child, a handful of sessions, per app. Days, not weeks. The blast radius is
enormous relative to the effort — this is the cheapest high-value action available before 9 August.

---

## 8. Verdict

### `Launch Recommended — with conditions`

Not *reduced scope*. Reducing the flagship set would not reduce the actual risk, because **the risk
is evidential, not per-app**: all six are live, type-clean and serving. Dropping one would remove a
pillar from the narrative without making the remaining five any better evidenced.

| Subject | Verdict |
|---|---|
| **Math Adventure RPG** | ✅ Launch-ready — best-evidenced app in the portfolio |
| **African Discoveries · Tech Makers · Truth Seekers · Mzansi Money · Micro Founders** | ✅ Launch-ready **technically**; ⏳ G5/G6 unevidenced |
| **The site** | ✅ Launch-ready after R6 (pillar naming) is settled |
| **Early Numeracy · Early Literacy** | ⏸ **Correctly deferred.** Present as *Currently Growing*, as today |
| **Foundations Collection** | ❌ **Cannot form by 9 August** — blocked on a founder decision not yet made |
| **iKhaya / World B** | ❌ Out of scope — 2027 |

**Conditions, in order:**

1. **R1 — back up the keystores off-machine.** Hours of work. It is the only *existential* risk in
   the register and it is unrelated to the launch date, which is exactly why it keeps being deferred.
2. **R6 — settle the pillar names.** A visitor sees two different names for the same pillar on one
   page.
3. **R4/R5 — reconcile `ECOSYSTEM.md`.** A flagship missing from the source-of-truth registry is the
   kind of thing that only hurts once someone else needs it.
4. **G7 — record founder approval against §4**, explicitly noting which gates are accepted as
   **unevidenced** at launch. Launching without full evidence is a legitimate founder choice; doing
   it *silently* is what corrodes the governance model.

---

## 9. Recommendation — the highest-value investment before 9 August

> ### 🥇 **Run the real-child play-tests. Numeria is not the bottleneck.**

Ranked on equal terms:

| Rank | Investment | Why |
|---|---|---|
| **1** | **Real-child play-tests** | Unblocks 9 Early Numeracy freezes + Early Literacy + African Discoveries + Space Explorer. **Only the founder can do it.** Days of effort, portfolio-wide payoff. Validates the core claim *before* strangers arrive |
| **2** | **Keystore backup (R1)** | Existential, cheap, and unrelated to any deadline — which is why it never gets done |
| **3** | **G5/G6 evidence sweep on the five unevidenced flagships** | Turns the launch face from *asserted* to *evidenced*. `math-adventure-rpg/scripts/a11y-audit.mjs` already exists and is portable |
| **4** | **Site + registry correctness (R4/R5/R6)** | Cheap, visible on launch day |
| **5** | **Early Numeracy UI decision** | Only path to the Foundations Collection; needs founder direction, not code |
| **6** | **Early Literacy M11 isiZulu** | Real, but it is not a 9 August flagship |
| **7** | **MA-2 (Numeria micro-animations)** | ⬅ **Lowest value right now.** It improves the app that is *already* the best-evidenced flagship. It adds polish where the portfolio has proof, and nothing where the portfolio has gaps |

**The case against MA-2 in one line:** Math Adventure RPG is the only flagship with tests, the only
one with accessibility tooling, and the one whose gates are closest to closed. Spending the next 19
days there widens the gap between the best-documented app and the five that need the attention.

### What would change this answer

This recommendation is falsifiable. It flips if any of the following is true:

- **The play-tests have already happened informally and simply were not recorded.** Then R2 is a
  *recording* problem, not a validation problem, and #3 (the evidence sweep) becomes first.
- **9 August is a soft date** — no press, no partners, no external commitment. Then launch risk drops
  sharply and MA-2 becomes a defensible use of the time.
- **A flagship is discovered broken on a real device.** Nothing here tested a real low-end Android;
  every G4 offline claim is 📄, not ✅. A single device session could reorder this whole table.
- **The founder's goal is momentum rather than proof** — a deliberate choice to launch on narrative
  strength and gather evidence afterwards. Legitimate, but it should be *recorded* as that.

---

## 10. Related

- [`community-release.md`](./community-release.md) §4 — the seven gates (owner of that rule)
- [`baselines/2026.1-community-release.md`](./baselines/2026.1-community-release.md) — the immutable
  reference snapshot this review measures against
- [`patterns/experiential-gates.md`](./patterns/experiential-gates.md) — why §7 cannot be automated
- [`decisions/DECISIONS.md`](./decisions/DECISIONS.md) — D-14 (curation), D-15 (editions), D-16 (Numeria)
- [`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md) — the evidence and honesty rules this review follows

> **Next step is a founder decision, not more analysis:** launch as planned · reduced scope · move
> the date. Only then is a `D-` entry written — recording what was *decided*, not what was intended.
