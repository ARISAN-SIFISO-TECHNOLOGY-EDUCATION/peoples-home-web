# 🌈 Number Kingdom — Experience Roadmap (Early Numeracy · World A)

> **Status: BLUEPRINT — awaiting founder Freeze (drafted 2026-07-04).**
> This is the experience-layer roadmap that elevates **Early Numeracy** from a collection of
> activities into a **living world** the child inhabits. It does **not** replace the educational
> roadmap — [`early-numeracy-roadmap.md`](./early-numeracy-roadmap.md) (Phases 1–10) is **build-complete**
> and its 16 no-fail modules stay intact. Number Kingdom is the **shell/world layer built over them.**
>
> **Governance (founder's model): Blueprint → Freeze → Build.** Each NK milestone is frozen before the
> next begins. **Freeze is a founder act** — the next AI never self-declares a freeze.

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

### NK-0 — Kingdom Constitution ⚖️ *(author + freeze BEFORE any UI)*
Lock the principles the whole world obeys. No code. Ratify → **Freeze**. Covers:
- **Educational philosophy** — inherits World-A non-negotiables (Offline First · Audio First · Confidence
  Before Correction · No Failure States · No Timers · Child-Led Discovery · Learning Through Play ·
  Environment As Reward · Companion Guided · Ages Before Grades · No Ads · **#FreeForever**).
- **Emotional design** — wonder, warmth, a place worth returning to; never a dashboard, never a test.
- **Companion behaviour** — Pip's voice rules (invite, never instruct; never says "let's do maths").
- **Navigation principles** — one screen, one tap deep, a child can never get lost or stuck.
- **Environmental growth** — the world changes with play; no numbers, no stars, only visible change.
- **Accessibility rules** — large targets, voice-first, visual instruction mode, reduced motion, high
  contrast, motor alternatives.
- **TPH Core integration** — advisory/consume-only; do **not** modify TPH Core (frozen SDK). Adopting the
  shared **TPH Learning Engines** (D-13) is the long-game; Number Kingdom is built so that adoption slots
  in later without another rebuild.
> The draft Constitution lives in §5–§6 of this doc; NK-0 = founder ratifies and freezes it.

### NK-1 — World Map 🗺️
The home screen becomes the Kingdom. A single-screen illustrated map with the seven landmarks, a sky, a
child character, and **"⭐ Continue Journey"** (returns to the last region). Tapping a landmark walks the
character there and opens that **region screen** — a themed sub-screen listing its modules as illustrated
"places" ("🌳 Counting Forest — Animals are waiting!"). Everything one tap deep. **Freeze.**

### NK-2 — Living Kingdom 🌱 *(includes the Daily Life Layer)*
Progress becomes *visible world change*, absorbing the current Math Village. Built on the existing progress
store (`lib/progress.ts` `seeds`/rounds). As the child plays: flowers bloom → butterflies arrive → birds
return → windmills spin → the river flows → the bridge is repaired → the castle is restored. **No numbers,
only change.**
- **Daily Life Layer** (founder addition) — the world feels *lived in*, independent of learning:
  morning the village wakes & birds appear; evening lanterns glow; rain brings puddles and hides
  butterflies; wind moves the leaves. Purely ambient/cosmetic (real device clock, no module logic).
  Reuses the visual language of `time-and-day` without touching the module. **Freeze.**

### NK-3 — Math Adventure Journal 📖
Rename & expand "My Number Book". The child collects the memory of their journey: numbers met · shapes
found · patterns solved · counting discoveries · animals counted · favourite games · achievements · a
journey map. Needs a modest new collection store (append-only, schema-drift-safe like `progress.ts`).
**Freeze.**

### NK-4 — Companion Integration 🐿
Keep the trio — 🦉 **Ollie** (patient teacher) · 🦊 **Fifi** (explorer) · 🐦 **Lulu** (celebration) — and
introduce 🐿 **Pip, the Kingdom Guide.** Pip is not another teacher; Pip invites discovery. Scripted line
pool (no runtime AI — true to #FreeForever), woven into region entry / correct / level-up, extending the
existing `useInstruction` narration. Examples: *"Let's see what's hiding in the forest!"* · *"I wonder who
needs our help today."* Never: *"Let's do maths."* **Freeze.**

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
