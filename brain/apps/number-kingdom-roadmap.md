# 🌈 Number Kingdom — Experience Roadmap (Early Numeracy · World A) — 🔒 FROZEN

> **Status: ✅ FROZEN — founder-ratified 2026-07-04.** Canonical roadmap for the Early Numeracy World-A
> app. The naming architecture (§0) and NK-0 Kingdom Constitution are **constitutional and immutable** —
> they may change only through a **formal roadmap revision**.
> This is the experience-layer roadmap that elevates **Early Numeracy** from a collection of
> activities into a **living world** the child inhabits. It does **not** replace the educational
> roadmap — [`early-numeracy-roadmap.md`](./early-numeracy-roadmap.md) (Phases 1–10) is **build-complete**
> and its 16 no-fail modules stay intact. Number Kingdom is the **shell/world layer built over them.**
>
> **Governance (founder's model): Blueprint → Freeze → Build.** Each NK milestone is frozen before the
> next begins. **Freeze is a founder act** — the next AI never self-declares a freeze.
>
> **Progress:** NK-0 ✅ FROZEN (2026-07-04) · **NK-1 World Map ✅ FROZEN (founder-ratified 2026-07-04,
> `f75d69a`)** · **NK-2 Living Kingdom ✅ FROZEN (founder-ratified 2026-07-05, `5ee188b`)** ·
> **NK-3 Math Adventure Journal ✅ FROZEN (founder-ratified 2026-07-05, `3ada8bc`)** ·
> **NK-4 Companion (Pip) ✅ BUILT & LIVE (`e22602b`), awaiting founder Freeze** · NK-5…NK-6 not started.

---

## 0. Naming architecture (LOCKED by founder 2026-07-04)

> **Don't rename the app. Rename the world.**

| Field | Value |
|---|---|
| **Product name** (adults, Play Store, People's Home, repo, URL) | **Early Numeracy** |
| **Experience name** (child-facing world) | **🌈 Number Kingdom** |
| **Primary world** | Number Kingdom |
| **Child-facing brand** | "Welcome to Number Kingdom!" |

Parents/teachers/store/registry see **Early Numeracy** — clarity for adults. The child opens the app and
never needs to see that name again; they **enter Number Kingdom**. This mirrors the ecosystem pattern:

| Product | Child's world |
|---|---|
| Early Literacy | Letter Garden → Word Meadow |
| **Early Numeracy** | **Number Kingdom** |
| Space Explorer | Spaceport → Solar System |
| Our World | My Home → My Planet |

**No churn:** repository (`ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-numeracy`), package name, URL
(`early-numeracy.pages.dev`), Play identity, People's Home registry entry, and docs **all stay the same.**
Only the in-app UI changes.

---

## 1. The core principle — wrap, don't rewrite

**The educational modules are the hard part, and they are done** (Phases 2–10 built, live, verified over
~4M simulated rounds). Number Kingdom changes only what *wraps* them:

- "Home / choose activity / play" → **arrive in a world / walk to a place / discover**.
- Module cards (rectangles) → **illustrated locations** on a world map.
- "42%" → **a world that visibly grows**.
- Generic praise → **Pip, the Kingdom Guide**.

Educational logic is **frozen and untouched**. Every module keeps its no-fail mechanics, its narration,
its progress store, its StrictMode-safe internals. This is why the transformation is high-emotional-impact
but contained blast radius.

---

## 2. Region map & module placement

One screen. One tap. No scrolling maze, no free-roam RPG (see navigation constraints §4). Seven regions,
every existing module has a home — nothing orphaned, nothing new invented to fill the map:

| Region | Houses these existing modules | Feeling |
|---|---|---|
| 🏡 **Number Village** (hub) | `numbers-everywhere` · `time-and-day` | Home base; real-world & daily life |
| 🌳 **Counting Forest** | `counting-garden` · `which-is-more` · `number-hunt` · `number-match` | Count animals, fruit, leaves, birds |
| 🌊 **Shape Lake** | `shapes-world` | Fish for shapes |
| 🏔 **Pattern Mountain** | `pattern-maker` · `number-shapes` | Repair the magical trail up |
| 🚂 **Number Railway** | `make-five` · `make-ten` · `addition-adventure` · `taking-away` | Ten-frame = carriage; passengers board/leave |
| 🎪 **Puzzle Carnival** | `measurement` · `money` · `data-sorting` | Ring-toss, balance, sorting games |
| 🏰 **Number Castle** | *(mixed celebration — samples everything)* | Festival, not a boss |

**Number Railway is the strongest theme** — a ten-frame literally *is* a carriage with ten seats;
addition = passengers boarding, subtraction = passengers leaving. Metaphor only; no educational rewrite.

---

## 3. Milestones (build incrementally; freeze each before the next)

### NK-0 — Kingdom Constitution ⚖️ — ✅ FROZEN (founder-ratified 2026-07-04)
**This is the immutable foundation for every future implementation decision.** Verbatim ratification:

**Mission.** Build children's confidence in mathematical thinking through exploration, play, observation,
and joyful discovery. Children should never feel like they are completing mathematics exercises. They
should feel like they are **helping a magical kingdom grow.**

**Educational Principles (constitutional):** Offline First · Audio First · Confidence Before Correction ·
No Failure States · No Timers · Child-Led Exploration · Learning Through Play · Ages Before Grades ·
Environment as Reward · Discovery Before Memorisation · Privacy by Design · **#FreeForever**.

**Experience Principles:** The child never navigates a dashboard — the child explores a living world. The
child never selects an exercise — the child visits a place. The child never earns abstract points — the
kingdom visibly grows.

**Navigation Principles:** One-screen world map · one-tap navigation · no free-roam RPG mechanics · no
possibility of getting lost · **"Continue Journey" always returns the child to the last activity.**

**Platform Principles:** TPH Core v1.0 is frozen. Number Kingdom **consumes** the platform; it does not
modify it. All integration occurs through public contracts and the Event Bus. (D-13: adopting the shared
TPH Learning Engines later must slot in without a rebuild.)

**World Structure (constitutional regions):** 🏡 Number Village · 🌳 Counting Forest · 🌊 Shape Lake ·
🏔 Pattern Mountain · 🚂 Number Railway · 🎪 Puzzle Carnival · 🏰 Number Castle. Future educational
content must belong within this world unless a **formal roadmap revision** introduces a new region.

**Companion — 🐿 Pip.** Pip is the Kingdom Guide, not another teacher. Pip encourages curiosity and
confidence · never judges · never uses negative language · **never replaces Ollie, Fifi, or Lulu.**

**Daily Life Layer.** The kingdom is alive; environmental changes communicate progress (flowers bloom ·
butterflies arrive · birds sing · windmills turn · rivers flow · lanterns glow at night · gentle rain
makes puddles). Atmospheric, not instructional — they reinforce a sense of belonging.

**Wrap, Don't Rewrite.** The educational logic of the existing sixteen modules is preserved. Work focuses
on presentation · navigation · environmental storytelling · emotional engagement. **Rewriting proven
educational mechanics requires a separate architectural review.**

**Definition of Success.** Early Numeracy is complete when children no longer perceive it as "doing
maths" — instead they experience returning to **Number Kingdom**, where mathematics naturally emerges
through exploration, play, and helping the kingdom flourish.

### NK-1 — World Map 🗺️ — ✅ FROZEN (founder-ratified 2026-07-04, `f75d69a`)
**Frozen after a 10-point founder experience review** (First Impression · Wonder · Parent Clarity ·
One-Hand Nav · Visual Balance · Region Recognition · Continue Journey · Pip's Welcome · Atmosphere ·
Memory Test — all PASS). Frozen surface: **Welcome Moment · one-screen world map · seven constitutional
regions · one-tap navigation · Continue Journey flow · parent-control placement · child-lock preservation
· animated storybook SVG approach · atmosphere layer · PWA compatibility · accessibility behaviour.**
Future work **enriches** this foundation; it does not replace it.
The home screen becomes the Kingdom. A single-screen illustrated map with the seven landmarks, a sky, a
child character, and **"⭐ Continue Journey"** (returns to the last region). Tapping a landmark walks the
character there and opens that **region screen** — a themed sub-screen listing its modules as illustrated
"places" ("🌳 Counting Forest — Animals are waiting!"). Everything one tap deep.
**Delivered:** `constants/regions.ts` (7 regions + positions + module→region map, all 16 modules placed) ·
`components/WorldMap.tsx` (sky, winding rainbow path, 7 tappable landmarks, a wanderer 🧒 that walks to
the tapped place, Continue Journey, parent controls + child-lock preserved, speaks a kingdom welcome) ·
`components/RegionScreen.tsx` (themed region screen; Village hub keeps the Today nudge + growing kingdom
scene; Castle framed as a festival being prepared, **not** a broken stub) · `App.tsx` rewired to
worldmap → region → module (Back from a module returns to its region; Back from a region returns to the
map) · `SessionState` gained `currentRegion` + `lastModuleId` (default-merge safe). Old `HomeScreen.tsx`
is now unused (left in place; removable during NK-5 cleanup). tsc 0 · clean build (entry
`index-CzNKB-Nx.js`) · PWA SW-registration fix (`7634696`) intact · deploy verified.
**Founder pre-freeze review (in progress):** founder is NOT freezing on technical completion alone — NK-1
is the emotional front door, so it gets a dedicated 10-point experience review (First Impression · Wonder
· Parent Clarity · One-Hand Nav · Visual Balance · Region Recognition · Continue Journey · Pip's Welcome ·
Atmosphere · Memory Test). One requested addition, now **built** (`f75d69a`, live):
- **Kingdom Welcome Moment** (`components/WelcomeMoment.tsx`) — shown **once ever** (localStorage
  `nk-welcomed-v1`): sun · rainbow arcs in · Pip 🐿 runs in with sparkles · "Welcome to Number Kingdom!
  The whole kingdom is waiting to explore with you!" · warm "⭐ Let's Begin". The Begin tap is the first
  audio gesture → speaks the welcome + unlocks speech; overlay fades, map revealed. Returning children get
  the spoken welcome-back instead.
- **Atmosphere** — added a floating butterfly + gentle lake shimmer; `index.css` keyframes nk-rainbow-in /
  nk-run-in / nk-twinkle (under the existing reduced-motion guard).
- **Scope note:** Pip appears here as a welcome **cameo only**; the full companion system stays **NK-4**.
**→ Freeze NK-1** — *awaiting the founder's experience-review verdict; then Freeze before NK-2.*

### NK-2 — Living Kingdom 🌱 *(includes the Daily Life Layer)* — ✅ FROZEN (founder-ratified 2026-07-05, `5ee188b`)
**Frozen surface:** seeds-driven visible growth (flowers/trees/butterflies/birds/bees/nest/rainbow at
thresholds) · the river appearing + flowing from 6 seeds · the Daily Life Layer (time-of-day sky + light,
sun→moon+stars+🏮 lanterns at night, per-calendar-day stable weather ≈68/22/9 clear/cloudy/rain) · the
"Your kingdom is growing!" acknowledgement on returning from play · the deterministic, never-flickering,
reduced-motion-guarded animation approach. Future work enriches this; it does not replace it.

Progress becomes *visible world change*, absorbing the current Math Village. Built on the existing progress
store (`lib/progress.ts` `seeds`/rounds). As the child plays: flowers bloom → butterflies arrive → birds
return → windmills spin → the river flows → the bridge is repaired → the castle is restored. **No numbers,
only change.**
- **Daily Life Layer** (founder addition) — the world feels *lived in*, independent of learning:
  morning the village wakes & birds appear; evening lanterns glow; rain brings puddles and hides
  butterflies; wind moves the leaves. Purely ambient/cosmetic (real device clock, no module logic).
  Reuses the visual language of `time-and-day` without touching the module. **Freeze.**

**✅ BUILT & LIVE (2026-07-04, `5ee188b`); awaiting founder Freeze.** Delivered — *visible life, not new
gameplay* (founder brief: "the kingdom is becoming more beautiful because of your curiosity"):
- `lib/kingdom.ts` — growth driven purely by `seeds` (one per completed round). Deterministic decor slots
  with thresholds: flowers bloom, trees grow, butterflies/birds/bees arrive, a nest is built, and a
  rainbow crowns the kingdom at 20 seeds. A **river** appears and flows from 6 seeds. Persisted
  growth-stage (`nk-kingdom-stage-v1`) so growth is noticed only when real.
- `lib/daylife.ts` — **Daily Life Layer**: time of day sets the sky + light (morning/day/evening/night),
  the sun becomes a moon with stars + 🏮 lanterns at night; **weather is stable per calendar day** (≈68%
  clear / 22% cloudy / 9% gentle rain → fuller river + a puddle). Deterministic, never flickers.
- `WorldMap` renders the living decor + river + day/night sky + celestial + lanterns + weather, and a
  gentle **"Your kingdom is growing!"** sparkle + spoken line when the child returns from play and the
  kingdom has grown. All motion under the existing `prefers-reduced-motion` guard.
- Modules untouched. tsc 0 · clean build (entry `index-lRggn5aE.js`) · SW fix intact · invariants checked
  (phases cover 24h, weather stable per-day, growth monotonic 0→15) · deploy verified.
- **→ Freeze NK-2** — *founder review, then Freeze before NK-3 (Math Adventure Journal).*

### NK-3 — Math Adventure Journal 📖 — ✅ FROZEN (founder-ratified 2026-07-05, `3ada8bc`)
**Frozen surface:** the derived journey memory (discoveries · places explored · favourite game · games
played · 12 stamps) · collection-not-assessment (no score/percent/fail) · the wrap-don't-rewrite
derivation from the progress store (modules never instrumented) · the append-only seen-achievements store
(`en-journal-v1`) + "New!" badging · the WorldMap-owned overlay (📖 bottom-left, no new route) · the warm
empty state. Future work enriches; it does not replace.
The child collects the memory of their journey: discoveries · places explored · favourite game · games
played · achievements (stamps) · a journey map. Collection, **not** assessment (NK-0) — no scores, no
percentages, no failure. (There was no prior "My Number Book" component to rename; built fresh.)

**Wrap, don't rewrite (crucial):** the Journal is **derived entirely from the existing progress store**
(`lib/progress.ts` — one seed per completed round). The 16 frozen educational modules are **not
instrumented or touched**; every "discovery" is a round the child already completed. The only persisted
Journal state is a tiny **append-only** set of achievement ids already *seen* (`en-journal-v1`,
schema-drift-safe like `progress.ts`) so a freshly earned stamp can be gently badged **"New!"**.

**Delivered:**
- `lib/journal.ts` — pure `buildJournal(progress)`: total discoveries, games (favourite = most-played
  first), per-region exploration facts, and **12 stamps** (region-anchored: Villager/Forest Friend/Shape
  Fisher/Mountain Climber/Train Driver/Carnival Star; milestones: First Steps/Explorer/Ten·Fifty·Hundred
  Discoveries/Kingdom Wanderer). Append-only seen-store (`readSeenAchievements`/`markAchievementsSeen`).
- `components/Journal.tsx` — a **WorldMap-owned overlay** (like the Welcome Moment): no new route, so
  App's NK-1 navigation is untouched. Summary tiles · favourite game · journey map (7 places, explored
  glow / faint-if-not) · games played · stamps grid (earned bright + **New!**, unearned faint silhouettes
  — a collection to look forward to, never a failure). Audio-first (Pip line on open; taps speak). Warm
  empty state ("Your journal is waiting for your first adventure!"), never a blank.
- `WorldMap` — an always-visible 📖 button (bottom-left, one tap from the map). `narration`:
  `kingdom.journal` / `kingdom.journalEmpty`.
- Modules untouched. tsc 0 · clean build (entry `index-CYE9Sc0q.js`) · SW fix intact · journal invariants
  checked (200k randomized runs: monotonic earning, favourite = max, region-explored iff played, wanderer
  needs all six playable regions, `discoveries === seeds`) · deploy verified live.
- **→ Freeze NK-3** — *founder review, then Freeze before NK-4 (Companion Integration — Pip).*

### NK-4 — Companion Integration 🐿 — ✅ BUILT & LIVE (2026-07-05, `e22602b`); awaiting founder Freeze
Introduce 🐿 **Pip, the Kingdom Guide.** Pip is not another teacher; Pip invites discovery — encourages
curiosity and confidence, never judges, never uses negative language, never says *"Let's do maths."*
Scripted line pools (no runtime AI — true to #FreeForever). Examples: *"Let's see what's hiding in the
forest!"* · *"I wonder what is happening in the forest today."*

**Important reconciliation with NK-0:** Early Numeracy has **no 🦉 Ollie / 🦊 Fifi / 🐦 Lulu** — those
live in *other* TPH apps. This app's in-module teaching voice is **anonymous** (`useInstruction` +
`NARRATION_EN.modules[*]`). So Pip does not "join a trio" here and there is no one to replace; instead Pip
lives **entirely on the world / guide layer** (the shell we own): the world map, region invitations,
kingdom-growth moments, and the journal. Pip **never enters the frozen modules** as a second teacher —
which also honours NK-0's "Pip invites discovery; he is not another teacher." Fully wrap-don't-rewrite:
no module or educational logic touched. (The original blueprint said "woven into region entry / correct /
level-up"; correct/level-up happen inside frozen modules, so — per the deeper NK-0 principle — Pip stays on
the navigation/guide layer. If the founder wants Pip flavour inside modules too, that is a deliberate,
separately-reviewed extension.)

**Delivered:**
- `constants/pip.ts` — Pip identity (`PIP` 🐿️) + **scripted pools**: welcome · welcomeBack · mapTip · grew
  · journal, and **per-region invitation pools for all 7 regions**. `pipLine()` picks at random, avoiding
  immediate repeats. Constitution-guarded: no negative language / no "maths" in any spoken line.
- `components/Pip.tsx` — a **visible companion** on the world map with a speech bubble; his words show in
  **visual mode** too (not audio-only). Tap Pip → a fresh invitation/tip (`animate-float`, reduced-motion
  safe).
- `WorldMap` — Pip greets on arrival (welcome / welcome-back), speaks a **varied region invitation** when
  the child taps a landmark (replacing the flat single tagline), celebrates kingdom growth, and offers a
  tip on tap. `Journal` opens in Pip's voice ("our adventure journal") + a small Pip in the header. The
  `WelcomeMoment` already carried the Pip cameo (NK-1) — now consistent end-to-end.
- Modules untouched. tsc 0 · clean build (entry `index-DA1vsOKc.js`) · SW fix intact · deploy verified.
- **→ Freeze NK-4** — *founder review, then Freeze before NK-5 (Regional Identity — per-module skins).*

### NK-5 — Regional Identity 🎨
Each existing module gets a **thematic skin only** — same gameplay, different feeling. Module-by-module,
low risk, high impact. Examples:
- 🌊 **Shape Lake** — shapes become fish / turtles / lily pads / boats.
- 🚂 **Number Railway** — ten-frame → ten seats; addition = boarding; subtraction = leaving.
- 🌳 **Counting Forest** — greens, dappled light, forest creatures around the existing tasks.
Freeze **per region** (or per agreed batch) before moving on.

### NK-6 — Castle Celebration 🏰
The Number Castle finale is a **festival, not a boss battle**. The child revisits everything learned
through joyful mixed activities; the reward is celebration, not completion. No fail state, no timer.
**Freeze → Number Kingdom v1 complete.**

---

## 4. Constraints & non-negotiables (the hard limits)

1. **Offline, zero external, CSP-locked.** Self-contained PWA: no CDN, no web fonts, no APIs, no external
   images. Everything precached & same-origin. The existing strict CSP (`default-src 'self'`, etc.) stays.
2. **Art ceiling = animated storybook SVG.** Built entirely in code (SVG + CSS gradients + gentle
   animation + emoji) — no illustrator, no asset pipeline, no raster art packs. Warm and cohesive, **not**
   literally Ghibli/Animal-Crossing painted raster. This keeps it tiny and offline-forever.
3. **No runtime AI.** Pip and all narration are **scripted pools**, selected contextually — never
   generative. #FreeForever cannot absorb per-learner API cost ([[tph-ai-principle]]).
4. **Ages 3–5 navigation.** One-screen map, one tap deep, character animates to the tapped place,
   "Continue Journey" restores context. **No free-roam walking, no corridors, no way to get lost/stuck** —
   a lost child breaks the no-fail promise.
5. **No-fail everywhere.** Wrong taps wobble, never penalise. No timers, no scores, no percentages.
6. **Performance.** No game engine, no physics lib. Respect `prefers-reduced-motion`. Keep region scenes
   lazy-loaded (modules already are). Must stay smooth on low-end Android.
7. **Don't touch TPH Core** (frozen SDK) — advisory/consume-only. Never run engine batch/processRepo
   against this repo (it's external to `generated-repos/`).
8. **PWA update hygiene** — the SW registration fix (`7634696`: `injectRegister:'auto'` + skipWaiting +
   clientsClaim + cleanupOutdatedCaches) must be preserved so users actually receive the new world.

---

## 5. Cross-cutting systems (draft Constitution content for NK-0)

- **Companion system** — Ollie/Fifi/Lulu personalities never break; Pip is the world's guide, invite-led.
- **Environment (Living Kingdom)** — the single reward mechanism; replaces stars/percentages entirely.
- **Math Adventure Journal** — the child's journey memory; collection, not assessment.
- **Vocabulary** — every concept still registers its words (more/less/circle/five/pattern/long/heavy…),
  ready for the shared Vocabulary Engine on D-13 adoption.
- **Accessibility** — voice-first, replay, large targets, reduced motion, high contrast, visual
  instruction mode, motor alternatives — carried from the current app, not regressed.
- **The Welcome Moment** — now an ecosystem principle (**PROJECT_DNA Principle 18**, founder-ratified
  2026-07-04): one unforgettable, once-only, warm, narrated first entrance that also unlocks audio.
  Reference implementation is Number Kingdom's `WelcomeMoment.tsx` (NK-1).

---

## 6. Definition of Done (Number Kingdom v1)

- The child arrives in a **place**, not a menu; navigates by walking to landmarks; every module reachable
  in one tap from its region.
- The world **visibly grows** with play and **feels alive** (daily life layer); no numbers/stars/percent.
- **Pip** guides throughout; the trio's personalities are consistent.
- The **Adventure Journal** records the journey.
- All 16 educational modules run **unchanged in logic**, reskinned to their region.
- Still: fully offline · zero external · CSP-locked · no runtime AI · no-fail · clean `tsc`/build ·
  passes a **real-child play-test** · meets the Google-Play "Expert Approved" bar.

---

## 7. Execution protocol for the next AI

1. **Do not build UI until NK-0 (Constitution) is founder-frozen.** Blueprint → Freeze → Build.
2. Build **one NK milestone at a time**, fully, then **await the founder's Freeze** before the next.
3. **Never rewrite educational modules** — NK-5 is a *skin* only; gameplay logic is frozen.
4. Honour the founder's working style ([[feedback_collaboration]]): plan-first, phase-by-phase, don't
   invent scope. **This blueprint is the scope.**
5. Preserve all hard constraints in §4 (offline, no external, no AI, no-fail, one-tap nav, art ceiling,
   PWA update hygiene).
6. After each milestone: `tsc --noEmit` 0 · clean `vite build` · deploy-verify (entry hash + chunk 200) ·
   update this doc + [`early-numeracy.md`](./early-numeracy.md) + `SESSION_HANDOFF.md` · commit + push app
   and Brain · record the play-test outcome.

## Related
- [`early-numeracy-roadmap.md`](./early-numeracy-roadmap.md) — the educational roadmap (Phases 1–10, build-complete)
- [`early-numeracy.md`](./early-numeracy.md) — app memory + per-phase build record
- [[tph-ai-principle]] · [[tph-single-brain]] · [[feedback_collaboration]] · [[tph-app-ecosystem]]
