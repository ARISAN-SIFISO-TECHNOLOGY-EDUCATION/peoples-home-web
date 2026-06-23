# THE PEOPLE'S HOME — Decision Log (the *why*)

> The reasoning behind the ecosystem. Code lives in git; this is the institutional memory that
> usually doesn't. **Append, don't rewrite** — each entry is a point-in-time decision.
> Last updated: 2026-06-21.

See also: [`BLUEPRINT.md`](./BLUEPRINT.md) · [`ECOSYSTEM.md`](./ECOSYSTEM.md) · [`ROADMAP.md`](./ROADMAP.md).

---

## Non-negotiable product rules
- **Ages, never grades.** Present everything by AGE. CAPS/IGCSE alignment is internal only —
  grade labels must never render in UI. Smoke test: `/Grade|GR[0-9]/` count must be **0**.
- **Every learning app's age ceiling reaches 17** *(2026-06-21)*. Science Sprouts (3–12) violates
  this → must extend to 13–17.
- **#FreeForever** — learning apps carry no ads, no IAP, no paywalls, no accounts. Forever.
  (The one exception is iKhaya's backend cost — flagged below.)
- **Offline · no-data** — learning apps require no internet and collect no data ("No data
  collected"). Anything needing network/PII is World B (iKhaya), not a learning app.
- **SA-first** — local contexts, names, Rand, languages. isiZulu shipped as **DRAFT** until a
  December native-speaker review.

## Architecture
- **Capability architecture (v2 blueprint, 2026-06-21).** The People's Home is a *capability
  system*, not 40 apps. Classify every item: **Capability → Implementation (App/Module/Service) →
  DNA**. Collapsed ~40 apps → ≈10 deep offline apps + iKhaya + TPH Core.
- **The DNA split (World A vs World B).** *World A* = offline learning (no login/server/tracking).
  *World B* = opportunity infrastructure (accounts/PII/POPIA/moderation/server) = **iKhaya**. They
  never mix. The Money & Empowerment pillars *span both*: an offline app teaches, then hands off to
  iKhaya — that handoff is "the bridge."
- **Module-over-new-app discipline.** Prefer a module inside an existing app over a new repo. Only
  spin a new product when the capability *and* DNA genuinely warrant it. (This is what stops the
  blueprint drifting back into 40 products.) E.g. Truth Seekers = ONE app, six modules.
- **TPH Core SDK** = the shared services (identity/progress/rewards/lore/offline engine/dashboards),
  currently embedded in ReadAfrica; extraction to a shared package is the platform track.

## Delivery
- **Web-first pivot (2026-06-12).** Stopped prioritising Google Play (slow review, morale). Ship
  learning apps as offline, installable **Cloudflare Pages PWAs** + a card on this site. The apps
  were already React+Vite, so PWA conversion is cheap. Azure-for-Startups credits are a candidate
  answer to iKhaya's AI/backend funding.
- **Science Sprouts = the LAST app on Google Play (2026-06-21).** SS was already in the Play
  pipeline and was *granted production access*, so it's being finished out (promote the tested
  versionCode 2 build → production, staged rollout). **After SS, the Play release machine is
  retired** — every other app (Truth Seekers onward) ships **web-first PWA only**, no Play track.
  This is the clean tail of the wind-down, not a return to Play.
- **PWA conventions:** `vite-plugin-pwa` (Vite apps) / Workbox (CRA); **unique manifest `id`** per
  app (sibling-collision rule); SW registered web-only (gate native via Capacitor when present).
- **Cloudflare/lockfile:** gitignore `package-lock.json` where `npm ci` is brittle (Vite 8 `@emnapi`;
  CRA dep drift) so Pages uses lenient `npm install`. CRA needs `CI=false`.
- **Narration:** use Math Adventure's robust `useNarration` (wait for `voiceschanged`, pin an
  installed voice, isiZulu→English speech fallback). Never ship the naive `speak()` (Science Sprouts
  shipped silent that way). Device-audio is a release gate.

## App-boundary calls
- **SIFISO stays separate** from Tech Makers *(2026-06-20)* — different audience/depth; merging would
  bolt Pyodide+Monaco onto Tech Makers' light bundle. SIFISO Learn = its own app (Python/Web/AI tracks).
- **Renamed "SIFISO — Learn Python" → "SIFISO — The Golden Hand"** *(2026-06-23)* — the app was never
  just a Python course; it's a **five-app-in-one system** (a journey: Golden Learn → Golden AI →
  Golden Quiz → Golden Startup → Golden Commons) — effectively the original prototype of The People's
  Home ("one shell, five apps"). The in-app title already said "The Golden Hand"; this propagates the
  real name across the ecosystem (card, ECOSYSTEM/ROADMAP/BLUEPRINT, manifest, README). **Repo slug
  `sifiso-learn-python` + the `.pages.dev` URL are kept** (renaming them would break the Cloudflare
  connection + live link — display name only). *Golden Startup carries the user's "1 Million Startups
  in 12 Months" campaign — the same vision that became Micro Founders (Pillar 05).*
- **Micro Founders = Venture Journey, not age-muscles** *(2026-06-23)* — the Pillar-05 app's spine is a
  **5-stage sequence** (Spot → Cost → Sell → Build → Pitch, sequential unlock) carrying one persistent
  "My Venture", **not** Truth Seekers' parallel age-muscle shape. Founding is *directional* (you can't
  cost what you haven't spotted); reasoning skills are *independent* (any order). Age survives as a
  within-stage difficulty dial, not the top axis. Full brief: [`MICRO_FOUNDERS.md`](./MICRO_FOUNDERS.md).
- **Micro Founders vs Mzansi Money** *(2026-06-23)* — Micro Founders = *make* money via a venture
  (entrepreneurship); Mzansi Money = *manage* your own money (financial literacy). Distinct apps.
- **iKhaya = the Opportunity layer**, absorbs the 6 navigators as in-app sections (not separate apps).
  Server-backed + PII = Play "data IS collected" + POPIA. **The #FreeForever funding fork** — its
  backend cost is the one place "free forever" needs a sustainability answer; resolve before 2027.

## Critical-information risk *(2026-06-21)*
The code is safe in GitHub. The **least-protected, most-critical** information is:
1. **The strategy brain** — was only in Claude's machine-local memory + the plan file. → being
   migrated into this versioned doc set (BLUEPRINT/ECOSYSTEM/ROADMAP/DECISIONS) so it survives the
   machine.
2. **Android signing keystores** (`.jks` + `keystore.properties`) — gitignored, **local-only,
   irreplaceable.** A prior **upload-key rotation incident** already proved the pain. **ACTION
   (outstanding): keep an encrypted, off-machine backup** (password-manager vault / encrypted cloud).
   Never in git, but must exist in more than one place.
3. **Account access** (GitHub org, Cloudflare, Play Console) — recoverable only with the logins.

## History / notable incidents
- **Keystore rotation (done, ~2026-06-09).** Math Adventure upload key rotated to `upload-new.jks`
  (alias `upload`); `keystore.properties` switched; v2.0/code5 AAB signed with it.
- **Play target-audience** declared 5&under → 16–17 (2026-06-09); must match the app's 3–17 content.
- **"Expert Approved" badge rejected** (Math Adventure, 2026-06-17) — too much text for young ages +
  disruptive sounds. Fix carries over to the PWA.
