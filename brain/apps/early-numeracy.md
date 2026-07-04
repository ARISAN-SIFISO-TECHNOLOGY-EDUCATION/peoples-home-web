# Early Numeracy

> 🧮 **Foundations** · ages **3–5** · **✅ LIVE — Phase 2 FROZEN + Phases 2.5–5 shipped** —
> installable offline PWA · six discovery modules + two practice games + Numbers Everywhere (7 scenes)
> + Addition Adventure + Taking Away (5 themes each) + Today surface (2026-07-04)

> ## 🔒 The authoritative plan is [`early-numeracy-roadmap.md`](./early-numeracy-roadmap.md)
> The founder **locked a complete product roadmap** (2026-07-03): *finish the product, not the app* —
> Phases 1–10 (Number Discovery → Data & Sorting) + Companion/Environment/Discovery-Book/Vocabulary/
> Parent-Corner integration + Expert-Approved bar + Definition of Done. **The next AI executes THAT
> file** and starts at **Phase 2**. It supersedes the "Implementation phases" section further down.

---

## Status (2026-07-04)

**✅ LIVE at https://early-numeracy.pages.dev/** and **linked on The People's Home** (Foundations
pillar). Repo `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-numeracy` (PRIVATE, branch `master`), local
`C:\Users\sifis\Next-Level-Projects\early-numeracy`. Vite · React 19 · TS · Tailwind v4 · vite-plugin-pwa.

### Phase 2 — Number Discovery: BUILT & LIVE — 2026-07-04 (commit `fa777a6`)
The five "Coming soon" stubs are now **six real, no-fail, audio-guided modules** (Make Five / Make Ten
split out of `make-five-ten`):
- **🌼 Counting Garden** — tap-to-count, one-to-one correspondence, spoken counting, number recognition.
- **🍎 Which is More?** — more / fewer / equal (equal via a centre button); wrong tap re-asks, no penalty.
- **✏️ Number Shapes** — trace the numeral by connecting ordered dots (drag or tap, any order, forgiving);
  numeral always shown with its quantity; 1–10.
- **🎨 Pattern Maker** — AB / ABC / AABB / ABB; gap at end then middle; tap-to-fill.
- **⭐ Make Five / 🌟 Make Ten** — compose on a five-/ten-frame (shared `MakeGame` engine); part–whole
  fact spoken on completion; can't overfill.

**Platform additions:** `lib/progress.ts` (schema-drift-safe default-merge loader), a shared
`components/module-kit.tsx` (frame chrome, celebration burst, level dots, prompt, number words),
`say`/`saySlow` on `useInstruction` (audio-only; every module fully playable silently in visual mode),
and an **environment-as-reward Math Village** that grows on the home screen (+ per-card growth leaves) —
no stars, no scores. `ModulePlaceholder` removed.

**Quality gate status:** tsc 0 errors · clean production build · pure game-logic invariants checked ·
**deploy verified**. ✅ **Phase 2 FROZEN — founder-authorized 2026-07-04.**

### Phase 2.5 — Numeracy Confidence: BUILT & LIVE — 2026-07-04 (commit `22b5a0b`)
The confidence bridge before bigger concepts:
- **🌞 Today** (home surface, `components/TodayStrip.tsx`) — a daily-rotating suggested activity, the
  child's **favourite** to replay (most-played module), and a spoken **real-world counting** nudge from
  the transfer-prompt pool. Suggestions, never tasks; no scores.
- **🔢 Number Match** — numeral↔quantity recognition/matching, both directions alternating by level;
  wrong tap wobbles and re-asks. Consolidates Counting Garden / Number Shapes recognition.
- **🔍 Number Hunt** — find the called-out numeral among decoys, three finds per round, spoken target
  cue; no fail state.
- Home screen now groups modules into **"Play & Learn"** (the core six) and a **"🎯 Practice"** section
  (`ModuleDef` gained a `group: 'discover' | 'practice'` field).

Quality gate: tsc 0 · clean build (8 lazy chunks, PWA precache 23, zero external requests) · logic
invariants checked (Match options, Hunt board/targets, Today daily-pick bounds) · **deploy verified**
(entry-chunk hash match; new chunks 200).

### Phase 3 — Numbers Everywhere: BUILT & LIVE — 2026-07-04 (commit `dacd6a6`)
The 🌍 **Numbers Everywhere** module (`modules/numbers-everywhere/`) — *maths lives in real places*:
- **Seven scenes** (Kitchen · Garden · Bedroom · Playground · Shops · Road · Home), each rendering
  tagged objects scattered in the scene.
- Each round poses a data-driven, no-fail task: **COUNT** a kind of thing ("Count the apples") or
  **FIND** some of them ("Find 3 windows"). Right taps count up aloud; other taps wobble gently.
- Object tags (`apple`/`fruit`/`round`/`window`/`car`/…) make tasks contextual and include shape finds
  ("round things") without a new mechanic. Generator proven solvable for all 7 scenes.
- New **"🌍 Explore"** home section (`ModuleGroup` gained `'explore'`); home reads Play & Learn ·
  Practice · Explore. App meta/manifest description made evergreen (`680afbc`).

Quality gate: tsc 0 · clean build (9 lazy chunks, PWA precache 24, zero external) · scene-logic
invariants checked · **deploy verified** (live entry hash `index-DRC0W2up.js`; chunk 200).
*(Roadmap note: "compare sizes" defers to Phase 7 Measurement, "sort colours" to Phase 10 Data & Sorting.)*

### Phase 4 — Addition Adventure: BUILT & LIVE — 2026-07-04 (commit `7da1f98`)
The ➕ **Addition Adventure** module (`modules/addition-adventure/`) — concrete visual addition, **no
equations**:
- Two groups of things are shown; the child taps each to move it into a container while the voice
  counts up, then hears the part-whole fact ("three and two make five").
- One join-and-count engine cycles the **five roadmap themes** as levels — **Add Together · Magic Basket
  · Feed the Animals · Treasure Chest · Bridge Builder** (different item + container each). Sums grow to
  5, then to 10. No timers, no fail state.
- Kept as **one** "Addition Adventure" card (same mechanic, calmer home for ages 3–5) rather than five
  cards, while still delivering all five experiences.
- New **"➕ Adding"** home section (`ModuleGroup` gained `'operations'`); home = Play & Learn · Adding ·
  Practice · Explore.

Quality gate: tsc 0 · clean build (10 lazy chunks, PWA precache 25, zero external) · addition round
bounds proven (a≥1, b≥1, 2≤total≤maxSum) · **deploy verified**.

### Phase 5 — Taking Away: BUILT & LIVE — 2026-07-04 (commit `420280d`)
The ➖ **Taking Away** module (`modules/taking-away/`) — subtraction as concrete take-away stories,
**still visual, no equations**:
- A group is shown; the child taps items to send them away; the "how many left" count ticks **down**,
  then they hear the fact ("five take away two leaves three").
- One take-away engine cycles **five themes** as levels — **Birds Fly Away · Cookie Time · Fish Swim
  Away · Blocks Away · Balloons Float Away**. N grows to 5, then to 9. Once the story amount is gone the
  rest lock — no over-removing, no fail state.
- Lives in the operations section, now **"➕➖ Adding & Taking Away"**.

Quality gate: tsc 0 · clean build (11 lazy chunks, PWA precache 26, zero external) · subtraction bounds
proven (3≤n≤maxN, 1≤m≤n−1, 1≤left) · **deploy verified**.
⛔ **Phases 2.5–5 not yet Frozen** — remaining gate is the **real-child play-test**. After it passes →
Freeze 2.5–5 → **Phase 6 (Shapes World)**.

> ⚠️ Still uses Early Numeracy's **own** hooks (`useNarration`/`useInstruction`/`useSessionState`/
> `useChildLock`), not the shared **TPH Learning Engines** (D-13). Adopting those engines remains part
> of "finishing the product" and can be folded into a later phase's platform-integration pass.

### Senior audit + security pass — 2026-07-03 (commit `8a03f92`)
Parity with the Early Literacy remaster; **no gameplay changed**.
- **C1 — real PWA icons.** `generate-icons.mjs` imported `canvas` (uninstalled) → the catch wrote
  1×1 transparent 70-byte placeholders, so the PWA had **no real install icon**. Ported the
  dependency-free zlib PNG generator ([[tph-early-literacy-status]] shares it) in the green brand →
  proper 192/512/maskable icons.
- **C2 — zero external.** Removed a **dead Google-Fonts `runtimeCaching`** block from `vite.config.ts`
  (no web fonts are actually loaded). The app now makes **zero external requests** — true offline / no-tracking.
- **M1 — ErrorBoundary** added and wrapping `<App>` (gentle "garden is resting" screen vs. white screen).
- **Security `public/_headers`** (CSP + X-Frame-Options DENY + nosniff + no-referrer + Permissions-Policy).
  Build has **no inline scripts**, so `script-src 'self'` holds with no `'unsafe-inline'`; `style-src`
  keeps `'unsafe-inline'` (Tailwind); `worker-src 'self' blob:` (Workbox). Mirrors iKhaya/Early Literacy.
  **Verified LIVE:** all 5 headers serving on the deployed site; assets 200 with correct MIME.
- **Deploy hardening:** `wrangler.toml` pins `dist`; moved `vite-plugin-pwa` to `dependencies` so a
  production install can't skip it. `npm audit` = **0 vulnerabilities**.

**Backlog (flagged, not fixed):** welcome-audio autoplays on mount without a user gesture (browsers
block it — same class as Early Literacy's M9; defer to a UX pass); `user-scalable=no` (intentional for
young children); the whole point — **Phase 2 real gameplay**. Also: the `build` script uses bash env
syntax (`WEB_BUILD=1 vite build`) which only runs on Linux/Cloudflare, not a Windows dev shell.

---

## What it is

A play-based number-sense app for pre-school and early primary children (ages 3–7). Not
arithmetic — number *sense*: the deep feeling for what numbers mean, how quantities relate,
and how patterns work. Delivered as five short game modules, each completable in under
5 minutes, fully offline, no login, no tracking. A child can tap, drag, and hear their
way through every activity without needing to read a single word.

---

## Category & audience

| Field | Value |
|---|---|
| **Pillar** | Foundations |
| **Capability gained** | Number sense — the bedrock of all future numeracy |
| **Primary audience** | Children ages 3–7 (pre-school → Grade 1) |
| **Secondary audience** | Parents and caregivers playing alongside |
| **World** | A — offline, no login, no server, #FreeForever |
| **DNA** | Matches Math Adventure RPG / ReadAfrica pattern exactly |

---

## Why it exists — the gap

Math Adventure RPG (ages 3–17) uses an RPG story format that requires following narrative
and reading quest text. That works well from roughly age 6 upwards. But ages 3–5 — the
children who need to build the *foundation of the foundation* — are left without a home.

Early Numeracy fills that gap: pure sensory, tactile, audio-first play for the youngest
learners before reading exists. It is the on-ramp to Math Adventure, not a replacement.

---

## What "number sense" actually means

Number sense is not counting to 100. It is a cluster of deeply-wired intuitions:

| Concept | What it looks like in a child |
|---|---|
| **Subitizing** | Instantly seeing "that's 3" without counting one-by-one |
| **1-to-1 correspondence** | Touching each object exactly once while counting |
| **Cardinality** | Knowing the last number said IS the total (not just a label) |
| **Comparison** | Knowing which pile has more/less without counting both |
| **Composition** | Knowing 5 can be made from 2+3, or 4+1, or 1+4 |
| **Patterns** | Seeing and extending AB, ABC, AABB sequences |
| **Measurement** | Longer/shorter, heavier/lighter — not yet with units |

A child who has these by age 7 is mathematically safe for the next decade. A child who
hasn't is already behind before they touch a calculator.

---

## The five game modules

Each module is self-contained, short (2–5 min), and exits cleanly. No forced progression —
a child can replay any module in any order.

---

### Module 1 — Counting Garden 🌱

**Teaches:** 1-to-1 correspondence, cardinality, counting 1–20

**Gameplay:**
- A garden scene with animals, fruit, or flowers scattered around
- Child taps each object; it "bounces" and a cheerful voice counts aloud in the child's language
- When the last one is tapped, a large number appears: "That's 7!"
- Levels 1–10 first; unlock 11–20 after 3 successful rounds of 1–10
- Wrong taps (tapping the same object twice) give a gentle wobble — no failure state

**UX rules:**
- Objects must be at least 64×64px tap targets
- Audio is mandatory for this module — mute shows a visual counter instead
- No timer, no pressure

---

### Module 2 — Which is More? 🐘

**Teaches:** Subitizing (up to 5), comparison (more / less / equal)

**Gameplay:**
- Two plates appear, each holding 1–9 objects (dots, animals, shapes)
- Child taps the plate with MORE; or taps the = button if they look the same
- Quantities up to 5 are shown as distinct arrangements (dice patterns)
- Quantities 6–9 are scattered randomly — child must count or estimate
- Correct: both plates celebrate. Wrong: plates "tip" to show which was heavier

**Progression:**
- Stage 1: quantities 1–5 (subitizing range)
- Stage 2: quantities 1–9 (counting required)
- Stage 3: one quantity shown as dots, one shown as a numeral (bridging symbol to quantity)

---

### Module 3 — Number Shapes ✏️

**Teaches:** Digit recognition (0–9), numeral-to-quantity mapping

**Gameplay:**
- A large numeral appears on screen with a dotted trace path
- Child traces it with a finger (touch) or mouse (desktop)
- When the trace is complete: the numeral "fills in" and the matching number of objects
  appear and count themselves aloud
- Then: "Can you find the 4?" — child taps the correct numeral from a row of 3

**Key principle:** Every digit is always shown alongside its quantity. Symbol and meaning
are never separated.

---

### Module 4 — Pattern Maker 🔵🔴

**Teaches:** Patterns — AB, ABB, ABC sequences; completing and extending

**Gameplay:**
- A row of coloured shapes is shown with one or more gaps (marked with ?)
- Child drags the correct shape/colour from a tray to fill each gap
- After filling: the whole pattern plays through as an animation with a rhythm sound
- Correct: the pattern "dances." Wrong: the gap glows, child tries again (no penalty)

**Levels:**
- AB (🔵🔴🔵🔴?) — easiest
- ABB (🔵🔴🔴🔵🔴🔴?)
- ABC (🔵🔴🟡🔵🔴?)
- AABB (🔵🔵🔴🔴🔵🔵?)

---

### Module 5 — Make 5, Make 10 🧩

**Teaches:** Number composition and decomposition (number bonds for 5 and 10)

**Gameplay:**
- A "frame" with 5 (or 10) slots appears — some already filled with coloured dots
- Child drags dots from a pile to fill the remaining slots
- When the frame is full: a celebratory animation and "5! You made 5!"
- Variation: two frames, fill both to make 10 — bridging to Part-Part-Whole thinking

**Why this matters:** A child who truly owns "5 = 2+3 = 1+4 = 0+5" is set for addition
and subtraction. This module plants that seed without a single equation on screen.

---

## UX principles — designing for 3-to-7-year-olds

These are **hard rules**, not guidelines:

| Rule | Reason |
|---|---|
| **No reading required** | Core gameplay must be completable by a non-reader |
| **Large touch targets (min 64×64px)** | Small motor control is still developing |
| **Audio-first feedback** | Children this age respond to voice more than text |
| **Immediate, joyful feedback** | No delay between action and response |
| **No timers in core play** | Anxiety at this age destroys learning |
| **No fail state / no game over** | Wrong answer = try again, never punishment |
| **Short sessions** | Each module completable in under 5 minutes |
| **Parent can sit alongside** | No "parent mode" account needed — design for shared play |
| **No ads, no upsells, no notifications** | World A principle — no dark patterns ever |

---

## Language & localisation

Numbers are culturally loaded — children should hear them in their home language first.

**Phase 1 (MVP):** English audio only
**Phase 2:** isiZulu number words (kunye, kubili, kuthathu…)
**Phase 3:** Sesotho, Afrikaans

The audio system must support swappable language packs (same architecture as ReadAfrica's
language switching). The UI text labels are minimal — icons carry most meaning.

---

## Tech stack

Follows the **World A proven pattern** exactly:

| Layer | Choice | Reason |
|---|---|---|
| Framework | Vite + React + TypeScript | Ecosystem standard |
| Styling | CSS Modules or Tailwind | Match whichever the team is using |
| Audio | Web Audio API + `useNarration` hook | Port from Math Adventure RPG |
| Offline | Vite PWA plugin (service worker + manifest) | Proven across all World A apps |
| Hosting | Cloudflare Pages | Ecosystem standard |
| Storage | `localStorage` only | World A — no server |
| Animation | CSS keyframes + Framer Motion (where needed) | Keep bundle lean |
| Build | `npm run build` → `dist/` | Standard |

**No backend. No accounts. No analytics SDK. No third-party tracking.**

---

## Implementation phases

> ⚠️ **SUPERSEDED (2026-07-03)** by the locked [`early-numeracy-roadmap.md`](./early-numeracy-roadmap.md).
> The phases below are the original Blueprint-v1 plan, kept for history. Execute the **locked roadmap**
> (Phases 1–10) instead; Phase 1 (Shell) here still matches reality and is done.

### Phase 1 — Shell & foundation
- Vite + React + TS scaffold
- PWA manifest + service worker (offline from day one)
- Home screen with 5 module cards
- Audio system: `useNarration` hook ported from Math Adventure
- Touch/click event normalisation (large targets, no double-tap zoom)
- Mobile-first responsive layout
- Deploy to Cloudflare Pages

**Done when:** App installs as a PWA, opens offline, shows all 5 module cards with placeholder screens.

---

### Phase 2 — MVP (modules 1 + 2)
- **Counting Garden** — levels 1–10, tap-to-count, audio counting
- **Which is More?** — stage 1 (quantities 1–5), comparison mechanic
- Shared celebration component (confetti / bounce / audio cheer)
- Basic progress stored in `localStorage` (which modules visited — no scores)

**Done when:** A 4-year-old can complete both modules without adult help.

---

### Phase 3 — Number recognition (module 3)
- **Number Shapes** — digit trace (0–9), numeral-to-quantity bridge
- SVG trace paths for all 10 digits
- Numeral recognition quiz (tap the right number)

---

### Phase 4 — Patterns + bonds (modules 4 + 5)
- **Pattern Maker** — drag-and-drop, AB/ABB/ABC/AABB levels
- **Make 5, Make 10** — frame-filling, Part-Part-Whole intro
- Unlock system: later levels unlock after earlier ones are tried (not required — just rewarded)

---

### Phase 5 — Counting Garden extension + polish
- Extend Counting Garden to levels 11–20
- Which is More? Stage 3 (numeral vs dots)
- Sound design pass — all audio reviewed for warmth and consistency
- Accessibility pass: reduced motion, high contrast mode

---

### Phase 6 — Localisation
- isiZulu audio pack for Counting Garden + Which is More?
- Language selector on home screen
- Architecture for adding further language packs

---

### Phase 7 — Android (if needed)
- Capacitor wrap (same as Math Adventure RPG pattern)
- Google Play Store submission
- Keystore creation + backup to Google Drive (follow TPH-KEYSTORES-BACKUP protocol)

---

## What success looks like

| Metric | Target |
|---|---|
| A 3-year-old can tap through Counting Garden without help | Core UX test |
| A 5-year-old can complete all 5 modules in one sitting | Engagement test |
| App opens fully offline after first install | World A compliance |
| PWA installs on Android in ≤ 2 taps | Accessibility test |
| No reading required to complete any module | Core UX invariant |
| Page load < 2s on a mid-range Android device on 3G | Performance baseline |

---

## Relationship to the rest of the ecosystem

| App / system | Relationship |
|---|---|
| **Math Adventure RPG** | Early Numeracy is the on-ramp; Math Adventure takes over at ~age 6 |
| **ReadAfrica** | Sister app in Foundations — reading and number sense grow together |
| **Everyday Foundations** | Adult version covers the same ground for grown-ups who missed it |
| **TPH Core / Passport** | No active integration in Phase 1–6; adopt `@tph/core` envelope in Phase 7+ |
| **iKhaya** | No connection — World A, no accounts |

---

## Open decisions (resolve before Phase 1 build)

| Decision | Options | Recommendation |
|---|---|---|
| Styling approach | CSS Modules vs Tailwind | Match the next most recently built World A app |
| Animation library | CSS only vs Framer Motion | CSS only for Phase 1; Framer if complexity grows |
| Audio format | MP3 vs WebM | Both, with MP3 fallback (Safari compatibility) |
| Trace engine for Module 3 | Custom SVG vs third-party | Custom SVG paths — keeps bundle zero-dependency |
| First SA language after English | isiZulu vs Sesotho | isiZulu (largest first-language base) |

---

## Related

- [`math-adventure-rpg.md`](./math-adventure-rpg.md) — the on-ramp destination; audio system to port
- [`read-africa.md`](./read-africa.md) — sister Foundations app; language pack architecture to study
- [`../architecture/01-capability-architecture.md`](../architecture/01-capability-architecture.md) — canonical slot: Foundations #3
- [`../../BLUEPRINT.md`](../../BLUEPRINT.md) — full 40-app ecosystem map

---

## First-time instruction protocol

Every module opens with a short voiceover + animated demonstration (≤8 seconds) that shows
the child exactly what to do. No reading. No instructions on screen. After one loop,
gameplay begins automatically.

- A **question-mark icon** (no text label) in a fixed corner replays the demo at any time.
- **Idle rule:** if no input is received for 8 seconds, the voice gently repeats the core
  instruction for that module. Example: *"Tap each animal to count them."* The idle prompt
  cycles: same instruction on the first trigger, a second gentler version on the third.
- **Full audio script required** for every state before recording begins:
  - Module entry prompt
  - Idle prompt (two variations per module)
  - Correct response celebration
  - Level transition
  - Session completion
  - Correction (per module — see below)
- Script must be reviewed by an early-years specialist before voice recording. This is not
  optional — assumptions about what a 3-year-old understands from a phrase are often wrong.

---

## Correction patterns

No fail state. No game over. No buzz. No "Wrong." Every correction is warm, calm, and
immediately actionable. Voice actor direction: *encouraging parent*, never *disappointed teacher*.

| Module | Wrong action | Correction response |
|---|---|---|
| **Counting Garden** | Tap an already-counted object | Object wobbles · voice: *"You already counted that one!"* |
| **Which is More?** | Tap the smaller plate | Brief pause · correct plate glows · voice: *"This pile has more. Let's try another!"* · question reshuffles |
| **Number Shapes** | Poor trace or wrong numeral tapped | Dotted trace path pulses again · voice: *"Try again!"* |
| **Pattern Maker** | Drag wrong shape to gap | Shape bounces back to tray · target gap glows invitingly |
| **Make 5 / Make 10** | Try to overfill the frame | Extra dot slides back · voice: *"Too many! We need 5."* |

Every correction ends with the child still in control, still playing, never penalised.

---

## Motor accessibility — tap alternatives to drag

Two modules (Pattern Maker, Make 5/Make 10) rely on dragging. Dragging is a more complex
motor skill than tapping, and some 3–4 year olds cannot do it reliably. A tap-based
alternative must be active from **day one** — not added in a later phase.

**Pattern Maker:**
- Tap a shape in the tray → it lifts with a visual highlight (selected state)
- Tap any gap in the pattern → the shape places itself
- Drag still works for children who can manage it

**Make 5 / Make 10:**
- Tap a dot in the pile → it attaches visually (follows the finger/cursor to the frame)
- Tap an empty slot → dot snaps into place
- Drag path still works

**Drop zone tolerance:** drag landing zones must accept shapes released up to **1.5×
the visual target size** off-centre. Small hands are imprecise — the app must compensate.

---

## Audio architecture

The app is audio-first and fully offline. Audio asset strategy must balance richness with
download size on data-constrained SA devices.

**Lazy-loading rule:**
- Home screen audio + Counting Garden audio load on first app open.
- All other module audio loads when the child first taps that module card.
- A brief audio-only loading indicator plays while the module audio downloads (a short
  musical chime — never a spinner with text).

**Caching rule:**
- Service worker pre-caches each module's audio on first play.
- Once cached, audio is never re-fetched (no background refresh).
- Language pack audio is a separate bundle, downloaded on demand when the parent selects
  that language. Cached permanently after first download.

**Encoding:**
- Primary: Opus / WebM (smaller, better quality)
- Fallback: MP3 (Safari compatibility)
- Mono only — stereo is unnecessary for voice

**Playback rule:** if a clip hasn't loaded when triggered, visual feedback proceeds
immediately and the voice plays as soon as the buffer is ready. A clip is never
cut off mid-sentence. Never play silence when a voice is expected.

**File size budgets:** determined by profiling and testing during Phase 1, not locked
in advance. The goal is fast first-install on 3G; actual numbers come from measurement.

---

## Visual-instruction mode

The app is audio-first, but deaf and hard-of-hearing children deserve full access.

**Parent-activated toggle** on the home screen: an ear-with-line icon (no text).
When on:
- Every voice instruction is replaced by a short looping animated demonstration.
  Example: an animated hand taps the animals one by one; a counter increments visually.
- Numerals in Number Shapes are accompanied by animated quantity breakdowns.
- Counting Garden: objects highlight one by one with a large pulsing number — no audio needed.

**Architectural commitment (Phase 1):**
Audio instruction logic and visual instruction logic must be **separate in code** from the
first line written. The visual-instruction layer should be an injectable alternative, not
a flag bolted onto audio code. This enables the feature to be added in a later phase
without refactoring the core modules.

This feature is not in Phase 1–3. The code separation is.

---

## Keeping children in the experience

**Goal:** a child should not accidentally leave the app mid-session.
Specify as goals, not guarantees — PWA fullscreen behaviour varies across Android versions
and browsers.

**Child-lock activation:**
- Long-press a fixed corner of the home screen for 3 seconds → app enters immersive/
  fullscreen mode (where the platform supports it).
- A small lock icon (no text) appears in the corner while locked.
- To unlock: long-press the lock icon → hold a green circle for 3 seconds.
- This keeps young children in the experience without requiring parents to stay present.

**State restoration:**
- On `visibilitychange` (app minimised and restored): the child resumes exactly where
  they were — same module, same level, same question.
- State is already in `localStorage` — the restore path must be **explicitly tested**,
  not assumed to work.

**Testing requirement:** test on at least 3 common SA Android devices (budget tier)
before shipping Phase 1. The interaction may behave differently on older Android versions.

---

## Play-testing protocol

A play-test gate is required before any phase is marked complete. This is not optional.
Technology assumptions about what a 3-year-old can do are often wrong — only real children
reveal the truth.

| Phase | Test group | What to observe |
|---|---|---|
| **Phase 1** | 2 children aged 3–4 | Can they navigate the home screen and start a module? Adjust tap targets and audio clarity. |
| **Phase 2** | 5 children aged 3–5 | Can they complete Counting Garden and Which is More? without adult help? Iterate on corrections. |
| **Phase 3** | 3–4 children aged 4–6 | Can they trace digits and pass the numeral quiz? |
| **Phase 4+** | Small group each time | Always try to include one child with motor delays. |

**Format:** informal — one afternoon with a few families. No formal UX lab, no recording
equipment required. The commitment is to **observe a real child using the app before marking
any phase done**. What you see in that afternoon is worth more than any assumption.

---

## Real-world transfer — constitutional rule

Every session must end with a **"Try this at home"** prompt. This is not optional and
not a feature — it is the app's philosophy made visible.

Technology starts the learning. Reality completes it.

**Implementation:**
- After any module completion, a full-screen card appears.
- A single illustration (no text) is shown alongside a spoken instruction.
- The voice speaks the prompt. The child hears it. They go and do it.
- Dismiss with a tap anywhere on the screen.
- Prompt is randomly selected from a pool of 20+ items. Rotates so repetition is rare.

**Example prompts:**
- *"Count five cups."*
- *"Find something heavy."*
- *"Find two circles."*
- *"Touch four leaves."*
- *"Find three red things."*
- *"Which shoe is bigger?"*
- *"Count the steps to the door."*
- *"Clap five times."*

**Why this is constitutional:** The Foundations pillar is built on the insight that number
sense grows through physical interaction with the world, not through screen time alone.
The real-world transfer prompt is the bridge. Every session that ends without one is a
missed opportunity to turn a tap into a lived experience.
