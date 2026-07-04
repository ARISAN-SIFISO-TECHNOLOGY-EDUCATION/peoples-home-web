# Session Handoff

> **Purpose:** Every AI session that does meaningful work in this project should end
> by updating this file. This is the only reliable way to bridge sessions when context
> windows end.
>
> **Protocol:** Append a new entry at the TOP (newest first). Never delete old entries.
> Date every entry. Be specific — future-you has zero context.
>
> **If you are starting a session:** read the most recent entry below, then check
> `CURRENT_STATE.md`. That's enough to resume.

---

## ✅ 2026-07-04 (session 32) — Early Numeracy: Phase 8 (Time & Day) shipped

**Phase 8 — Time & Day — BUILT & LIVE** (`early-numeracy` `99afc3f`; deployed + verified):
- 🕐 **Time & Day** module — time & daily life; pre-reader friendly (no numerals to read).
- One module cycles **three no-fail activities** across 10 levels: **TIME OF DAY** (tap the named sky —
  morning 🌅 / afternoon ☀️ / night 🌙, themed gradient scenes), **SEQUENCE** (tap daily-life pictures
  first → last — six sets covering routines + time sequences), **CLOCK** (match the clock showing the
  same time — SVG clock faces, hour hand ≥3h apart so the difference stays visually obvious; simple
  o'clock, visual only).
- New **"🕐 Time & Day"** home section (`ModuleGroup` gained `'daily'`). Home = Play & Learn · Adding &
  Taking Away · Shapes · Measuring · Time & Day · Practice · Explore.
- **Honest scope note:** days-of-week *naming* is deliberately light (touched via morning→afternoon→
  night vocabulary) — spelling day names is reading-heavy for ages 3–5; can deepen later.
- Verified: tsc 0 · clean build (TimeAndDay lazy chunk, precache 29, zero external) · all three
  generators proven over 600k rounds (clock reshuffle terminates ≤15) · deploy verified (entry
  `index-CrjdKx1A.js`, chunk 200).

**⛔ Phases 2.5–8 not yet Frozen** — only gate left is the **real-child play-test** (human). Phase 2 is
the sole Frozen phase. **NEXT AI:** on play-test confirmation → Freeze 2.5–8 → start **Phase 9 (Money —
South African context)** — coins · notes · buying · selling · simple change · pretend shop. D-13
reminder stands (own hooks, not the shared TPH Learning Engines).

---

## ✅ 2026-07-04 (session 31) — Early Numeracy: Phase 7 (Measuring World) shipped

**Phase 7 — Measuring World — BUILT & LIVE** (`early-numeracy` `76c1118`; deployed + verified):
- 📏 **Measuring World** module — measurement & comparison (big/small · tall/short · heavy/light ·
  long/short · full/empty), all visual estimation, no numerals required to play.
- One module cycles **three no-fail activities** across 10 levels: **COMPARE** (tap the
  bigger/taller/longer/heavier/fuller — or the opposite — across all five attributes; size attrs scale
  the same emoji, heavy uses intuitive pairs like 🐘/🐁, full/empty uses a `FillGlass` fill bar),
  **ARRANGE** (seriation — tap three same-emoji things smallest → biggest), **MEASURE** (non-standard
  units — count how many unit blocks long a thing is, "it is n blocks long!").
- New **"📏 Measuring"** home section (`ModuleGroup` gained `'measure'`). Home = Play & Learn · Adding &
  Taking Away · Shapes · Measuring · Practice · Explore.
- Verified: tsc 0 · clean build (Measurement lazy chunk, precache 28, zero external) · all three
  generators proven over 400k randomized rounds · deploy verified (entry `index-DeWBCSvT.js`, chunk 200).

**⛔ Phases 2.5–7 not yet Frozen** — only gate left is the **real-child play-test** (human). Phase 2 is
the sole Frozen phase. **NEXT AI:** on play-test confirmation → Freeze 2.5–7 → start **Phase 8 (Time &
Daily Life)** — morning/afternoon/night · days · simple clocks · daily routines · sequences. D-13
reminder stands (own hooks, not the shared TPH Learning Engines).

---

## ✅ 2026-07-04 (session 30) — Early Numeracy: Phase 6 (Shapes World) shipped

**Phase 6 — Shapes World — BUILT & LIVE** (`early-numeracy` `ac1634d`; deployed + verified):
- 🔷 **Shapes World** module — 2D shapes (circle · square · triangle · rectangle · oval · heart · star)
  via a new SVG primitive `Shape.tsx` (one 100×100 space, reused for fills, outlines and trace dots).
- One module cycles **five activities** as levels, each mirroring a proven mechanic: **FIND** (tap all of
  a shape), **MATCH** (tap the named shape), **TRACE** (connect-the-dots outline, ref-based), **BUILD**
  (fill a picture's slots — house/party hat/snowman/badge), **REAL-WORLD** (find real things of a shape).
  All no-fail.
- New **"🔷 Shapes"** home section (`ModuleGroup` gained `'shapes'`). Home = Play & Learn · Adding &
  Taking Away · Shapes · Practice · Explore.
- Verified: tsc 0 · clean build (12 lazy chunks, precache 27, zero external) · all five activity
  generators proven valid · deploy verified.

**⛔ Phases 2.5–6 not yet Frozen** — only gate left is the **real-child play-test** (human). Phase 2 is
the sole Frozen phase. **NEXT AI:** on play-test confirmation → Freeze 2.5–6 → start **Phase 7
(Measurement)** — big/small · tall/short · heavy/light · long/short · full/empty (compare · arrange ·
measure · estimate). D-13 reminder stands (own hooks, not the shared TPH Learning Engines).

---

## ✅ 2026-07-04 (session 29) — Early Numeracy: Phase 5 (Taking Away) shipped

**Phase 5 — Taking Away — BUILT & LIVE** (`early-numeracy` `420280d`; deployed + verified):
- ➖ **Taking Away** module — subtraction as concrete take-away stories, **still visual, no equations**.
  A group is shown; the child taps items to send them away, the "how many left" count ticks down, then
  they hear "n take away m leaves left".
- One take-away engine cycles **five themes** as levels: Birds Fly Away · Cookie Time · Fish Swim Away ·
  Blocks Away · Balloons Float Away. N grows to 5, then to 9. Story amount gone → rest lock (no
  over-removing, no fail state).
- Operations home section renamed **"➕➖ Adding & Taking Away"**. Home = Play & Learn · Adding & Taking
  Away · Practice · Explore.
- Verified: tsc 0 · clean build (11 lazy chunks, precache 26, zero external) · subtraction bounds proven
  · deploy verified.

**⛔ Phases 2.5–5 not yet Frozen** — only gate left is the **real-child play-test** (human). Phase 2 is
the sole Frozen phase. **NEXT AI:** on play-test confirmation → Freeze 2.5–5 → start **Phase 6 (Shapes
World)** — 2D shapes (circle · square · triangle · rectangle · oval · heart · star): find shapes, build
pictures, shape sorting, tracing, real-world objects. D-13 reminder stands (own hooks, not the shared
TPH Learning Engines).

---

## ✅ 2026-07-04 (session 28) — Early Numeracy: Phase 4 (Addition Adventure) shipped

**Phase 4 — Addition Adventure — BUILT & LIVE** (`early-numeracy` `7da1f98`; deployed + verified):
- ➕ **Addition Adventure** module — concrete visual addition, **no equations**. Two groups are shown;
  the child taps each item into a container while the voice counts up, then hears "a and b make total".
- One join-and-count engine cycles the **five roadmap themes** as levels: Add Together · Magic Basket ·
  Feed the Animals · Treasure Chest · Bridge Builder. Sums grow to 5, then to 10.
- Kept as **one** card (same mechanic, calmer home) rather than five; new **"➕ Adding"** home section
  (`ModuleGroup` gained `'operations'`). Home = Play & Learn · Adding · Practice · Explore.
- Verified: tsc 0 · clean build (10 lazy chunks, precache 25, zero external) · addition round bounds
  proven · deploy verified.

**⛔ Phases 2.5, 3 & 4 not yet Frozen** — the only gate left is the **real-child play-test** (human).
Phase 2 is the sole Frozen phase. **NEXT AI:** on play-test confirmation → Freeze 2.5 + 3 + 4 → start
**Phase 5 (Taking Away)** — subtraction through stories (birds fly away, cookies eaten…), still visual.
D-13 reminder stands (own hooks, not the shared TPH Learning Engines).

---

## ✅ 2026-07-04 (session 27) — Early Numeracy: Phase 3 (Numbers Everywhere) shipped

**Phase 3 — Numbers Everywhere — BUILT & LIVE** (`early-numeracy` `dacd6a6`; evergreen description
`680afbc`; deployed + verified, live entry `index-DRC0W2up.js`):
- 🌍 **Numbers Everywhere** module — seven real-world scenes (Kitchen · Garden · Bedroom · Playground ·
  Shops · Road · Home). Each poses a data-driven, no-fail **COUNT** ("count the apples") or **FIND**
  ("find 3 windows") task over tagged scene objects; right taps count up aloud, others wobble.
- New **"🌍 Explore"** home section (`ModuleGroup` gained `'explore'`); home = Play & Learn · Practice ·
  Explore.
- Verified: tsc 0 · clean build (9 lazy chunks, precache 24, zero external) · scene-logic invariants
  proven solvable for all 7 scenes across randomized rounds · deploy verified.

**⛔ Phases 2.5 & 3 not yet Frozen** — only gate left is the **real-child play-test** (human). **NEXT
AI:** on play-test confirmation → Freeze 2.5 + 3 → start **Phase 4 (Addition Adventure)** — joining
groups, visual addition, story problems (no equations first). D-13 reminder still stands (own hooks, not
the shared TPH Learning Engines). Docs updated: `apps/early-numeracy.md`, `apps/early-numeracy-roadmap.md`,
`ROADMAP.md`.

---

## ✅ 2026-07-04 (session 26) — Early Numeracy: Phase 2 FROZEN + Phase 2.5 (Numeracy Confidence) shipped

Founder authorized freezing Phase 2 and starting 2.5. Both done.

**Phase 2 — FROZEN** ✅ (`fa777a6`, founder-authorized). The six Number Discovery modules are the
locked baseline.

**Phase 2.5 — Numeracy Confidence — BUILT & LIVE** (`early-numeracy` `22b5a0b`, deployed + verified):
- **🌞 Today** home surface (`components/TodayStrip.tsx`) — daily-rotating suggested activity, the
  child's **favourite** to replay (most-played), and a spoken **real-world counting** nudge from the
  transfer-prompt pool. Suggestions only; no scores.
- **🔢 Number Match** — numeral↔quantity recognition/matching (both directions, alternating by level).
- **🔍 Number Hunt** — find the called-out numeral among decoys (3 finds/round), spoken target cue.
- Home now grouped into **"Play & Learn"** (the six) + **"🎯 Practice"** (the two games);
  `ModuleDef.group` added.

**Verified:** tsc 0 · clean build (8 lazy chunks, PWA precache 23, zero external requests) · Phase-2.5
logic invariants checked across randomized rounds · **deploy verified live** (entry-chunk hash match;
NumberMatch/NumberHunt chunks 200).

**⛔ Phase 2.5 not yet Frozen** — only gate left is a **real-child play-test** (human). **NEXT AI:** on
play-test confirmation → Freeze 2.5 → start **Phase 3 (Numbers Everywhere)** — scenes (Kitchen · Garden
· Bedroom · Playground · Shops · Road · Home) where maths is discovered in the world. Reminder (D-13):
the app still uses its own hooks, not the shared TPH Learning Engines — adopting them stays part of the
work. Docs updated: `apps/early-numeracy.md`, `apps/early-numeracy-roadmap.md`, `ROADMAP.md`.

---

## ✅ 2026-07-04 (session 25) — Early Numeracy Phase 2 (Number Discovery) BUILT, LIVE & verified

Executed the locked roadmap's **Phase 2**. The five "Coming soon" stubs are now **six real, no-fail,
audio-guided modules** (commit `early-numeracy` `fa777a6`, deployed to early-numeracy.pages.dev):

- **🌼 Counting Garden** — tap-to-count, one-to-one correspondence, spoken counting, number recognition.
- **🍎 Which is More?** — more / fewer / equal (equal via a centre button); wrong tap re-asks, no penalty.
- **✏️ Number Shapes** — trace the numeral by connecting ordered dots (drag or tap, any order, forgiving);
  numeral shown with its quantity; 1–10.
- **🎨 Pattern Maker** — AB / ABC / AABB / ABB; gap at end then middle; tap-to-fill.
- **⭐ Make Five / 🌟 Make Ten** — `make-five-ten` **split** into two modules on a shared `MakeGame`
  engine; part–whole fact spoken; can't overfill.

**Platform:** progress store (`lib/progress.ts`, schema-drift-safe default-merge), shared
`components/module-kit.tsx` (frame chrome, celebration, level dots, prompt, number words), `say`/`saySlow`
on `useInstruction` (audio-only — every module fully playable silently in visual mode), and an
**environment-as-reward Math Village** that grows on the home screen (+ per-card growth leaves; no stars).
`ModulePlaceholder` removed. Target ages aligned to **3–5** (index.html + PWA manifest).

**Verified:** tsc 0 · clean build (6 lazy chunks, PWA precache 21, zero external asset requests) · pure
game-logic invariants checked across thousands of randomized rounds · **deploy verified live** (manifest
now "Six game modules… ages 3–5"; entry-chunk hash matches local build; module chunks 200).

**⛔ Not yet Frozen.** The only remaining Phase-2 gate is a **real-child play-test** (human step).
**NEXT AI:** if the founder confirms the play-test passed → Freeze Phase 2 → start **Phase 2.5 (Numeracy
Confidence)**. Reminder (D-13): the app still uses its own hooks, not the shared TPH Learning Engines —
adopting them stays part of "finishing the product." Docs updated: `apps/early-numeracy.md`,
`apps/early-numeracy-roadmap.md`, `ROADMAP.md`.

---

## ✅ 2026-07-03 (session 24) — Early Numeracy product roadmap LOCKED + Space Explorer deployed/linked

**Space Explorer:** deployed by the founder at **https://ikhaya-space-explorer.pages.dev/** (the bare
`space-explorer.pages.dev` was taken) and **linked live** on The People's Home Curiosity pillar
(`peoples-home-web` `06c9e05`; Brain `dd384b3`). Verified our hardened build is serving.

**Confirmed complete across all three on-ramps** — audit + security + bug-identifier/fix:
- Early Numeracy: `8a03f92` (audit/security) + `de7e06f` (bug).
- Early Literacy: `28b1fbe` (security) + remaster + `2ba6bf3` (bug).
- Space Explorer: `cd8e9ce` (in-house/security) + `2dad860` (bug). Memory accurate — no correction needed.

**🔒 Early Numeracy — complete product roadmap LOCKED.** The founder handed over a comprehensive
Phase 1–10 plan ("finish the **product**, not the app" — the same treatment Early Literacy and Space
Explorer received). Saved verbatim-in-spirit as **`brain/apps/early-numeracy-roadmap.md`** (authoritative;
supersedes the old Blueprint-v1 "Implementation phases"). Pointers added at the top of
`apps/early-numeracy.md` and in `ROADMAP.md`.
- **Scope:** Phase 2 Number Discovery (6 modules) → 2.5 Confidence → 3 Numbers Everywhere → 4 Addition
  → 5 Subtraction → 6 Shapes → 7 Measurement → 8 Time → 9 Money (SA) → 10 Data & Sorting. Each phase
  ends with a **Freeze** through the quality gates. Cross-cutting: Companion, Math Village environment,
  "My Number Book", Vocabulary Engine, Parent Corner, accessibility. Bar = Google Play "Expert Approved".
- **Naming (D-13):** the roadmap's "TPH Core v1.0 (Frozen)" = the **TPH Learning Engines** set; build
  Early Numeracy on those public contracts (it currently uses its own hooks — adopting them is part of
  the work). Do not confuse with `@tph/core`.
- **NEXT AI STARTS HERE:** execute **Phase 2** (turn the 5 "Coming soon" module stubs into real
  gameplay; split Make 5 / Make 10), one phase at a time, freeze between. Founder is taking a break.

---

## ✅ 2026-07-03 (session 23) — Space Explorer brought in-house (Curiosity #3) + Foundations marked in-progress

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/Space-Explorer` `main` — `cd8e9ce` (conversion),
`2dad860` (bug fixes), `be663c0` (README). **Site:** `peoples-home-web` `main` `57fba54`.

**1. Foundations marked in-progress** on the site: Early Numeracy is linked live but is a Phase-1
shell, so the Foundations pillar card now shows "· in progress" (`incomplete` flag in PILLARS).

**2. Space Explorer** — cloned and given the full Early Literacy in-house treatment (it's another
Google AI Studio / Gemini export). A polished, **complete** Curiosity & Knowledge app (ages 3–17):
solar-system discovery, 5 tabs, curiosity-points → ranks, local profile. **No app logic/UI changed.**
- **AI dropped** (unused): removed `@google/genai` + `express` + `dotenv` + `motion`, cleared the
  Gemini capability, deleted `.env.example`.
- **True offline:** removed a **live Google Fonts `@import`** (the app claims "fully operational
  offline" — now real). Zero external requests. Offline PWA added (vite-plugin-pwa + zlib icons).
- **Deploy prep:** name → `space-explorer`; tailwind + pwa → deps; **`@types/react` added** (tsc was
  hollow → real, 0 errors); `_headers` CSP + `_redirects` + `wrangler.toml`; **new README**.
- **Bug sweep (bug-identifier/bug-fixer):** fixed the same High class as Early Literacy — unguarded
  `localStorage.setItem` (now try/catch) + no default-merge on profile load (now
  `{...DEFAULT_PROFILE, ...parsed}`). `tsc`/build clean, `npm audit` 0.

**⚠️ Deploy blocker (pick up here):** Space Explorer is **not deployed**. The bare subdomain
`space-explorer.pages.dev` is **taken by an unrelated app ("GravityDemo")**, so a Cloudflare Pages
project for this repo needs a **different** project name/subdomain. Steps: connect the repo (preset
None/Vite, build `npm run build`, output `dist`, no env). **Then** flip its Curiosity PILLARS entry in
`index.html` from `future` → `live` with the real URL (left as `future` so the site never links the
wrong app). Full detail: `brain/apps/space-explorer.md`.

---

## ✅ 2026-07-03 (session 22) — Bug skills connected + swept Early Numeracy & Early Literacy

Connected the founder's **skills library** (`SifisoScS/skills`, 232 playbooks) to the engine repo
and used two of them — **`bug-identifier`** then **`bug-fixer`** — on both Foundations on-ramps, the
same way audit + security were applied.

**Skills setup:** cloned to `repository-engine-1000/.claude/skills` (own git repo, `origin` intact,
gitignored in the engine). **Strengthened** both bug skills for universality (pushed to `SifisoScS/skills`
`6f9998f`): bug-identifier gained a **PWA / offline-first / static-client-app** stack hotspot (third-party
font/CDN calls that break offline + leak, precache gaps, unguarded storage, media-before-gesture,
lazy/Suspense without an error boundary, broken PWA icons, missing CSP); bug-fixer gained a
**no-test-harness** verification path (reproduce-in-app + type-check/build + live check; a green build
is the floor, not the ceiling).

**Early Numeracy (`early-numeracy` `master` `de7e06f`)** — sweep was mostly clean (the session-21 audit
had already hardened it; the type system guards the narration contract). One **[Medium]** confirmed:
`goToModule`/`goHome` scheduled post-navigation narration via `setTimeout` but never cleared it, so a
fast-tapping child (module → back within 350ms) heard the module-entry line speak on the home screen.
Root-cause fix: hold the nav-narration timer in a ref, clear before re-scheduling + on unmount. Sibling
sweep: HomeScreen/ModulePlaceholder already clear on unmount. Reported-not-fixed: welcome autoplay
before a gesture (needs device repro), idle-timer resets every render (latent, Phase-2).

**Early Literacy (`early-literacy` `main` `2ba6bf3`)** — one **[High]** confirmed and fixed:
the loader did `setProgress(JSON.parse(saved))` with **no default merge**, so a returning user whose
saved progress predates a newer field (`storybooks`, `wordsSpelled`, `vocabulary`, `birds`, `trees`)
got `undefined` there; 8+ components read those unguarded (`progress.storybooks.includes`,
`wordsSpelled.length`, `completedActivities['key']`) → `TypeError` on load → ErrorBoundary → but the
malformed value persists → reload → **crash loop, user bricked**. Fix: `{...defaultProgress, ...parsed}`
+ `{...defaultSettings, ...parsed}` (the pattern early-numeracy's `useSessionState` already uses).
**Reproduced before/after in node** (old-schema blob threw 3 TypeErrors before; after, fields default
and saved values are preserved). `tsc`/build clean on both apps.

---

## ✅ 2026-07-03 (session 21) — Early Numeracy: senior audit + security pass + linked LIVE on the site

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-numeracy` `master` — commit `8a03f92`.
**Site:** `peoples-home-web` `main` — commit `125331c`. **Live:** https://early-numeracy.pages.dev/

Gave Early Numeracy the same treatment as Early Literacy — audit against the real code, security
hardening, then linked it into The People's Home. **No gameplay changed; it remains a Phase 1 shell**
(all 5 modules still "Coming soon"). It was already deployed at early-numeracy.pages.dev but not linked.

- **C1 — real PWA icons.** `generate-icons.mjs` imported `canvas` (uninstalled) → the catch wrote 1×1
  70-byte placeholders; the PWA had no real install icon. Ported the dependency-free zlib generator
  (green brand) → proper 192/512/maskable icons.
- **C2 — zero external.** Removed a dead Google-Fonts `runtimeCaching` block from `vite.config.ts`
  (no fonts are actually loaded) → the app now makes zero external requests.
- **M1 — ErrorBoundary** wrapping `<App>` (child-safe "garden is resting" fallback).
- **Security `public/_headers`** (CSP `script-src 'self'` with NO unsafe-inline — build has no inline
  scripts; style-src keeps unsafe-inline for Tailwind; worker-src blob: for Workbox — plus
  X-Frame-Options DENY, nosniff, no-referrer, Permissions-Policy). `wrangler.toml` pins `dist`;
  moved `vite-plugin-pwa` to `dependencies` (prod-install safety). `npm audit` = 0 vulns.
- **Verified LIVE:** all 5 security headers serving on early-numeracy.pages.dev; assets 200 w/ correct MIME.
- **Linked on The People's Home:** converted the Foundations `future` placeholder → live entry
  (`status:'live'` + url) in `index.html` PILLARS. Verified present on peoples-home-web.pages.dev.
  **Foundations is now fully live** (Math Adventure · ReadAfrica · Everyday Foundations · Early
  Literacy · Early Numeracy). Brain synced: `apps/early-numeracy.md`, `ECOSYSTEM.md`, `ROADMAP.md`.

**Verified:** `tsc --noEmit` 0 errors; `vite build` clean; `_headers` in `dist/`; 19 chunks precached.

### Remaining for Early Numeracy — content/UX, not hardening
Phase 2 real gameplay (all modules are placeholders) · welcome-audio autoplay-without-gesture (defer
to a UX pass, EL's M9 class) · `build` script uses bash env `WEB_BUILD=1` (Linux/Cloudflare only) ·
device play-test with a real 3–7-year-old.

---

## ✅ 2026-07-03 (session 20) — Early Literacy: M10 (all 26 letters) + security pass + CSP verified LIVE

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy` `main` — commits `611a9cd`, `28b1fbe`.
**Brain:** `peoples-home` `main` — commit `c4b3e40`.

Closed out the last two engineering items on the remaster backlog. Only content/localisation (M11)
and a real-child play-test remain.

- **M10 — full alphabet authored (`611a9cd`).** Extended the letter content from 9 letters to all
  26 across four data sets: `LETTER_DB` (`LetterGarden.tsx`), `TRACE_PATHS_DB` (`tracing.ts`),
  `DISCOVERY_CATALOG_DB` (`discovery.ts`, SA-first facts — African penguins, savanna lions,
  African-plains zebras), and `VOCABULARY_DB` (`vocabulary.ts`, +15 words). `ACTIVE_LETTERS` now
  derives from the DB keys (sorted) — no letter falls back to the triangle placeholder any more.

- **Security pass (`28b1fbe`).** Added `public/_headers` (Cloudflare Pages) + fixed the "Suggeted"
  → "Suggested" typo in the Grown-up Corner. Attack surface is deliberately tiny (offline, no
  backend/accounts/PII/AI, `npm audit` = 0 vulns, no secrets). The built HTML ships **no inline
  scripts/handlers**, so `script-src 'self'` holds with **no `'unsafe-inline'`** — strongest
  practical script policy. `style-src` keeps `'unsafe-inline'` (Tailwind v4 + `motion` runtime
  styles); `worker-src 'self' blob:` for Workbox. Also X-Frame-Options DENY + `frame-ancestors
  'none'`, nosniff, `Referrer-Policy: no-referrer`, and a Permissions-Policy denying
  camera/mic/geo/payment/usb/FLoC. Mirrors iKhaya's proven policy, minus the `/api` rules (no backend).
  Full Security Report written into `apps/early-literacy.md` §12.

- **CSP verified LIVE on early-literacy.pages.dev (2026-07-03).** `curl -I` confirms all 5 headers
  serving byte-identical; Cloudflare rebuilt on the push (entry chunk now `index-Ber5XZxi.js`).
  Every referenced resource is same-origin and returns `200` with correct MIME (JS/CSS/manifest/SW),
  so `'self'` covers everything and `nosniff` is safe. **Not yet checked:** zero *runtime* CSP
  violations from motion/Tailwind — needs a real browser console (folds into the device play-test).

**Verified:** `tsc --noEmit` 0 errors; `vite build` clean; 29 chunks precached (offline intact).
Production-readiness now ~9/10. *(Build- + header-verified; not yet browser-tested on a device.)*

### ✅ "TPH Core" naming decision — RESOLVED this session (`49edf66`, `D-13`)
Founder chose to **rename the app's runtime to the "TPH Learning Engines"**, reserving "TPH Core" for
the canonical SDK. Applied in the app (TS symbols `TPHCore*` → `TPHLearning*`, UI badge, app-local
doc) — pure rename, `tsc`/build clean. Brain updated: integration doc §4, `apps/early-literacy.md`
(§5/§9/§11/§12), and decision log **D-13**. No collision remains.

### Remaining — human-gated, not engineering
- **M11** — isiZulu / SA-language packs. Deferred to the **~Dec 2026** cross-app localisation batch;
  needs a **native-speaker** review (do NOT machine-translate a children's literacy app).
- **Device play-test** — observe a real 3–7-year-old; confirm no runtime CSP violations in-browser.
- **Fold into `@tph/core` (Option 2), later** — the TPH Learning Engines remain a candidate
  contribution to the canonical SDK once `@tph/core` extraction is actually underway. Not now.

---

## ✅ 2026-07-02 (session 19) — Early Literacy: remaster Phase 3 (M7, M9, M12 — UX/safety)

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy` `main` — commit `47df259`.

- **M7 — adult gate:** the Grown-up Corner (can reset all progress) now sits behind a two-digit-sum
  gate (`AdultGate.tsx`). Village → gate → corner on success. Stops a child wiping progress.
- **M9 — no autoplay:** removed the blocked timer greeting. New users unlock audio via the
  age-selection tap; returning users get a "tap to begin" screen; the welcome is spoken in that gesture.
- **M12 — real-world transfer:** closing a module shows a spoken "Try this at home" card
  (`TransferPrompt.tsx`, 16 SA-first literacy prompts), once per browser session.

**Verified:** `tsc --noEmit` 0 errors; `vite build` clean; 29 chunks precached (offline intact).
Production-readiness now ~8.5/10. *(Build-verified, not yet browser-tested on a device.)*

### Remaining (Phases 4–5) — now mostly content/authoring
M10 (only 9 of 26 letters have tracing/discovery) · M11 (isiZulu / SA-language packs — Dec 2026) ·
hygiene (`public/_headers`, "Suggeted" typo). Plus the open founder decision: **"TPH Core" naming
reconciliation**.

---

## ✅ 2026-07-02 (session 18) — Early Literacy: remaster Phase 2 (M3, M4, M8)

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy` `main` — commit `7077f99`.

- **M3 — single tree-stage owner:** `App.tsx` no longer computes its own stage thresholds; it
  delegates to `EnvironmentEngine`, now a pure function of stars/completions (not seeded by the
  persisted value). The two-formula inconsistency is gone.
- **M4 — real type-checking + doc truth:** added `@types/react` + `@types/react-dom` (were missing,
  so `tsc` was hollow) — **0 errors surfaced**. Corrected the app's `04-tph-core.md` with an
  "implementation reality" banner (Vocabulary "3-attempts → mastered" is aspirational; code masters
  on first spell). Tracing + Environment contracts do match the code.
- **M8 — code-split:** modules + modals are `React.lazy`/`Suspense`; `manualChunks`
  (react/motion/icons/vendor). **Initial `index` chunk 548 KB → 28 KB**; modules load on demand; all
  29 chunks precached so offline is intact.

**Verified:** `tsc --noEmit` 0 errors; `vite build` clean. Production-readiness now ~8/10.

### Remaining (Phases 3–5, in `apps/early-literacy.md` §12)
M7 (adult gate on Grown-Up Corner / reset) · M10 (only 9 of 26 letters have tracing/discovery) ·
M9 (tap-to-begin) · M12 (per-session "Try this at home") · hygiene (`_headers`, "Suggeted" typo).
Plus the open founder decision: the **"TPH Core" naming reconciliation**.

---

## ✅ 2026-07-02 (session 17) — Early Literacy: offline PWA + audit + Phase-1 fixes + repo → org

**Live:** https://early-literacy.pages.dev/ — now an **installable offline PWA**.
**Repo:** **transferred `SifisoScS/early-literacy` → `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy`**
(PRIVATE) `main` — commit `b22bc6b`.

### What was done
- **Offline PWA:** `vite-plugin-pwa` (Workbox precache of the full shell + SPA navigateFallback),
  unique manifest `id: /early-literacy/`, real branded icons via a **dependency-free** zlib PNG
  generator (`generate-icons.mjs`). Closes the World-A offline definition-of-done gap.
- **Senior architecture audit** (first-principles) run on the real code. **Phase 1 (critical) applied:**
  - **C1:** removed narration fetches to `actions.google.com` (Google-AI-Studio remnant) — the app
    now makes **zero network calls** (was silently breaking offline-first + no-tracking).
  - **C2:** single shared `AudioContext` (was creating one per SFX → audio died mid-session at the
    browser context cap).
  - **M5:** ErrorBoundary (child-safe fallback vs white screen). **M6:** guarded localStorage writes.
  - Fixed a latent `playCat` Web-Audio bug.
- **Brain updated:** `apps/early-literacy.md` now carries the full audit + remaster backlog (Phases 2–5).

### Remaster backlog (Phases 2–5) — see `apps/early-literacy.md` §12
M3 (single tree-stage owner) · M4 (engine contract↔code truth + **add `@types/react`** — type-checking
is currently hollow) · M8 (code-split the 156 KB monolith) · M7 (adult gate on Grown-Up Corner) ·
M10 (only 9 letters have tracing/discovery) · M9 (tap-to-begin) · M12 (per-session transfer prompt).

### Next steps (in order)
1. **Phase 2** — M3, M4 (incl. `@types/react`), M8. *(Recommended next.)*
2. **Founder decision:** "TPH Core" naming reconciliation (rename app engine set or fold into `@tph/core`).
3. **Add a live card** for Early Literacy on peoples-home-web.
4. **Phase 4.5** — build when directed.
5. 🔴 Keystore backup still outstanding (carried from session 11).

**Verified:** `tsc --noEmit` 0 errors; `vite build` clean; no `actions.google.com` in `dist/`.

---

## ✅ 2026-07-02 (session 16) — Early Literacy: AI dropped + DEPLOYED (✅ LIVE)

**Live:** **https://early-literacy.pages.dev/** (Cloudflare Pages). **Repo:** `SifisoScS/early-literacy`
`main` — commit `2c2f211`.

**Why:** Early Literacy is a `#FreeForever` World-A app — founder: *"the app was developed using
Google AI Studio, so they added the AI as per their rules, but we don't use AI in our apps as they
are free."* So the AI was removed and the app deployed.

### What was done (no app logic / UI changed)
- **Dropped AI:** removed `@google/genai` dependency + `MAJOR_CAPABILITY_SERVER_SIDE_GEMINI_API`
  from `metadata.json` (both AI-Studio auto-added, **verified zero usage in `src/`**). Also removed
  unused server cruft (`express`, `dotenv`) and the Gemini boilerplate in `.env.example`.
- **Deploy prep:** `package.json` name `react-example` → `early-literacy`; moved build tools
  (`tailwindcss`, `typescript`) into `dependencies` (Cloudflare `NODE_ENV=production` gotcha, learned
  on iKhaya); added `public/_redirects` (SPA) + `wrangler.toml` (output `dist`); committed lockfile.
- **New complete README** written to speak to the app (village, journey, companions, principles).
- **Verified:** `npm install` (0 vuln), `tsc --noEmit` (0 errors), `vite build` → `dist/`. Live URL
  serves title "The People's Home • Early Literacy Village"; no Gemini/genai/API refs in served HTML.
- **Brain updated:** `apps/early-literacy.md` (LIVE + governance deviation #1/#4 resolved),
  `CURRENT_STATE.md`, `PROJECT_TIMELINE.md`, `ECOSYSTEM.md`, `ROADMAP.md`, engine cross-ref.

### Cloudflare settings used
Framework: None/Vite · Build: `npm run build` · Output: `dist` · **no env vars**. URL kept the bare
name (`early-literacy.pages.dev` — not suffixed).

### Next steps (in order)
1. **Offline-PWA hardening** — add `vite-plugin-pwa` (service worker + unique manifest `id`), verify
   cold-load offline. This is the one real gap vs. the World-A definition of done. *(Recommended next.)*
2. **Add a live card** for Early Literacy on peoples-home-web once PWA-verified.
3. **Founder decision:** "TPH Core" naming reconciliation (rename app engine set, or fold into `@tph/core`).
4. **Phase 4.5** — build when directed.
5. 🔴 Keystore backup still outstanding (carried from session 11).

---

## ✅ 2026-07-02 (session 15) — Early Literacy integrated into The People's Home (no app code changed)

**Nature:** Ecosystem **integration**, not app development. The Early Literacy app was built
externally (Google AI Studio / Gemini); this session integrated it into the single Brain,
registries, architecture, and governance. **No application code was modified.**

**App repo:** `SifisoScS/early-literacy` (PRIVATE, personal account) —
local checkout `C:\Users\sifis\Next-Level-Projects\early-literacy` (cloned this session).
**Brain repo:** `peoples-home` (this repo). **Not committed/pushed** — left staged for review.

### What the app is (verified from source)
- "Early Literacy Village", ages 3–7, Foundations slot **#4** (was "Early Literacy Games" 🔮 Future).
- React 19 · Vite 6 · Tailwind v4 · `motion` · `lucide-react`. Offline; `localStorage` only.
- Curriculum **Phases 1–4 complete** (Listening → Sound Discovery → Letter Garden → First Words)
  across 8 module screens; **navigation framework complete**; **Phase 4.5 planned**.
- Consumes 6 platform engines via a type-safe **Event Bus** — **none modified**. Adds 2 app-layer
  engines: **WordEngine** + **ReadingJourneyEngine** (correctly *not* platform).

### Integration Report — files created / updated (all in `peoples-home/brain` unless noted)
**Created:**
- `apps/early-literacy.md` — full app memory (mission, journey, engines, nav/offline/accessibility
  models, governance review, architecture audit, roadmap).
- `patterns/world-a-navigation.md` — the navigation standard (reusable by Early Numeracy, Science
  Sprouts, Our World, ReadAfrica).
- `architecture/04-early-literacy-integration.md` — how it consumes the platform without modifying
  it; the app-engine pattern; the "TPH Core" naming-collision writeup.

**Updated:**
- `CURRENT_STATE.md` (as-of → 2026-07-02; new Foundations on-ramp table with Early Literacy + Early Numeracy)
- `PROJECT_TIMELINE.md` (Early July 2026 section)
- `apps/README.md` + `architecture/01-capability-architecture.md` (slot #4 status → 🔧 Built)
- `patterns/README.md` (index row)
- Operational: `../ECOSYSTEM.md`, `../ROADMAP.md` (registry rows)
- Engine cross-ref (other repo): `repository-engine-1000/docs/peoples-home/TPH_REGISTRY.md` + `PEOPLE'S_HOME.md`

### Governance findings (documented, NOT silently changed — per the integration mandate)
1. ⚠️ **Unused cloud AI capability.** `metadata.json` declares `MAJOR_CAPABILITY_SERVER_SIDE_GEMINI_API`
   and `package.json` depends on `@google/genai`, but **zero AI calls exist in `src/`**. Honours
   Principle 17 (wired, not activated) in practice; recommend dropping the unused capability + dep.
2. ⚠️ **"TPH Core" naming collision.** The app's frozen "TPH Core v1.0" engine runtime is a *different*
   thing from the canonical (unfrozen, mid-extraction) TPH Core SDK. Reconcile: rename the app runtime
   or fold it into `@tph/core`. Founder decision required.
3. ⚠️ **Repo under personal `SifisoScS`**, not the org — migrate on publish.
4. **`package.json` name** is placeholder `"react-example"` — cosmetic; fix before publish.
   (Repo confirmed PRIVATE — Principle 12 satisfied.)

### Next steps (in order)
1. **Founder decision** on the "TPH Core" naming reconciliation (blocks a clean platform story).
2. **Deploy** Early Literacy to Cloudflare Pages (unique manifest `id`, offline-verify), then flip a card on the site.
3. Drop the unused `@google/genai` dependency + Gemini capability; fix `package.json` name; migrate repo to the org.
4. **Phase 4.5** — build when the founder directs.
5. Commit the Brain changes to `peoples-home` when approved (this session left them uncommitted).
6. 🔴 Keystore backup still outstanding (carried from session 11).

---

## ✅ 2026-06-30 (session 14c) — Early Numeracy Phase 1 BUILT

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-numeracy` (private) — `master`

**Commit:** `554654f` | **GitHub:** github.com/ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-numeracy

**Cloudflare Pages:** Connect repo manually → Build command: `npm run build` → Output: `dist/`

---

### What was built

Complete Phase 1 shell. All criteria met:
- ✅ Vite + React + TypeScript + Tailwind v4 scaffold
- ✅ VitePWA: offline-first, service worker, 225KB precached shell
- ✅ Home screen with 5 colourful module cards (64×64px min touch targets, no reading required)
- ✅ useNarration hook (Web Speech API, voice-quality guard, ported + adapted from Math Adventure RPG)
- ✅ useInstruction: **architecturally separated audio/visual paths** — visual channel is stubs but exists in code from Phase 1 so Phase 5+ can fill it without refactoring
- ✅ useSessionState: persists to localStorage, restores on `visibilitychange` (child returns from background)
- ✅ useChildLock: long-press 3s corner → fullscreen; long-press lock icon → unlock
- ✅ ModulePlaceholder: warm coming-soon screen per module, speaks on mount
- ✅ All 5 modules lazy-loaded (0.24KB per chunk)
- ✅ No backend · No accounts · No tracking · No ads

### File structure

```
early-numeracy/
├── src/
│   ├── types/index.ts              — ModuleId, SessionState, InstructionMode, Screen
│   ├── constants/modules.ts        — MODULES array with colors, icons, names
│   ├── constants/narration.ts      — Full audio script (24 transfer prompts, all module lines)
│   ├── hooks/useNarration.ts       — Web Speech API wrapper
│   ├── hooks/useInstruction.ts     — Audio/visual separated instruction system
│   ├── hooks/useSessionState.ts    — Persist + restore on visibilitychange
│   ├── hooks/useChildLock.ts       — Long-press lock/unlock
│   ├── components/HomeScreen.tsx   — 5 card grid + top bar
│   ├── components/ModuleCard.tsx   — Individual card (press feedback, visited dot)
│   ├── components/ModulePlaceholder.tsx — Coming-soon screen
│   └── modules/*/                  — 5 module stubs (all lazy-loaded)
```

### Phase 1 done-when verified
- App builds cleanly: `npm run build` → 225KB precache
- TypeScript: `npx tsc --noEmit` → zero errors
- 5 module cards render on home screen
- Module placeholder screens show per-module colour + icon + coming-soon message
- State persists to localStorage; restores on visibilitychange
- Service worker generated; app shell is offline-capable

### What is next
- **Deploy to Cloudflare Pages:** go to pages.cloudflare.com → Connect to Git → select `early-numeracy` → Build: `npm run build` → Output: `dist`
- **Play-test Phase 1** with 2 children aged 3–4 before marking done (blueprint requirement)
- **Phase 2** (when directed): Counting Garden + Which is More? — real gameplay

---

## ✅ 2026-06-30 (session 14b) — Early Numeracy blueprint v2 — 7 gaps + constitutional rule

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/peoples-home-web` — `main`

**File:** `brain/apps/early-numeracy.md` (Blueprint v2)

---

### What was done

Designed and finalized the full Early Numeracy blueprint. The founder reviewed Blueprint v1
and identified 7 gaps and 1 constitutional rule. All were incorporated into the file with
two founder refinements:

1. Audio: architectural (lazy-loading + caching + language packs) — no hard file-size budgets
2. Child-lock: specified as goals, not guarantees — PWA fullscreen varies across devices

**7 gaps added as new sections:**

| # | Section | Core principle |
|---|---|---|
| 1 | First-time instruction protocol | ≤8s animated demo, question-mark replay, 8s idle prompt, full audio script spec |
| 2 | Correction patterns | Per-module: warm/calm, never "Wrong", child stays in control |
| 3 | Motor accessibility | Tap-to-select-then-tap-to-place alternative for every drag, 1.5× drop tolerance |
| 4 | Audio architecture | Lazy-load by module, service worker cache, modular language packs, Opus+MP3 |
| 5 | Visual-instruction mode | Parent toggle (ear icon), audio/visual logic separated in code from Phase 1 |
| 6 | Keeping children in the experience | Long-press child-lock, visibilitychange state restore, test on 3 SA devices |
| 7 | Play-testing protocol | Play-test gate required before any phase is marked complete |

**Constitutional rule added:** "Real-world transfer" — every session ends with a spoken
"Try this at home" prompt over an illustration. 20+ prompt pool. Technology starts the
learning; reality completes it.

---

**What is next for Early Numeracy:**
- Begin Phase 1 (shell) only when founder directs
- Write full audio script before any voice recording
- Play-test Phase 1 with 2 children aged 3–4 before marking it done

---

## ✅ 2026-06-30 (session 14) — Capability Pillars redesign — working JS-rendered cards

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/peoples-home-web` — `main`

**Commit:** `8affbba`

---

### What was done

Redesigned the Capability Pillars section of `index.html` to match the TanStack Start app reference screenshots:
- **Compact 3-column card grid** — each card has a circular coloured icon, pastel blob top-right, capability chips, and a live-experience count
- **Click-to-detail panel** — clicking a card hides the grid and shows a full detail view: pillar hero with icon and chips, app list with Live/Coming soon badges, "Other capability pillars" navigation buttons
- **All 6 pillars live** with correct app links per the BLUEPRINT

### Technical approach (what works)

The grid is **empty in HTML** (`<div class="pillar-grid" id="pillar-grid"></div>`) and populated entirely by JS:

- `renderGrid()` — builds all card HTML via string concatenation, injects into `#pillar-grid`, sets `display:grid`. Called once on page load, and again when the user clicks "← All capabilities".
- `showPillar(id)` — hides the grid, populates `#pillar-detail` with the full detail panel, scrolls to the section.
- `mkChips(chips, cls)`, `mkApps(apps)`, `mkOthers(others)` — string concat helpers.
- `PILLARS` array: `status:'live'|'future'` (not `live:true/false`), `icon` as HTML entity strings, `color` and `blob` as inline style values.

**Key lesson — what killed earlier attempts:**
- Nested template literals inside `<script>` tags cause silent parse failures in some browsers — use `var`/`for`/string concatenation throughout.
- `color-mix()` was removed from the pillars section entirely — replaced with direct `rgba()` and named hex values. The blueprint section still uses `color-mix()` with `--accent` safely.
- Static HTML cards (ecc7c58 attempt) introduced a different problem — the working version keeps cards JS-rendered.

### CSS classes added (in `<style>` block)

`.pillar-grid`, `.pc`, `.pc-blob`, `.pc-arrow`, `.pc-head`, `.pc-ico`, `.pc-text`, `.pc-chips`, `.pc-chip`, `.pc-count`
`.pd`, `.pd-back`, `.pd-hero`, `.pd-hero-blob`, `.pd-kicker`, `.pd-hero-row`, `.pd-hero-ico`, `.pd-hero-title`, `.pd-hero-chips`, `.pd-hero-chip`, `.pd-apps-hd`, `.pd-apps`, `.pd-app`, `.pd-status`, `.pd-others`, `.pd-others-list`, `.pd-other`, `.pd-other-dot`

---

**What is next for peoples-home-web:**
- Real `index.html` URL to verify Cloudflare Pages deployment renders cards correctly
- Save "Landing Page Architecture" document to `brain/platform/peoples-home-web.md`
- Three unreconciled v2 apps still need architecture decision (Everyday Foundations, Our World, The Golden Hand)
- Opportunity Hub definition — plan file exists at `C:\Users\sifis\.claude\plans\as-i-am-building-unified-dove.md`

---

## ✅ 2026-06-29 (session 13) — iKhaya scroll clipping fix + end-of-list indicator

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/ikhaya` — `main`, deployed to ikhaya.pages.dev.

**Commits this session:** `200bf48` → `160f83e`

---

### 1. Scroll clipping — last card half-visible (`200bf48`)

**Bug:** When a short list of cards (e.g. 4 results) was shown, the bottom half of the last card was cut off by the fixed bottom nav.

**Root cause:** After the sidebar refactor (`67d0d80`) `.app-main-area` was a plain `div` with no CSS on mobile. This meant `main.app-content { flex: 1 }` (which used to expand the content area to fill the full viewport) was silently ignored — its parent was no longer a flex container. The content area shrank to its natural height and the fixed bottom nav overlapped the tail of the list.

**Fix — two changes in `src/index.css`:**

1. Added `.app-main-area` base rule (applied on all screen sizes):
   ```css
   .app-main-area {
     flex: 1;
     display: flex;
     flex-direction: column;
     min-width: 0;
   }
   ```
   This restores the mobile behaviour that existed before the sidebar wrapper was introduced.

2. Replaced the desktop block with the **two-panel independent-scroll pattern**:
   ```css
   @media (min-width: 768px) {
     .app-shell   { flex-direction: row; height: 100dvh; overflow: hidden; }
     .app-sidebar { height: 100%; overflow-y: auto; /* no more position:sticky */ }
     .app-main-area { overflow-y: auto; }
   }
   ```
   Shell is now a fixed viewport box; sidebar and main area each own their own scroll. Sidebar never needs `position: sticky` — it simply fills the fixed parent.

3. Mobile bottom padding raised to `calc(5rem + env(safe-area-inset-bottom, 0px))` — covers iPhone home indicator (34px safe-area was eating into the 5rem = 80px gutter).

---

### 2. End-of-list indicator — never showed with small result sets (`160f83e`)

**Bug:** "You've seen all N results" only appeared when `visible.length > PAGE_SIZE (20)`. With 24 seed items and no filters, the first 20 show and the "Load more" button appears — but once the user clicked it and saw all 24, the end message showed (correct). With **any filter** that reduced results below 20, neither the Load-more button nor the end message appeared — the list ended in silence.

**Fix in `src/pages/DiscoverPage.tsx`:**
```tsx
// Before — only fires when visible > 20:
{remaining <= 0 && visible.length > PAGE_SIZE && (
  <p className="results-end">You've seen all {results.length} results</p>
)}

// After — fires whenever there is nothing left to load:
{remaining <= 0 && (
  <p className="results-end">
    {results.length === 1
      ? 'Showing the only result'
      : `You've seen all ${results.length} results`}
  </p>
)}
```
Users now always see a clear "done" signal at the bottom of the list, regardless of how many results the filter returned.

---

**What is next for iKhaya:**
- Real opportunity data (replace seed data with live sources)
- Replace aspirational stats (100K+, 25K+, 2K+) with real numbers before beta
- Notifications page (`/notifications`) — currently a banner only, not a page
- `ADMIN_PHONE_NUMBER` still needs to be set in Railway (Kilimanjaro — from session 11)
- Keystore backup still needs to be copied to Google Drive (from session 11)

---

## ✅ 2026-06-29 (session 12) — iKhaya landing page, hub pages, full retheme, responsive nav

**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/ikhaya` — all changes on `main`, deployed to ikhaya.pages.dev via Cloudflare Pages.

**Commits this session (in order):**
`9c20c39` → `ae48a24` → `af627ad` → `225e4b5` → `b13a7f2` → `3afb719` → `aa535ed` → `581adff` → `67d0d80`

---

### 1. Marketing landing page (`9c20c39`)

`/` now shows a full marketing front door; the app moved to `/discover` and below.

- `src/pages/LandingPage.tsx` — dark hero, search bar (hands off `?q=` and `?type=` to DiscoverPage), 6 hub cards, stats band, values section, footer. All SVGs inline.
- `src/styles/landing.css` — fully scoped under `.landing`, cream/green theme, responsive at 960px and 600px.
- `App.tsx` — `isLanding` guard; `app-content-full` for landing; DiscoverPage moved to `/discover`.
- `DiscoverPage.tsx` — reads `?q=` and `?type=` URL params to seed initial filters.

**Stats note:** `100K+` / `25K+` / `2K+` are aspirational placeholders — replace with real numbers before public beta.

---

### 2. Navigation fixes (`ae48a24`, `af627ad`, `225e4b5`)

- Added **app header** (iKhaya logo → `/`) on all app pages; hidden on desktop where sidebar takes over.
- Removed explicit `← Back` buttons from detail pages — back handled by browser gesture, bottom nav, and app header.
- **Bug fixed:** `ApplicationWorkspacePage` error state was calling `navigate('/')` (landing) — fixed to `navigate('/discover')`.
- **Fixed stuck pages:** `isDetail` was hiding the bottom nav on opportunity/workspace pages. Changed bottom nav gate from `!isDetail` → `!isLanding` so nav is always visible inside the app.

---

### 3. Hub pages (6 routes) + pathway section removed (`b13a7f2`)

- Removed "Discover opportunities across 6 pathways" section and all chip/icon code.
- Hub cards now navigate to their own routes (was all going to `/discover`).
- Created 5 new hub pages using shared `HubPlaceholderPage` component:
  - `/learning` → Learning Hub (courses, learnerships, TVET, skills dev)
  - `/skills` → Skills Passport (digital record, certs, portfolio, sharing)
  - `/funding` → Funding Hub (bursaries, NYDA/DTI grants, SETA, guides)
  - `/career` → Career Hub (paths, CV builder, interview prep, mentorship)
  - `/entrepreneurship` → Entrepreneurship Hub (CIPC, incubators, NYDA, coaching)
- All pages show "Coming Soon" badge, 4 feature items, link to Opportunity Hub.

---

### 4. Full app retheme — dark → warm cream/green (`3afb719`, `aa535ed`)

Entire app palette replaced to match the landing page. No more developer dark theme.

| Token | Before | After |
|---|---|---|
| `--bg` | `#0f0f1a` dark | `#f2efe6` cream |
| `--surface` | `#1a1a2e` navy | `#ffffff` white |
| `--accent` | `#7c5cbf` purple | `#5ba12f` People's Home green |
| `--text` | `#e8e8f0` near-white | `#15211c` dark ink |

App header and bottom nav background changed from `--surface` (white) to `--surface-2` (`#ebe7da`) to match the sync bar — unified warm band at top and bottom.

All 8 hardcoded dark hex values (badge backgrounds, checklist gathered, etc.) updated to light equivalents.

---

### 5. Load-more pagination on Discover page (`581adff`)

`PAGE_SIZE = 20`. Shows first 20 results; "Load more — N remaining" button appends next 20. Filters reset to page 1 automatically. "You've seen all N results" end message. Full filtered count always shown in results-count.

---

### 6. Sidebar (desktop) + bottom bar (mobile) responsive nav (`67d0d80`)

- `src/components/AppSidebar.tsx` — sticky 220px left column on desktop (≥768px), hidden on mobile.
  - **Hubs:** 🔍 Opportunity Hub (Live badge) · 📚 Learning · 🛡️ Skills · 💰 Funding · 💼 Career · 🚀 Entrepreneurship
  - **My iKhaya:** 📋 My Applications (urgent red badge) · 👤 My Profile
  - iKhaya brand at top links to landing page `/`.
- **Mobile (< 768px):** bottom bar with Discover · My Applications · My Profile. App header shows iKhaya logo.
- **Desktop (≥ 768px):** sidebar visible; app-header and bottom-nav hidden via CSS.
- `App.tsx` restructured: sidebar outside, everything else in `.app-main-area`.

---

**What is next for iKhaya:**
- Real opportunity data (replace seed data with live sources)
- Replace aspirational stats (100K+, 25K+, 2K+) with real numbers before beta
- Notifications page (`/notifications`) — currently a banner only, not a page
- `ADMIN_PHONE_NUMBER` still needs to be set in Railway (Kilimanjaro — from session 11)
- Keystore backup still needs to be copied to Google Drive (from session 11)

---

## ✅ 2026-06-28 (session 11) — Keystore backup + Science Sprouts signing config

**Done this session:**

### 1. Keystore backup bundle created

Both Google Play upload keystores are now bundled and ready for off-machine storage.

**Backup location (LOCAL — must be moved off-machine):**
```
C:\Users\sifis\Desktop\TPH-KEYSTORES-BACKUP-2026-06-28\
```

**Contents:**
| File | App | Alias |
|---|---|---|
| `math-adventure-rpg--upload-new.jks` | Math Adventure RPG | `upload` |
| `math-adventure-rpg--keystore.properties` | Math Adventure RPG | — |
| `science-sprouts--upload.jks` | Science Sprouts | `upload` |
| `README.txt` | Instructions + alias info (no passwords) | — |

**Password:** same for both apps — stored in your password manager under `TPH Android Keystores`.

**🔴 OUTSTANDING ACTION:** Copy `TPH-KEYSTORES-BACKUP-2026-06-28/` to Google Drive
(private folder) + a second off-machine location. This is the only thing not yet done.
Once copied, the keystore 🔴 is fully resolved.

### 2. Science Sprouts — signing config added (commit `e4176ae`)

Science Sprouts had no `keystore.properties` and no signing config in `build.gradle`.
Release builds were unsigned. Fixed to match Math Adventure RPG exactly.

**Files changed:**
- `android/app/science-sprouts-upload.jks` — keystore copied into `android/app/`
  (was at project root; now consistent with MA layout; gitignored)
- `android/keystore.properties` — created (gitignored): storeFile, storePassword,
  keyAlias=`upload`, keyPassword
- `android/app/build.gradle` — added keystoreProps loader + `signingConfigs.release`
  block; enabled `minifyEnabled true` + `shrinkResources true` (was `false`)
- `android/.gitignore` — uncommented `*.jks` / `*.keystore`; added `keystore.properties`
  rule (was commented out — risked accidental commit of secrets)

**Result:** `gradle assembleRelease` / `bundleRelease` now produces a properly signed
AAB on the dev machine without any credentials in source control.

**Note:** the original `science-sprouts-upload.jks` at the project root is still there
but can be deleted — the active copy is now in `android/app/`.

**Next steps:**
1. 🔴 Copy keystore backup to Google Drive (5 minutes)
2. Add `TPH Android Keystores` entry to password manager with the shared password
3. Wait for ChatGPT brief on Wave 12 planning

---

## ✅ 2026-06-28 (session 10) — Founding story locked + AI principle established

**Done this session:**

### 1. The People's Home origin story captured (brain/history/HISTORY.md)

The founding moment had never been written down. It is now:

- Sifiso built **Math Adventure RPG** and published it to Google Play Store — the first app.
- While building **Science Sprouts**, two things crystallised:
  1. Google Play has policies that contradict the core belief — the store controls distribution,
     can delist, and gatekeeps the relationship between builder and learner.
  2. The vision was bigger than "publishing apps." It needed to be a *home* — for the apps
     and for the people — where they learn, build, and achieve.
- **Science Sprouts** became the last app ever published to Google Play.
- **The People's Home** was founded — not as a technical decision, but as a values decision.

**Founder verbatim (2026-06-28):**
> *"I wanted to build a home for my apps and the people — where they'll learn, build, and achieve."*

This is the lived expression of the one belief: *"Technology should empower society — not gatekeep it."*
Google was gatekeeping. The People's Home was the answer.

### 2. AI principle: Wire AI, don't activate it (PROJECT_DNA.md — Principle 17)

The tension: #FreeForever means learners never pay. AI API calls cost money per learner per use.
At scale, per-learner AI runtime cost is unsustainable without charging someone — and that someone
cannot be the learner.

**The rule (now Principle 17 in PROJECT_DNA.md):**
- **AI builds the product** → ✅ acceptable. One-time build cost per feature (Claude Code,
  ChatGPT planning). Falls on the builder, not the learner.
- **AI runs the product for learners** → ❌ wired, not activated. Scales with users.
  #FreeForever cannot survive per-learner API cost at scale without a funding model.

**What "wired not activated" means in practice:**
- iKhaya Phase 9 built the full AI matching architecture: consent page, Cloudflare proxy,
  two-tier intelligence engine. All of it is there. None of it is running.
- `ANTHROPIC_API_KEY` stays unset. The local tag-matching tier (zero API cost) IS the
  #FreeForever product. AI ranking is the upgrade path for when economics allow.

**Three conditions required before any AI tier activates in production:**
1. A funding model covers the per-call cost without charging learners
2. The feature degrades gracefully to the free local alternative if funding ends
3. The decision is logged in DECISIONS.md with the funding model documented

### 3. Brain files updated

| File | Change |
|---|---|
| `brain/history/HISTORY.md` | New "Origins" section at the top — the founding moment |
| `brain/decisions/DECISIONS.md` | D-11 (founding decision) + D-12 (wire AI, don't activate) |
| `brain/PROJECT_DNA.md` | Principle 17 appended — Wire AI, Don't Activate It |
| `brain/SESSION_HANDOFF.md` | This entry |

**Commit:** `e9069f2` → `peoples-home-web` main

**No code was written this session. All work was institutional memory.**

**Next steps:**
- Wait for ChatGPT brief on Wave 12 planning
- 🔴 Keystore backup still outstanding (`upload-new.jks` — local-only, unrecoverable)
- Set `ANTHROPIC_API_KEY` in Cloudflare only when a funding model is in place (see Principle 17)

---

## ✅ 2026-06-28 (session 9) — iKhaya Phase 10 (Production Hardening)

**Done this session:**

- **Phase 10 — Production Hardening (commit `22f0da9`):**

  **Security headers (`public/_headers`):**
  - `X-Frame-Options: DENY` — clickjacking protection
  - `X-Content-Type-Options: nosniff` — MIME sniffing protection
  - `Referrer-Policy: strict-origin-when-cross-origin`
  - `Permissions-Policy: camera=(), microphone=(), geolocation=(), payment=()`
  - CSP: `default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'`
    (unsafe-inline in style-src is an accepted trade-off for React inline styles)
  - `/api/*` gets `Cache-Control: no-store` to prevent caching of sync/AI endpoints

  **Error handling:**
  - `src/components/ErrorBoundary.tsx` — class component wrapping the whole app AND the
    inner route tree. Shows a safe fallback UI; error detail only in DEV mode.
  - `src/pages/NotFoundPage.tsx` — 404 page for the wildcard `*` route.

  **Performance — lazy loading:**
  - All 7 pages (`DiscoverPage`, `OpportunityDetailPage`, `ApplicationWorkspacePage`,
    `ApplicationsPage`, `ProfilePage`, `ConsentPage`, `NotFoundPage`) wrapped in
    `React.lazy()` + `<Suspense fallback={<PageLoader />}>`.
  - Initial JS bundle: 318 kB → 265 kB (−16.7%). Pages load on demand.

  **Connectivity (`src/hooks/useOnlineStatus.ts`):**
  - `useOnlineStatus()` tracks `navigator.onLine` reactively via window events.
  - SyncStatus updated: shows 📴 offline state; refresh button disabled when offline.
  - App skips auto-sync when offline.

  **Service worker (`vite.config.ts`):**
  - `navigateFallback: '/index.html'` — SPA routing works offline.
  - `navigateFallbackDenylist: [/^\/api\//]` — API routes never served from SW cache.

  **POPIA rights (`src/pages/ProfilePage.tsx` + `src/storage/db.ts`):**
  - `exportAllData()` — collects profile, applications, saved opportunities, notification
    prefs, AI consent → JSON download as `ikhaya-my-data-YYYY-MM-DD.json`.
    Excludes opportunity records (public server data) and sync record (app metadata).
  - `clearAllData()` — clears all 5 user-specific IndexedDB stores. App still works after
    (opportunity records remain). Implements POPIA Section 24 right to erasure.
  - "📥 Download my data" + "🗑 Delete all my data" buttons added to Profile.

  **POPIA documentation:**
  - `docs/popia-privacy-notice.md` — plain-language notice covering what data, where stored,
    third parties (Anthropic, Cloudflare), children, all 5 POPIA rights.
  - `docs/dpia.md` — full Data Protection Impact Assessment. Data flow diagrams, 7 risks
    assessed. 2 residual risks accepted (shared device, under-18 consent gap).
  - `docs/security-review-report.md` — 22-domain security review. 0 Critical, 0 High,
    5 Medium risks (all accepted for MVP, documented with resolution targets).

  **Build result:** 49 modules, 265 kB initial JS (−16.7%), 16 precached assets, 0 TS errors.

**iKhaya Opportunity Hub — ALL 10 PHASES COMPLETE. 🎉**

```
Phase 1  ✅  Vision & Brain (locked in peoples-home brain)
Phase 2  ✅  Domain model (Opportunity, UserProfile, Application types)
Phase 3  ✅  UX & navigation (bottom nav, PWA shell, 4 pages)
Phase 4  ✅  Offline-first foundation (service worker, IndexedDB, seed data)
Phase 5  ✅  Opportunity discovery engine (search, filter, browse)
Phase 6  ✅  Eligibility engine (profile matching)
Phase 7  ✅  Application workspace (CV builder, motivation letter, document checklist)
Phase 8  ✅  Synchronisation layer + Notification Engine
Phase 9  ✅  Opportunity Intelligence Engine (local tag scoring + Claude AI ranking)
Phase 10 ✅  Production Hardening (security headers, error boundary, lazy loading, POPIA)
```

**Pre-public-launch items (from security-review-report.md):**
1. Set `ANTHROPIC_API_KEY` in Cloudflare Pages → activate AI ranking
2. Add Cloudflare rate limiting to `/api/ai-match` (max 10 req/IP/hour)
3. Run `npm audit` and fix any High/Critical findings
4. Encrypt IndexedDB using Web Crypto API
5. Write formal incident response plan (72h POPIA breach notification)
6. Implement parental consent flow for under-18 learners (if school-facing)

**🔴 URGENT — Keystore backup:** `upload-new.jks` is local-only. Unrecoverable if lost.

**Files changed (Phase 10):**
- `ikhaya/public/_headers` — security headers (new)
- `ikhaya/src/components/ErrorBoundary.tsx` — new
- `ikhaya/src/components/SyncStatus.tsx` — `isOnline` prop + offline state
- `ikhaya/src/hooks/useOnlineStatus.ts` — new
- `ikhaya/src/pages/NotFoundPage.tsx` — new
- `ikhaya/src/pages/ProfilePage.tsx` — data export + delete rights
- `ikhaya/src/storage/db.ts` — `exportAllData()` + `clearAllData()`
- `ikhaya/src/App.tsx` — full rewrite: lazy pages, double ErrorBoundary, useOnlineStatus
- `ikhaya/src/index.css` — focus rings, error boundary page styles
- `ikhaya/vite.config.ts` — navigateFallback + denylist
- `ikhaya/docs/popia-privacy-notice.md` — new
- `ikhaya/docs/dpia.md` — new
- `ikhaya/docs/security-review-report.md` — new

**Next steps:**
1. Set `ANTHROPIC_API_KEY` in Cloudflare → ikhaya → Settings → Environment variables
2. Wait for ChatGPT brief on next wave (Wave 12 planning)
3. Keystore backup 🔴
4. TPH Core SDK extraction from ReadAfrica → `@tph/core` (when directed)

---

## ✅ 2026-06-28 (session 8) — iKhaya Phase 9 (Opportunity Intelligence Engine)

**Done this session:**

- **Phase 9 — Opportunity Intelligence Engine (commit `79e4efa`):**

  **Two-tier matching architecture:**

  *Tier 1 — Local (offline, instant, no consent needed):*
  - `src/engines/localMatcher.ts` — pure scoring (0–100): interest type match (30 pts),
    capability tag overlap (40 pts), province availability (15 pts), basic eligibility (15 pts).
    Min score 20 to appear. Zero network calls. Works offline.
  - `src/engines/intelligenceEngine.ts` — orchestrator. `getLocalRecommendations()` = offline,
    instant. `getAIRecommendations()` = async, consent-gated, returns null on any failure
    (graceful fallback to local).

  *Tier 2 — AI-enhanced (Claude, opt-in, requires connectivity):*
  - `functions/api/ai-match.ts` — Cloudflare Pages Function at `POST /api/ai-match`.
    Server-side proxy to Claude Haiku (fast, cheap, structured JSON). Receives anonymised
    profile + ≤10 candidates; returns ranked JSON with match explanations and strengthen tips.
    Returns 503 if `ANTHROPIC_API_KEY` not configured. API key NEVER reaches the client.
  - `src/services/aiMatchingService.ts` — client calls `/api/ai-match`; returns null on any
    error (offline, 503, timeout, JSON parse).

  *POPIA-compliant consent:*
  - `src/pages/ConsentPage.tsx` — `/consent` route. Full disclosure of what data is sent
    (interests, capability tags, age, province, qualification — NO name/ID/contact).
    Explicit two-button opt-in. Consent stored in IndexedDB.
  - DB version 1→2: `aiConsent` store added with upgrade path for existing users.
  - `getAIConsent()` / `setAIConsent()` in `db.ts`.
  - AI is NEVER called without explicit consent. Revocable at any time in Profile.

  *UI:*
  - `src/components/RecommendationsPanel.tsx` — "✨ For You" section above search bar
    on DiscoverPage. Shows top 5 local recommendations. "🤖 AI rank" button triggers AI
    (navigates to /consent first if needed). Collapsible. AI results show AI badge. "↩ Local"
    to revert.
  - `src/components/MatchExplanation.tsx` — match badge (Strong/Good/Some + score), local
    reasons as chips, AI explanation text, strengthen tip.
  - `src/pages/DiscoverPage.tsx` — RecommendationsPanel injected above search when
    profile has interests/capability tags.
  - `src/pages/ProfilePage.tsx` — "AI Matching" toggle section to enable/revoke consent.
  - `src/App.tsx` — `/consent` route added; consent page hides bottom nav.
  - `src/index.css` — Phase 9 styles (~200 lines added).
  - `src/types/opportunity.ts` — MatchScore, AIMatchResult, AIConsentRecord interfaces.
  - Build: 46 modules, 318 kB JS, 20.6 kB CSS. 0 TypeScript errors.

**To activate AI ranking on Cloudflare Pages:**
Go to Pages → ikhaya → Settings → Environment variables → Production
Add: `ANTHROPIC_API_KEY = sk-ant-...`
Local matching works immediately with no configuration.

**State of ongoing work:**
- Phase 9 complete and deployed (commit `79e4efa` → Cloudflare Pages).
- Local matching works for anyone with interests set in Profile.
- AI ranking ready but dormant until `ANTHROPIC_API_KEY` is set in Cloudflare.

**Next steps (in order):**
1. **Set `ANTHROPIC_API_KEY` in Cloudflare Pages** to activate AI ranking
2. **Phase 10 — Production hardening** (POPIA review, security review, auth if needed)
   - Replace static `/api/opportunities.json` with a real backend endpoint
   - Service worker caching review (ensure API routes not inadvertently cached)
   - Full security review per `brain/SECURITY_CONSTITUTION.md`
3. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. Unrecoverable if lost.

**Files changed:**
- `ikhaya/functions/api/ai-match.ts` — new Cloudflare Pages Function
- `ikhaya/src/engines/localMatcher.ts` — new
- `ikhaya/src/engines/intelligenceEngine.ts` — new
- `ikhaya/src/services/aiMatchingService.ts` — new
- `ikhaya/src/components/RecommendationsPanel.tsx` — new
- `ikhaya/src/components/MatchExplanation.tsx` — new
- `ikhaya/src/pages/ConsentPage.tsx` — new
- `ikhaya/src/types/opportunity.ts` — MatchScore, AIMatchResult, AIConsentRecord added
- `ikhaya/src/storage/db.ts` — DB v2, aiConsent store, getAIConsent/setAIConsent
- `ikhaya/src/pages/DiscoverPage.tsx` — RecommendationsPanel injected
- `ikhaya/src/pages/ProfilePage.tsx` — AI Matching consent toggle added
- `ikhaya/src/App.tsx` — /consent route + isDetail update
- `ikhaya/src/index.css` — Phase 9 styles

---

## ✅ 2026-06-28 (session 7) — iKhaya Phase 8 (Synchronisation Layer + Notification Engine)

**Done this session:**

- **Phase 8 — Synchronisation Layer (commit `1ec4edb`):**
  - `public/api/opportunities.json` — static "API" payload (all 25 seed opportunities).
    Served by Cloudflare Pages at `/api/opportunities.json`. When Phase 10 adds a real
    backend, only `SYNC_URL` in `opportunitySync.ts` changes.
  - `src/sync/opportunitySync.ts` — `fetchRemoteOpportunities()` fetches the JSON with
    a 10s timeout, returns null on any network failure (never throws)
  - `src/sync/syncManager.ts` — `checkAndSync()` (24h gate, fires on app open) and
    `performSync()` (force, called on manual refresh). Merges remote data into IndexedDB.
    Server is authoritative for opportunity records; local is authoritative for applications.
    Updates SyncRecord (idle / syncing / error). Detects new opportunities since last sync.
  - `src/engines/notificationEngine.ts` — `getActiveNotifications()` generates in-app
    deadline alerts from local data only. Critical (<48h), urgent (<N days from prefs, default 7).
    Filters by notification type preferences. No PII leaves the device. Push notifications
    deferred to Phase 10 (requires backend auth).
  - `src/components/SyncStatus.tsx` — replaces old static SyncBanner. Shows relative
    "last updated" time ("just now", "3h ago", "yesterday"), spinning ⟳ while syncing,
    manual 🔄 refresh button, "+N new" badge when new opportunities arrive
  - `src/components/NotificationBanner.tsx` — dismissible deadline alert stack
    (critical = red left-border, urgent = amber). Only shown on list/discover screens,
    hidden inside detail/workspace views.
  - `src/App.tsx` — wired: seed → stamp SyncRecord → load notifications →
    background checkAndSync on mount; manual refresh via handleRefresh(); urgent
    notification badge (red dot) on My Applications nav tab
  - `src/pages/ProfilePage.tsx` — new "🔔 Alert Preferences" section: toggle for
    new-opportunity alerts, range slider for closing-soon window (1–30 days),
    per-type chip filter
  - `src/storage/db.ts` — added `getNotificationPrefs()` and `saveNotificationPrefs()`
    (uses existing `notificationPrefs` store; no DB version bump needed)
  - `src/index.css` — Phase 8 styles: `.sync-banner-left`, `.sync-spinner`,
    `.sync-new-badge`, `.sync-refresh-btn`, `.notification-panel`, `.notification-item`
    (critical/urgent/info variants), `.notification-dismiss`, `.nav-badge`,
    `.notif-pref-section`, `.notif-toggle-row`
  - Build: 40 modules, 307 kB JS, 16.8 kB CSS. 0 TypeScript errors.

**State of ongoing work:**
- Phase 8 complete and deployed to ikhaya.pages.dev (commit `1ec4edb` → Cloudflare Pages).
- Sync works offline (falls back to local data; shows error state in status bar).
- Notifications are in-app only (no push); alerts reset on new session (dismissed via sessionStorage).

**Next steps (in order):**
1. **Phase 9 — Opportunity Intelligence Engine** (AI matching, Capability Profile integration)
   Requires: TPH Core SDK extraction from ReadAfrica → `@tph/core`; Claude API access from client
2. **Phase 10 — Production hardening** (POPIA review, security audit, auth if needed)
3. **Real backend** — Railway or Cloudflare Workers endpoint to replace static JSON "API".
   When built, only `SYNC_URL` in `src/sync/opportunitySync.ts` needs to change.
4. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. Unrecoverable if lost.

**Files changed:**
- `ikhaya/public/api/opportunities.json` — new static API payload
- `ikhaya/src/sync/opportunitySync.ts` — new
- `ikhaya/src/sync/syncManager.ts` — new
- `ikhaya/src/engines/notificationEngine.ts` — new
- `ikhaya/src/components/SyncStatus.tsx` — new (replaces inline SyncBanner)
- `ikhaya/src/components/NotificationBanner.tsx` — new
- `ikhaya/src/App.tsx` — wired sync + notifications; new imports
- `ikhaya/src/pages/ProfilePage.tsx` — added Alert Preferences section
- `ikhaya/src/storage/db.ts` — getNotificationPrefs / saveNotificationPrefs added
- `ikhaya/src/index.css` — Phase 8 styles (~100 lines added)

---

## ✅ 2026-06-28 (session 6) — iKhaya Phase 7 (Application Workspace) + deploy fix

**Done this session:**
- **Blank page fix (deploy):** Cloudflare Pages was serving the raw source `index.html`
  (with `<script src="/src/main.tsx">`) because `NODE_ENV=production` caused npm to skip
  devDependencies — so `vite`, `typescript`, `@vitejs/plugin-react` were never installed
  and the build silently failed. Fix: moved all build tools to `dependencies`; simplified
  build script to `vite build`; added `wrangler.toml` locking `pages_build_output_dir = dist`.
  Commit `024a2f6`.

- **Phase 7 — Application Workspace (commit `1fffea9`):**
  - `src/engines/applicationEngine.ts` — creates/updates ApplicationRecord locally;
    `startApplication`, `updateStage`, `saveNotes`, `saveCVData`, `saveMotivation`,
    `toggleDocument`, `addDocument`; text-export formatters for CV and motivation letter
  - `src/pages/ApplicationWorkspacePage.tsx` — 4-tab workspace: Overview (notes, status
    summary, history, apply button), CV, Letter, Documents; stage progress bar
    (Interested → Preparing → Applied → In Progress → Accepted) + outcome buttons
    (Declined / Withdrawn); debounced 600ms saves; clipboard copy for CV and letter
  - `src/components/CVBuilder.tsx` — SA CV form: Personal info, Education, Experience
    (incl. volunteer flag), Skills (chip input), Languages (chip input), References
  - `src/components/MotivationHelper.tsx` — 4-section guided letter with prompts and
    word count; auto-saves on change
  - `src/components/DocumentChecklist.tsx` — tick-off checklist with required/optional
    badges, progress counter, custom document add
  - `src/components/DeadlineTracker.tsx` — days-remaining badge (green/amber/red/rolling)
  - `src/types/opportunity.ts` — CVData, CVEducation, CVExperience, CVReference,
    MotivationDraft interfaces added
  - `src/pages/OpportunityDetailPage.tsx` — "Start / Continue Application Workspace"
    primary button; loads existing application state on mount
  - `src/pages/ApplicationsPage.tsx` — tapping card navigates to workspace
  - `src/App.tsx` — `/application/:opportunityId` route; workspace hides bottom nav
  - `src/index.css` — full Phase 7 styles (~200 lines)
  - Build: 35 modules, 300 kB JS, 14 kB CSS. 0 TypeScript errors.

**State of ongoing work:**
- Cloudflare Pages should now be deploying the correct built version. Verify at ikhaya.pages.dev.
- Phase 7 complete and deployed.

**Next steps (in order):**
1. Phase 8 — Synchronisation layer (live opportunity data, notification engine)
   Requires: server-side opportunity API endpoint (no backend exists yet)
2. Phase 9 — Opportunity Intelligence Engine (AI matching with Capability Profile)
3. Phase 10 — Production hardening (POPIA, security review, auth)
4. Keystore backup (URGENT 🔴) — `upload-new.jks` local-only. Unrecoverable if lost.

**Files changed:**
- `ikhaya/src/engines/applicationEngine.ts` — new
- `ikhaya/src/pages/ApplicationWorkspacePage.tsx` — new
- `ikhaya/src/components/CVBuilder.tsx` — new
- `ikhaya/src/components/MotivationHelper.tsx` — new
- `ikhaya/src/components/DocumentChecklist.tsx` — new
- `ikhaya/src/components/DeadlineTracker.tsx` — new
- `ikhaya/src/types/opportunity.ts` — CVData + MotivationDraft interfaces added
- `ikhaya/src/App.tsx` — new route + nav hide
- `ikhaya/src/pages/OpportunityDetailPage.tsx` — workspace entry button
- `ikhaya/src/pages/ApplicationsPage.tsx` — navigate to workspace
- `ikhaya/src/index.css` — Phase 7 styles
- `ikhaya/package.json` — build tools moved to dependencies
- `ikhaya/wrangler.toml` — new, locks Cloudflare output dir

---

## ✅ 2026-06-28 (session 5) — iKhaya wired into The People's Home website + Kilimanjaro bot

**Done this session:**
- **`peoples-home/index.html`** — Opportunity Hub placeholder `<span>` converted to a live link:
  `<a class="app live" href="https://ikhaya.pages.dev/" target="_blank" rel="noopener">Opportunity Hub ↗</a>`
  iKhaya is now discoverable from the People's Home website. Commit `08b0f09`.
- **`kilimanjaro/src/knowledge/platform.ts`** — Added `IKHAYA` WorldBEntry constant and updated
  `formatPlatformContext()`. The bot now knows iKhaya is ✅ LIVE (was "coming 2027"), knows all
  6 opportunity types, highlights 25 SA opportunities, and can direct learners to `ikhaya.pages.dev`
  when they ask about bursaries, jobs, grants, learnerships, freelancing, or community opportunities.
  Commit `91debf6`.

**State of ongoing work:**
- iKhaya Opportunity Hub Phase 7 (Application workspace) is the next build phase — not started.

**Next steps (in order):**
1. Phase 7 — Application workspace (CV builder, motivation helper, document checklist, deadline tracker)
2. Phase 8 — Synchronisation layer (live opportunity data, notification engine)
3. Phase 9 — Opportunity Intelligence Engine (AI matching with Capability Profile)
4. Phase 10 — Production hardening (POPIA, security review, auth)
5. Keystore backup (URGENT 🔴) — `upload-new.jks` local-only. Unrecoverable if lost.

**Files changed:**
- `peoples-home/index.html` — Opportunity Hub is now a live link (commit `08b0f09`)
- `kilimanjaro/src/knowledge/platform.ts` — iKhaya added as live World-B entry (commit `91debf6`)

---

## ✅ 2026-06-28 (session 4) — iKhaya Opportunity Hub Phase 4+5 built and pushed

**Done this session:**
- **GitHub repo created:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/ikhaya` (PRIVATE)
- **Local path:** `C:\Users\sifis\Next-Level-Projects\ikhaya`
- **Stack:** Vite + React 19 + TypeScript + vite-plugin-pwa + idb + react-router-dom
- **Commit:** `305414c` — 25 files, 8,697 insertions
- **Phases done:** Phase 2 (domain model as TS types) + Phase 4 (offline PWA foundation) + Phase 5 (discovery engine) + Phase 6 MVP (eligibility engine)

**What was built:**
- `src/types/opportunity.ts` — full domain model: 6 opportunity types, 9 provinces, 9 qualification levels, all entities
- `src/data/seed-opportunities.ts` — 25 real SA opportunities (NSFAS, YES, NYDA, WeThinkCode_, GADS, Upwork, Harambee, etc.)
- `src/storage/db.ts` — IndexedDB layer (idb), namespace: `tph_oh_db`
- `src/engines/discoveryEngine.ts` — full-text search, 8 filter types, sorted results
- `src/engines/eligibilityEngine.ts` — age/province/qualification/citizenship checks, ✓/⚠/✗/— verdicts
- `src/pages/DiscoverPage.tsx` — search bar, type chips, filter chips, opportunity cards with eligibility
- `src/pages/OpportunityDetailPage.tsx` — full detail, eligibility breakdown, Apply Now CTA
- `src/pages/ApplicationsPage.tsx` — application tracking (empty state — Phase 7 needed)
- `src/pages/ProfilePage.tsx` — local profile: age, province, qualification, citizenship, interests
- PWA: service worker, workbox precache, manifest, `_redirects` for SPA routing
- Build: ✓ 275 kB JS, 6 kB CSS, no errors

**Cloudflare Pages deploy — ✅ LIVE:**
- URL: **https://ikhaya.pages.dev/**
- Auto-deploys from `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/ikhaya` main branch

**Next steps (in order):**
1. ⏳ **Connect Cloudflare Pages** (manual — see above)
2. Phase 7 — Application workspace (CV builder, motivation helper, checklist)
3. Phase 8 — Sync layer (fetch live opportunities, notification engine)
4. Phase 9 — Opportunity Intelligence Engine (AI matching)

**Files changed (this session):**
- `C:\Users\sifis\Next-Level-Projects\ikhaya\` — new repo, 25 files

---

## ✅ 2026-06-27 (session 3) — Opportunity Hub defined and locked in Brain

**Done this session:**
- **`brain/platform/opportunity-hub.md`** (NEW) — Full permanent definition of Opportunity Hub:
  purpose, mission, vision, the 5-step philosophy chain, the single sentence definition,
  position in the iKhaya ecosystem, all 6 opportunity types with examples, all 7 engines
  with full specs, relationship to World A / TPH Core / iKhaya, 3 architectural tensions,
  8 guiding principles, 5 success metrics, current status, link to build playbook.
- **`brain/playbooks/build-opportunity-hub.md`** (NEW) — 10-phase implementation blueprint:
  Phase 1 (done) through Phase 10 (production hardening). Each phase has goal, inputs needed,
  key decisions, key files, done condition, and POPIA/security considerations.
- **`brain/platform/ikhaya.md`** (UPDATED) — Platform module map appended. iKhaya's full
  module set documented: OH, Learning Hub, Skills Passport, Funding Hub, Career Hub,
  Entrepreneurship Hub, Community Hub. Cross-reference to opportunity-hub.md added.
- **`brain/PROJECT_GLOSSARY.md`** (UPDATED) — 7 new entries added: Opportunity Hub,
  iKhaya Platform Modules, Opportunity Intelligence Engine, Eligibility Engine,
  Discovery Engine, Application Engine, Capability Profile, #FreeForever Funding Fork.

**Architecture locked:**
- iKhaya = platform brand. Opportunity Hub = flagship module. This distinction is now
  in the brain and must never collapse.
- Capability chain: Capability → Confidence → Readiness → Opportunity → Real-World Outcomes
- 6 opportunity types: Education, Employment, Entrepreneurship, Funding, Community, Global & Digital
- 7 engines: Opportunity, Eligibility, Discovery, Application, Progress, Notification, Intelligence

**Next steps (in order):**
1. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. Back up now.
2. **Wave 12 planning** — wait for ChatGPT brief before starting.
3. **TPH Core SDK extraction** — extract from ReadAfrica into `@tph/core`.
4. **Opportunity Hub Phase 2** — domain model. Begin only when directed.
   Start with: tech stack decision, opportunity data source, entity ownership.

**Files changed:**
- `brain/platform/opportunity-hub.md` — new: full definition
- `brain/playbooks/build-opportunity-hub.md` — new: 10-phase build blueprint
- `brain/platform/ikhaya.md` — updated: platform module map + cross-reference
- `brain/PROJECT_GLOSSARY.md` — updated: 7 new entries

---

## Entry format

```markdown
## [YYYY-MM-DD] — Short description of what happened

**Done this session:**
- Bullet points of what was actually completed and committed

**State of ongoing work:**
- What is mid-flight (started but not finished)
- Exactly where to pick up

**Next steps (in order):**
1. The very next action needed
2. The action after that
...

**Unresolved issues / risks:**
- Anything that needs attention but wasn't resolved

**Files changed (key ones):**
- `path/to/file.ts` — what changed
```

---

## 2026-06-27 (session 2) — Security Constitution + DNA extended to 16 principles

**Done this session:**
- **`brain/SECURITY_CONSTITUTION.md` (NEW):** Full Universal Security Engineering Constitution stored permanently. Covers: security roles + mission, 12 security principles, security mindset assumptions, all 22 review domains (Data, Child Safety, Privacy, Trust Boundaries, Identity & Auth, Authorization, Platform, AI Security, Brain Security, Knowledge Governance, Secrets, Supply Chain, Input Validation, Cryptography, APIs, Databases, File Handling, Business Logic, Availability, Secure Defaults, Deployment, Compliance), 10 threat modelling questions, adversarial review (6 attacker personas), security governance rules, Security Review Report template (Security/Privacy/Resilience/Child Safety/Supply Chain/Production Ready scores /10), Final Principle.
- **`brain/PROJECT_DNA.md` (v1.2):** Principle 16 added — Secure by Design. "Security is not a feature. Security is a permanent architectural constraint." Header updated (Fifteen → Sixteen). Cross-reference to SECURITY_CONSTITUTION.md added. Evolution log appended.
- **`brain/AI_ONBOARDING.md`:** Phase 4 extended with item 19 (SECURITY_CONSTITUTION.md). Security section updated to point to Constitution for security-focused sessions.
- **`brain/README.md`:** Core navigation table updated with SECURITY_CONSTITUTION.md entry. DNA entry corrected to "sixteen principles."
- **`brain/AI_SYSTEM_PROMPT.md`:** Security Review Framework section updated — cross-reference to SECURITY_CONSTITUTION.md added (quick-check list + pointer to full 22-domain reference).
- **Commit:** `3be6bff` — 695 insertions, 5 files. Pushed to `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/peoples-home-web` main.

**State of ongoing work:**
- Security Constitution is complete. Brain now has a three-layer security model:
  - `PROJECT_DNA.md` principle 16 — what cannot be broken
  - `SECURITY_CONSTITUTION.md` — how to operate as security engineering partner
  - `AI_SYSTEM_PROMPT.md` — quick-check list + pointer to Constitution
- All planned brain documents are now complete for this sprint.

**Next steps (in order):**
1. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. If lost, Math Adventure Google Play account is unrecoverable. Back up now.
2. **TPH Core SDK extraction** — extract shared code from ReadAfrica into `@tph/core` standalone package. This is the lead platform item for H2 2026.
3. **Wave 12 planning** — wait for ChatGPT brief before starting. Do not plan ahead of the brief.
4. **Engine playbooks** — `new-wave.md`, `debug-batch.md` in engine-1000 `docs/playbooks/`.
5. **Engine `PROJECT_GLOSSARY.md`** — follow the same pattern as `brain/PROJECT_GLOSSARY.md`.
6. **Deepening passes** — more Journeys, more areas in the live apps.
7. **isiZulu native-speaker review** — ~December 2026.
8. **iKhaya one-suburb beta** — 2026 H2.

**Unresolved issues / risks:**
- Keystore backup: `upload-new.jks` at local path only. HIGH risk of permanent loss. Action required immediately.

**Files changed (key ones):**
- `brain/SECURITY_CONSTITUTION.md` — new: full 22-domain security operating charter
- `brain/PROJECT_DNA.md` — extended: principle 16 (Secure by Design), v1.2
- `brain/AI_ONBOARDING.md` — updated: item 19 added to Phase 4 reading path
- `brain/README.md` — updated: SECURITY_CONSTITUTION indexed in Core navigation
- `brain/AI_SYSTEM_PROMPT.md` — updated: cross-reference to SECURITY_CONSTITUTION

---

## 2026-06-27 — The People's Home Brain built + Kilimanjaro Phases 5–7

**Done this session:**
- **Phase 5 (Platform Knowledge):** Added `src/knowledge/platform.ts` to Kilimanjaro with all 10 live World-A apps, correct URLs, descriptions, and age ranges. Added admin gating (`ADMIN_PHONE_NUMBER` env var).
- **Phase 6 (RAG / live search):** Added `src/knowledge/fetcher.ts` (daily Cloudflare Pages snapshot) and `src/knowledge/search.ts` (keyword-overlap search). Bot can now answer questions from live website content.
- **Phase 7 (Interactive messages):** Added WhatsApp button and list-picker support to the bot. New types in `src/whatsapp/types.ts` and `src/whatsapp/client.ts`. Brain now returns `BotResponse` union (`text | buttons | list`). `receive.ts` routes interactive replies. Welcome message is buttons. App menu is a list picker with all 10 apps in 2 sections.
- **Railway fix:** Moved `@types/express`, `@types/node`, `@types/node-cron`, `typescript`, `prisma` from devDependencies to dependencies (Nixpacks uses `NODE_ENV=production` → skips devDependencies at build time).
- **Knowledge correction:** Discovered all 10 World-A apps are live (bot previously thought only 1–2 were). Complete rewrite of `platform.ts` with accurate URLs and states.
- **Math Adventure Play link fixed:** Correct package ID is `com.sifiso.mathadventurerpg` (was incorrectly `com.ikhaYaai.mathadventurerpg`).
- **THE PEOPLE'S HOME BRAIN:** Built this entire `brain/` directory structure — migrated `docs/memory/` content, restructured canon into `vision/` and `architecture/`, wrote AI_ONBOARDING.md, SESSION_HANDOFF.md, PROJECT_GLOSSARY.md, patterns/, history/, decisions/ subdirectories.
- **Engine-1000 integration (A, B, C):** Created `docs/peoples-home/` in engine-1000 repo with cross-reference docs, TPH tracking, and roadmap mirror.

**State of ongoing work:**
- All Kilimanjaro phases 5–7 are deployed and verified working on Railway.
- Brain construction is complete as of this commit.
- Engine-1000 integration files created.
- Bot persona is "The People's Guide."

**Next steps (in order):**

1. **Add ADMIN_PHONE_NUMBER in Railway Variables**
   - Go to Railway → kilimanjaro project → Variables
   - Add: `ADMIN_PHONE_NUMBER=<your number in E.164 without +, e.g. 27821234567>`
   - This gates personal tools (notes, reminders, invoices) to admin only

2. **Brain deepening passes** — review existing app memory files for accuracy
   - `brain/apps/*.md` — some may predate the final shipped state
   - `brain/platform/tph-core.md` — update with `@tph/core` extraction status

3. **TPH Core SDK extraction** — pull TPH Core out of ReadAfrica into a shared `@tph/core`
   package; this is now the lead platform item

4. **isiZulu review** — deferred to ~December 2026 per ROADMAP

5. **Keystore backup** — the signing `.jks` files are local-only; back them up off-machine
   (high priority security risk — data loss = unrecoverable)

6. **iKhaya one-suburb beta** — background track for 2026 H2

**Unresolved issues / risks:**
- **Keystore backup outstanding** — if the local machine is lost, Math Adventure and
  Science Sprouts cannot be updated on Google Play. Back up `upload-new.jks` immediately.
- **Science Sprouts Play rollout** — in progress (rolling out to Google Play);
  the web PWA is fully live but Play may still be in review stages.
- **iKhaya #FreeForever funding fork** — must be resolved before 2027 launch.
  World A is free; iKhaya needs a revenue model that doesn't compromise the mission.
  This decision is deferred but must be made before iKhaya goes to production.

**Files changed (key ones, this session):**
- `kilimanjaro/src/knowledge/platform.ts` — complete rewrite, all 10 apps
- `kilimanjaro/src/knowledge/fetcher.ts` — snapshot cron
- `kilimanjaro/src/knowledge/search.ts` — keyword search
- `kilimanjaro/src/whatsapp/client.ts` — button + list message types
- `kilimanjaro/src/whatsapp/types.ts` — interactive webhook types
- `kilimanjaro/src/agent/brain.ts` — "The People's Guide" persona, interactive responses
- `kilimanjaro/src/webhook/receive.ts` — interactive reply routing
- `kilimanjaro/package.json` — moved types/build deps to dependencies
- `peoples-home/brain/` — entire directory (new)
- `repository-engine-1000/docs/peoples-home/` — new (engine integration)

---

*(Older entries will appear below as sessions accumulate.)*
