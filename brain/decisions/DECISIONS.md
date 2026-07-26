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

## D-13 · App runtimes must not borrow the name "TPH Core" — Early Literacy's engine set renamed to "TPH Learning Engines" (2026-07-03)

- **Context:** integrating Early Literacy surfaced a name collision. The app (built externally in
  Gemini) shipped a **frozen "TPH Core v1.0"** runtime — EventBus · Companion · Tracing · Vocabulary ·
  Discovery · Environment — which is a *different* thing from the canonical **TPH Core SDK**
  (Identity · Progress · Passport · …), itself still mid-extraction from ReadAfrica into `@tph/core`.
  Two engine sets, one name.
- **Options weighed:** (1) **rename** the app-local runtime, reserving "TPH Core" for the canonical
  SDK; (2) **fold** the app engines into `@tph/core`; (3) defer.
- **Decision:** **Option 1.** The app's runtime is renamed the **"TPH Learning Engines."** "TPH Core"
  now names exactly one thing — the canonical shared SDK. Option 2 was deferred: `@tph/core` is still
  mid-extraction, and folding a *frozen* app runtime into it is a larger, multi-app effort for later.
- **Why:** "one canonical source of truth" (the whole reason the Brain exists). Two "TPH Core"
  definitions would silently confuse every future agent. A rename is low-risk, reversible, and
  doesn't disturb the frozen app logic.
- **Applied:** early-literacy commit `49edf66` — TS symbols `TPHCore*` → `TPHLearning*`, UI badge,
  and the app-local architecture doc rebranded (filename kept for link stability); `tsc`/build clean.
- See [`architecture/04-early-literacy-integration.md`](./architecture/04-early-literacy-integration.md) §4.

## D-14 · The Community Release — curate the public site to six flagships (2026-07-10)

- **Before:** the People's Home site (`../index.html`) advertised **14 live app cards** across the 6
  pillars — everything that had shipped. Breadth, but a diffuse first impression, and it surfaced
  apps mid-transformation (Early Numeracy → Number Kingdom; Early Literacy still on its roadmap).
- **Change:** for the **release to the community**, present **one flagship per pillar** — a curated
  **six**: **Math Adventure RPG** (Foundations) · **African Discoveries** (Curiosity) · **Tech
  Makers** (Creation) · **Truth Seekers** (Thinking) · **Mzansi Money** (Money) · **Micro Founders**
  (Entrepreneurship). The other apps stay **listed, never hidden**, re-framed as a *purposeful
  roadmap* in three tiers: **🌟 Available Today** (the six) → **🏗 Currently Growing** (Early
  Numeracy, Early Literacy) → **🌱 Future Collection** (everything else). Each non-flagship card
  gets inspiring copy + a roadmap badge (NOW / BUILDING / NEXT), not a bare "Coming soon."
- **Why:** a focused, high-quality first impression beats an exhaustive list; the tiered roadmap
  says *"an expanding educational world,"* not *"unfinished software."* It is also **fully
  reversible** — status is one field per app; promotion is a one-field flip.
- **Why *not* Early Numeracy / Early Literacy in the six:** they are becoming their best selves
  (Number Kingdom; the literacy roadmap). Launching them before that polish would dilute them.
  They sit in *Currently Growing* until they meet the promotion criteria.
- **Governance:** this is net-new strategy (no prior "curated set" existed in the Brain). The
  operating model — flagship philosophy, **promotion/demotion criteria**, release cadence, review
  process — lives in the new **Community Release Constitution**
  [`../community-release.md`](../community-release.md). Note the standing tension with **D-01**
  (module-over-new-app / *don't proliferate*): curation is the *presentation-layer* companion to
  that build-layer discipline — fewer things shown, not fewer things built.
- **Long-term:** once Number Kingdom + Early Literacy reach polish, expand to a **Foundations
  Collection** (Early Literacy + Early Numeracy/Number Kingdom + Math Adventure RPG), with Math
  Adventure RPG as the premium maths adventure and Number Kingdom the ages-3–5 on-ramp.
- See [`../community-release.md`](../community-release.md); operational live-set in
  [`../../ECOSYSTEM.md`](../../ECOSYSTEM.md) / [`../../ROADMAP.md`](../../ROADMAP.md).

## D-15 · Math Adventure RPG = one product, two editions; the Stable Build Principle (2026-07-10)

- **Context:** `math-adventure-rpg` is a **single codebase** that already ships **both** the web PWA
  (Cloudflare Pages) and the Google Play app (Capacitor Android). The web version is now the
  ecosystem's first app slated for active enhancement, and those enhancements must never risk the
  shipped Play release.
- **Decision:** keep **one canonical codebase** (no fork). Define two **editions**:
  - **Google Play = the Stable / LTS edition.** Maintenance only — bug fixes, compliance,
    accessibility, security. No experimental UI, no beta systems.
  - **Web = the Community Edition** — the innovation lab (Living World, Story Theatre, advanced
    animation, large-screen/keyboard, community). Successful innovations **graduate** to a future
    Play release only after validation.
- **The Stable Build Principle:** the Play build is an LTS release; **no architectural or web work
  may change its gameplay, saves, progression, content, or UX without explicit founder approval.**
  Architecture evolves *behind* the release, not through it.
- **Mechanism (rejected the fork):** one repo, gated by **build profiles** —
  `play-store | community | development | demo` — superseding the bare `WEB_BUILD` flag (kept
  backward-compatible). Adopted **seam-first**: introduce `platform/` (profiles → PLATFORM detection
  → feature flags → adapters) and a `web/` feature area **now**, extract shared code into `core/`
  **incrementally later** (one subsystem at a time, by stability, freeze between). *"No file moves
  without a reason."* This is the same *clean-boundaries-first, then move behind them* discipline
  that shaped TPH Core (D-09) — a big-bang refactor was rejected as needless risk to the Play build.
- **Reusable model:** editions, **release channels** (`Development → Founder Preview → Community
  Edition → Stable (Play) → Expert-Approved`), **version semantics** (Stable = semver+versionCode;
  Community = `-preview`/Innovation line), and the **feature-graduation pipeline** are documented as
  a template for every future TPH app. This is the presentation/delivery companion to **D-03**
  (web-first) and **D-11** (Play is not our home) — Play stays, but only as a frozen LTS shell.
- **Open (founder's call):** whether to elevate the Stable Build Principle to a **DNA Principle #19**
  (`PROJECT_DNA.md` is append-only; adding a principle is a founder act — not done here).
- See [`../apps/math-adventure-release-policy.md`](../apps/math-adventure-release-policy.md),
  [`math-adventure-rpg.md`](../apps/math-adventure-rpg.md), and the repo's own `CLAUDE.md`.

## D-16 · Math Adventure RPG's world is "Numeria"; its story system stays app-local (2026-07-20)

- **Context:** the Community Edition seam (D-15) opened a chartered place for web-only innovation, and
  the first programme into it is a layered animation + storytelling capability (Living World ·
  micro-animations · concept animations · story episodes · Story Theatre). Two naming questions had to
  be settled *before* any of it was designed, because both are expensive to reverse.
- **Question 1 — the world's name.** Math Adventure RPG had **no named world**, which also left it
  absent from Principle 18's Welcome Moment examples. "The Kingdom of Numbers" was proposed.
- **Options weighed:** (1) a distinct name; (2) "The Kingdom of Numbers"; (3) defer naming.
- **Decision:** **Option 1 — the world is `Numeria`.** "The Kingdom of Numbers" was **rejected**: it is
  a near-anagram of **Number Kingdom**, which is founder-LOCKED and constitutional for
  **early-numeracy** — a *different app in the same pillar*, with which it would co-exist in the
  planned Foundations Collection. ~110 references across 11 files, plus two already-ratified
  anti-conflation clauses (one in the immutable Baseline 2026.1, one in code).
- **Why (the deeper reason — not just collision avoidance):** the two names encode a *progression*.
  Number Kingdom says *"numbers are friendly"* to a 3–6 year old. Numeria says *"mathematics is a
  world worth exploring"* to a learner of 3–17 who has grown. The existing regions — Academy of
  Numbers, Merchant's Guild, Dragon's Tower, Engineers' Citadel, Star Observatory — are not nursery
  locations; they imply a civilisation with professions, history and mastery. **The child has grown;
  the world has grown with them.** Direct precedent for the mechanism: **D-13** (rename the newcomer;
  reserve the name for exactly one thing).
- **Question 2 — a shared "TPH Story Engine".** The founder raised extending storytelling across every
  World-A app (Early Literacy, Space Explorer, Our World, Science Sprouts, African Discoveries…).
- **Decision:** **not yet.** Numeria's story system is built **app-local** under an app-local name
  (`src/web/numeria/`), and is extracted to `@tph/core` only when DNA Principle 11's **two-app
  trigger** fires — i.e. when a second app genuinely needs it.
- **Why:** `@tph/core`'s own stated rule is *"package what's proven, not what's imagined"*; the
  Passport was extracted only after proving out across three apps, and the README explicitly defers
  the household/progress engine until it has real consumers. Naming it "TPH Story Engine" while it
  lives inside one app would recreate the **D-13** error exactly. Letting the second app *contribute*
  to the contract beats letting the first app define it unilaterally.
- **Also recorded:** the blueprint's core doctrine — ***"Story supports learning; it never competes
  with it"*** — is a direct response to the 2026-06-17 "Expert Approved" rejection (text volume +
  disruptive sounds), made operable by the **Four-Purpose Test**: *every story element must teach,
  motivate, orient, or celebrate, or it does not belong.*
- **Applied:** [`../apps/numeria-roadmap.md`](../apps/numeria-roadmap.md) (blueprint, MA-0…MA-5) and
  [`../apps/numeria-constitution.md`](../apps/numeria-constitution.md) (MA-0). **Both DRAFT — MA-0 is
  not frozen, and freeze is a founder act.** No animation code written.
- **Resolved same day (2026-07-20), after review:**
  - **🌼 Meadow Gate** is the Phase 1 (ages 3–5) threshold province — the only region created rather
    than revealed. Chosen over *Foothills of Numeria* / *Numeria's Doorstep*: *"You don't begin by
    entering a fortress. You begin by walking through a meadow."*
  - **The Academy (13–17) is part of Numeria** — *"Numeria's highest institution of learning."*
    Younger learners travel through the world; older learners don't leave it, they **graduate within
    it**. Learning is continuous, not segmented, and the Academy of Numbers → Summit Academy pairing
    becomes narrative structure rather than coincidence.
  - **Companion ≠ Guide.** A player-renamed companion cannot carry canonical narration — the world
    can't name it. Companion = renameable, emotional support, reacts to gameplay. Guide = fixed
    identity, narrator, introduces provinces, appears in Story Theatre. Sparky 🐉 stays the learner's
    own and is not made to do both.
- **Open (founder's call — the last thing blocking the MA-0 freeze):** **the Guide's identity.**
  Deliberately not invented during drafting: once named, that character is part of Numeria for years,
  so it gets a dedicated design discussion. Constrained by ecosystem convention — each world gets its
  own guide, personalities are never borrowed, so Numeria may not use Pip.

---

## D-17 · The Portfolio Launch — 9 August 2026, launch as planned with conditions (2026-07-21)

- **Context:** MA-1 (Numeria Living World) shipped 2026-07-21 and was judged complete. Rather than
  continue to MA-2, the founder asked whether Numeria was even the right next investment:
  *"Before investing more effort in Numeria, it's worth checking whether any of the other launch
  projects have blockers that deserve attention first."*
- **A date existed only in conversation.** "9 August" appeared **nowhere** in the repository — not in
  `ROADMAP.md`, `PROJECT_TIMELINE.md`, `CURRENT_STATE.md`, `community-release.md` or any `apps/*.md`.
  It was one ended conversation away from being lost, which is the exact failure
  [`../UPDATE_PROTOCOL.md`](../UPDATE_PROTOCOL.md) exists to prevent.
- **Sequencing (founder's correction, and it matters):** the review was performed **first**, and this
  decision recorded **after**. The founder's reasoning: *"A decision log should record what you
  actually decided — not what you intended before reviewing the evidence."* Had the milestone been
  recorded first, this entry would have committed the log to a scope the review might have
  invalidated. **Evidence before ratification** — worth reusing.
- **What 9 August is (founder's definition, verbatim):** *"the planned public launch of The People's
  Home portfolio. It is not merely a website launch or a single-product release. It is a portfolio
  launch intended to present the initial collection of flagship educational experiences together as
  the first public expression of The People's Home."*
- **Why that raises the bar:** the Community Release (**D-14**) was a *presentation* decision —
  curation, explicitly reversible, *"status is one field per app."* A public portfolio launch is a
  different act: the first time these apps are shown to strangers as finished work. That is precisely
  what [`../community-release.md`](../community-release.md) §4's seven gates were written for.
- **Evidence:** [`../launch-readiness-2026-08-09.md`](../launch-readiness-2026-08-09.md) — scored
  against §4 **as it already exists** (cited, never restated — D-13, *one owner per rule*), with every
  mark carrying its provenance (✅ Verified / 📄 Claimed / ⏳ Open / ❓ Unknown).
- **The review's headline finding:** **the seven-gate bar had never been applied to the six apps that
  will be the public face.** The founding six were *designated* by D-14, and §4 was written in the
  same change to govern *future* promotions. Correct for a reversible curation; but the gates were
  never run against the current flagship set. **The gap is evidential, not technical** — all six
  type-check clean, all six URLs serve, nothing is broken.
- **Options weighed:** (1) launch as planned with conditions; (2) launch with reduced scope;
  (3) move the date.
- **Decision: Option 1 — launch as planned on 2026-08-09, with conditions.** Reduced scope was
  rejected on the review's reasoning: the risk is **evidential, not per-app**, so dropping a flagship
  would remove a pillar from the narrative without making the remaining five better evidenced.
- **The conditions (founder, 2026-07-21):**
  1. **Prioritise the real-child play-tests and record the evidence.**
  2. **Resolve the documentation inconsistencies** identified by the review.
  3. **Complete the required founder approvals** before launch.
  4. **Defer MA-2** until these portfolio-level conditions are addressed, or until new evidence
     changes the priority.
- **Why the play-tests come first — Numeria is not the bottleneck.** One un-run gate blocks more work
  than anything else in the project: **all nine Early Numeracy phase freezes simultaneously**, plus
  Early Literacy, African Discoveries and Space Explorer. Per
  [`../patterns/experiential-gates.md`](../patterns/experiential-gates.md) it is an **experiential
  gate** — satisfied by observation, not automatable, and closable **only by the founder**. Days of
  effort, portfolio-wide payoff.
- **Why MA-2 was deferred (ranked last of seven):** Math Adventure RPG is already the only flagship
  with automated tests and the only one with accessibility tooling. Investing the remaining days there
  would widen the gap between the best-documented app and the five that need attention. *This is a
  deferral on current evidence, not a judgement on MA-2's value.*
- **Also recorded — what the review verified rather than trusted:** three live apps are **missing from
  `../ECOSYSTEM.md`** ("the map of everything") — **Everyday Foundations** entirely, and **Mzansi
  Money (a flagship)** and **Our World** have no repo/URL/build row · **Tech Makers and Mzansi Money
  are PRIVATE**, which the registry implies otherwise · the six pillars are **named three different
  ways**, two of them on the same page · **five of six flagships have no automated tests at all.**
  Remediation is deliberately *not* part of this decision — a review that silently repairs what it
  finds stops being a review.
- **Explicitly unchanged:** nothing frozen (MA-0, Number Kingdom NK-4 and the Early Numeracy roadmap
  all remain unfrozen — freeze is a founder act) · [`../PROJECT_DNA.md`](../PROJECT_DNA.md) untouched ·
  the **Foundations Collection cannot form by 9 August** (Early Numeracy is blocked on a founder UI
  decision not yet made) · **iKhaya / World B remains out of scope** (2027).
- **What would reopen this:** the review states its own falsifiers — if the play-tests already happened
  informally and were merely unrecorded, R2 becomes a *recording* problem and the evidence sweep moves
  first; if a flagship is found broken on a real low-end Android (every offline claim is 📄, never ✅);
  or if the founder deliberately chooses momentum over proof — legitimate, but it should be recorded
  as that.

### D-17 · status updates (append-only; the decision above is unedited)

- **2026-07-23 — R1 (Android keystores) is CLOSED.** ✅ The signing keystores are backed up
  off-machine and integrity-verified. Work spanned the evening of 2026-07-22 into the early hours of
  2026-07-23. **The risk the review rated 🔴 Existential — the only one — no longer exists.**
  - **Recorded as portfolio state only.** The verification method, storage location and filenames are
    **deliberately not repeated here**; they live in the implementation repository, which stays their
    single source of truth. This layer records *that* a risk was retired, not *how*
    ([`../UPDATE_PROTOCOL.md`](../UPDATE_PROTOCOL.md) rule 6 — operational facts to the operational
    layer). Founder's framing: *"Institutional memory shouldn't only record risks; it should record
    when risks are retired."*
  - ⚠️ **Which condition this closes — two lists are easily confused.** It closes **condition 1 of the
    *review's* list** ([`../launch-readiness-2026-08-09.md`](../launch-readiness-2026-08-09.md) §8)
    and **priority #2 of §9**. It closes **none of D-17's four conditions above** — condition 1 there
    is the **real-child play-tests**, still open. A planning document for a sibling repository stated
    that R1 *was* "D-17's condition 1"; that is incorrect and is recorded here so the error is not
    re-derived from it later.
  - **§6's R1 row is deliberately left as written.** The review records what was found before the
    decision; its own banner forbids editing findings to match later outcomes. Closure is recorded
    here and in `CURRENT_STATE.md`, not by rewriting the finding.
  - **Remaining open:** D-17 conditions 1–3 (play-tests · documentation sweep · founder approvals);
    condition 4 (defer MA-2) holds. **R2 — no app has been observed with a real child — is now the
    highest-severity open risk in the register.**

---

## D-18 · The platform's software layer is "Institutional **Services**", not "capabilities" — reserve *capability* for human development (2026-07-24)

- **Context:** the `institutional-platform-strategy.md` DRAFT (added 2026-07-24) used **"capability"**
  for a *software service function* (`getVision()`, `getLaunchStatus()`). But
  [`../architecture/01-capability-architecture.md`](../architecture/01-capability-architecture.md)
  already owns **"capability" = what a *learner gains*** (the eight categories — the real unit of
  educational value). Same word, two meanings, same folder — flagged on entry as reconciliation #1.
- **Decision:** the software layer is renamed **Institutional Services** throughout the strategy.
  **"Capability" is reserved exclusively for human development / learning.** *Institutional services
  describe what the institution **does**; capabilities describe what a person **becomes**.*
  - *"Interfaces consume capabilities"* → *"Interfaces consume **institutional services**."*
  - *"Expose capabilities, not storage"* → *"Expose **institutional services**, not storage."*
  - *"Institutional Capability Layer"* → *"Institutional Services Layer."* ("Business capability" →
    "business logic", for the same reason.)
- **Why not "capability" for the software sense:** technically defensible, but the word already has an
  established educational meaning central to World A. Overloading it inside the same architecture is
  the collision this project has ruled on twice before — **Number Kingdom vs Numeria (D-16)** and the
  **"TPH Core" → "TPH Learning Engines" rename (D-13)**. Same mechanism: when a name collides with a
  load-bearing one, rename the newcomer.
- **The layering it exposes** (founder observation, recorded for the eventual implementation ADRs):
  **Institutional Services** (what the institution does) sit *above* **TPH Core shared services** (how
  multiple apps implement their responsibilities) sit above infrastructure. Two distinct layers, not
  one.
- **Applied 2026-07-24.** The strategy DRAFT is revised to **v0.2**; reconciliation #1 is **RESOLVED**.
  The document remains DRAFT overall — its §13 still lists the decisions required before implementation.

## D-19 · The Institutional Platform governs World A but is never a *runtime dependency* of it (2026-07-24)

- **Context:** reconciliation #2 flagged on the strategy DRAFT's entry. Its
  auth/permissions/multi-tenant/API machinery describes the **institutional meta-layer**; read
  carelessly, §11's *"the institutional operating platform for the entire ecosystem"* reads as
  putting a server under the offline learning apps — contradicting Product Rules #3–#4 (#FreeForever ·
  offline · no accounts · no server).
- **Decision — a constitutional boundary:** **The Institutional Platform may *describe*, *distribute*,
  and *recommend* World A. It must never become a *runtime dependency* of a World A educational
  experience.** World A stays sovereign: learning, progression, privacy, local storage, offline
  operation, the child's experience — all owned by the app, none requiring the platform to be
  reachable.
  - **Institutional Platform owns:** governance · documentation · planning · public information ·
    repository health · release management · AI interfaces · websites · authenticated services.
  - **World A owns:** learning · progression · privacy · local storage · offline operation · the
    child experience.
- **Why it's a rule and not an implication:** it protects the single strongest invariant in the
  project. An implication can be eroded one convenient feature at a time; a stated boundary cannot be
  crossed without visibly overturning **D-19**. Accounts/servers remain a **World B / iKhaya** concern
  ([`../architecture/02-world-a-world-b-dna.md`](../architecture/02-world-a-world-b-dna.md)).
- **Scope:** this is the platform-vs-World-A runtime boundary specifically. It does not touch the
  World A / World B split itself (Canon 02 owns that) — it *cites* it.
- **Status:** reconciliation #2 **RESOLVED**. The strategy DRAFT still does not leave DRAFT — D-18 and
  D-19 clear the two entry flags, not the eight implementation decisions in its §13.

---

## D-20 · The Educational Record Standard — adopted as World A canon (Canon 06) (2026-07-24)

- **Origin — a small question that became constitutional.** It began as a play-test note on African
  Discoveries — *"why is this a one-minute read?"* — and surfaced a hidden assumption: the app was
  optimising for **completion** (a UX reflex) in an **education institution**, which optimises for
  **understanding.** The founder rejected the premise that a shallow layer must precede a deep one.
- **What was adopted:** [`../architecture/06-educational-record-standard.md`](../architecture/06-educational-record-standard.md)
  — the standard that answers *"when may an educational record be declared complete?"* Its spine:
  **understanding over completion** (no reading-time target); a four-criterion **Definition of
  Completeness**; four editorial **bands** (Foundation · Context · Connections · Exploration) as author
  requirements, not screens; **Negative Requirements** (a description/image/achievements/AI prose/word
  count are inputs, not evidence — the guard against "looks complete"); a required **Misconceptions &
  Clarifications** element; every claim **sourced** (carrying African Discoveries' Phase 0 discipline).
- **The three founder rulings (A/B/C):**
  - **A — Adopt.** Not as an application document; as a **World A constitutional standard.** The rules
    are subject-independent: they hold for Imhotep or photosynthesis, Mali or fractions, Python or
    astronomy.
  - **B — Promote to the Brain** as the canonical **Educational Record Standard** (renamed from
    "Editorial Standard" — it governs the whole record, not merely the writing), owned under World A.
    Constitutional sentence placed at the top: *"No educational record may claim completeness unless it
    satisfies this standard."*
  - **C — African Discoveries retains a delegated reference,** not a second copy. Ownership is explicitly
    the Brain's; `african-discoveries/docs/editorial-standard.md` points here. **A reference, not a
    duplicate — one owner, so the two cannot drift** (D-13).
- **The governance rule it carries:** *the standard defines the model; the model must evolve to satisfy
  the standard, never the reverse.* An app whose data model cannot hold Bands 1–2 must grow the model,
  not narrow the bar.
- **Adoption ≠ implementation (deliberate separation).** Adoption fixes *what complete means*, across
  World A, and is founder-approval-gated only. **Implementation is per-app** and gated by scope (e.g.
  African Discoveries' 9–17 vs fund-3–8 call), the content-model change, and the journey-axis decision.
  This makes the philosophy canonical **without** committing to rewrite any content immediately.
- **Not done here:** no record is yet authored to the standard; the African Discoveries content model is
  unchanged; the "journey axis" (the dead `LEARNING_JOURNEY` vs a Discover→…→Teach path) remains one
  vocabulary short of a decision. **Completeness principle as a one-line product rule in Canon 03** is a
  cross-reference (below), not a restatement — the standard owns it.

---

## D-21 · From *inventing* the institution to *operating* it — industrialise the workflow, never lower the bar (2026-07-26)

- **The mode shift.** This session invented the educational institution: Canon 06, the Educational Record
  Schema, the authoring playbook, the review gates, and **two validation records of different kinds**
  (Imhotep = person, Great Zimbabwe = civilisation) that proved the system works. Those were the unknowns;
  they are no longer unknown. The founder's ruling: **inventing is over; operating begins.** Inventing is
  deliberately slow because mistakes become constitutional; operating should be faster because the
  constitution already exists. The mindset changes from *"can Canon 06 do this?"* to **"apply Canon 06."**
- **Two ways to accelerate — only one is allowed.** ❌ *Bad acceleration:* produce many records fast by
  relaxing the standard — this destroys everything built. ✅ *Good acceleration:* keep the standard exactly
  where it is and **industrialise the workflow.** The bar does not move; the throughput does.
- **The pipeline model.** Records move through queues (Research → Authoring → Self-review → Historian review
  → Teacher review), so **many records sit at different stages simultaneously** instead of one-at-a-time.
  Average time per record also falls honestly: Imhotep and Great Zimbabwe were among the *hardest* possible
  (deep historiographical misconceptions); an endemic animal, a national park, a geological feature or an
  instrument need careful sourcing but less controversy-resolution. Lower average difficulty, **same bar.**
- **Two independent tracks, non-blocking.** **Track A — Library Growth** (author the catalogue to Canon 06).
  **Track B — Launch Readiness** (UI polish, performance, accessibility, testing, release docs, independent
  reviews). Neither blocks the other. Rationale the founder stressed: **four apps still need preparation**;
  if African Discoveries consumes all time, the portfolio suffers. Standards exist precisely to stop
  reinventing the process — the expensive architectural cost is paid, now benefit from it.
- **⚠️ The honest constraint the pipeline diagram hides — the ceiling is human, not throughput.** The
  Authoring/Self-review queues are AI-fillable and can run fast. The **Historian-review and Teacher-review
  queues require independent humans who do not yet exist**, and source-URL verification likewise. So
  industrialising authoring produces an **authored-but-unverified backlog** — records at `verified: false`,
  correct-by-construction but **not certifiable, and not shippable to a child on authoring alone.** This is
  acceptable *by design* only because we name it: raising *records authored* must never be mistaken for
  raising *records a child can trust.* Sourcing the independent reviewers is the real rate-limiter on
  "finish the catalogue," and it is a Track-B / founder task, not an authoring one. (This is the
  proxy-substitution guard applied to throughput: *authored* is a proxy for *trustworthy*; the gap between
  them is exactly the two human gates.)
- **Programme.** Continue the **validation-record archetypes** (schema §5.1: person ✅ · civilisation ✅ ·
  scientific innovation · animal/biodiversity · living figure · natural wonder · cultural tradition) to
  prove subject-agnosticism across the domain; **then** switch to systematic library authoring. Operating
  mode starts *now*, within the archetype programme.
- **Not changed:** Canon 06, the schema, the playbook, and the gates are untouched — accelerating means
  using them faster, not editing them. All authored records remain `verified: false` until the two human
  gates close.

---

> **Open decisions (not yet resolved):**
> - The **#FreeForever funding fork** for iKhaya (the one place free-forever needs an answer).
> - Whether **Digital Creator Academy** ever becomes a real app (parked).
> - The eventual relationship between the various Golden Hand framings (offline prototype vs any
>   server-backed direction) — see [`apps/the-golden-hand.md`](./apps/the-golden-hand.md).
