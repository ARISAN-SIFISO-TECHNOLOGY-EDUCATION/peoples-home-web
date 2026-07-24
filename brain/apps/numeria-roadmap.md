# 🗺️ Numeria — Animation & Storytelling Blueprint (Math Adventure RPG · World A · Community Edition)

> **Status: 📝 DRAFT — awaiting founder Freeze of MA-0.** Canonical blueprint for the experience layer
> of the **Math Adventure RPG** web Community Edition. The naming architecture (§0) and the
> **MA-0 Numeria Constitution** are **constitutional** once frozen — they may change only through a
> **formal roadmap revision**.
>
> This is the *experience-layer* roadmap that elevates Math Adventure RPG from a set of levels into a
> **world the learner inhabits**. It does **not** replace the educational engine — `src/mathEngine.ts`
> and the 65-level progression are **build-complete and frozen**. Numeria is the shell built *over*
> them.
>
> **Governance (founder's model): Blueprint → Freeze → Build.** Each MA milestone is frozen before the
> next begins. **Freeze is a founder act — the next AI never self-declares a freeze.**
>
> **Web only.** Everything here ships behind the platform seam and is inert in the `play-store`
> profile. See [`math-adventure-release-policy.md`](./math-adventure-release-policy.md).
>
> **Progress:** MA-0 📝 DRAFT — not yet frozen · **MA-1 ✅ built 2026-07-21** (implemented, not frozen —
> see §3 MA-1) · MA-2…MA-5 not started.
>
> ⚠️ **Recorded deviation.** MA-1 was built while MA-0 is still DRAFT, on the founder's explicit
> instruction of 2026-07-21 (*"We are now beginning implementation… Your job is to implement MA-1
> (Living World) only"*). The founder may set aside their own sequencing rule; **an AI may not.** The
> deviation is recorded here rather than normalised: `Blueprint → Freeze → Build` remains the model,
> and MA-2 must not begin without a comparable explicit instruction.
>
> **Resolved by the founder 2026-07-20:** the world is **Numeria** · the threshold province is
> **🌼 Meadow Gate** · **The Academy is part of Numeria** (its highest institution of learning) ·
> **Companion ≠ Guide** (two entities, never merged).
> **🔓 Still open, and the last thing blocking the MA-0 freeze: the Guide's identity.**

---

## 0. Naming architecture (proposed — LOCK at MA-0 freeze)

> **Don't rename the app. Name the world.**

| Field | Value |
|---|---|
| **Product name** (adults, Play Store, People's Home, repo, URL) | **Math Adventure RPG** |
| **Experience name** (learner-facing world) | **🗺️ Numeria** |
| **Kids' shell** (ages 3–12) | Kids' Adventure — *the provinces of Numeria* |
| **Senior shell** (ages 13–17) | The Academy — **Numeria's highest institution of learning** (§2) |
| **Learner-facing brand** | "Welcome to Numeria." |

**No churn:** repository (`ARISAN-SIFISO-TECHNOLOGY-EDUCATION/math-adventure-rpg`), package name, URL
(`math-adventure-rpg.pages.dev`), Play Store identity, People's Home registry entry **all stay the
same.** Only the in-app web experience changes.

### ⚠️ Numeria is NOT Number Kingdom

This is constitutional, and it is the reason the name was chosen.

| App | World | Theme | Ages |
|---|---|---|---|
| Early Numeracy | 🌈 **Number Kingdom** | *"Numbers are friendly."* | 3–6 |
| **Math Adventure RPG** | 🗺️ **Numeria** | *"Mathematics is a world worth exploring."* | 3–17 |

The founder's rationale, recorded verbatim (2026-07-20):

> Early Numeracy is designed for children around ages 3–6. Its world should feel welcoming, magical,
> simple, comforting. "Number Kingdom" immediately conveys that. Math Adventure RPG already has
> regions like Academy of Numbers, Merchant's Guild, Dragon's Tower, Engineers' Citadel, Star
> Observatory. Those aren't nursery locations — they suggest a civilization with professions,
> history, exploration, and mastery. The player isn't just visiting numbers anymore. They're becoming
> part of a mathematical world. **The child has grown. The world has grown with them.**

"The Kingdom of Numbers" was considered and **rejected**: it is a near-anagram of a founder-LOCKED,
constitutional name owned by a *different app in the same pillar*, with which it would co-exist in the
planned Foundations Collection. Precedent: **D-13**, where "TPH Core" meaning two things was resolved
by renaming the newcomer, on the grounds that *"two definitions would silently confuse every future
agent."* See **D-16**.

Existing anti-conflation clauses that this section satisfies: `baselines/2026.1-community-release.md`
§6 (immutable), `apps/math-adventure-rpg.md`, and a code comment in `src/web/living-world/index.ts`.

---

## 1. The core doctrine

### Story supports learning; it never competes with it

Math Adventure RPG's "Expert Approved" badge was **rejected on 2026-06-17 for text volume and
disruptive sounds** ([`vision/01-product-rules.md`](../vision/01-product-rules.md)). A storytelling
layer is the single most likely way to re-trigger that failure. So the doctrine is not aspirational —
it is a scar.

In practice: story scenes are brief · optional or reward-gated where appropriate · gameplay remains
the primary learning experience · animation **explains or celebrates**, it never buries the maths
under dialogue.

### The Four-Purpose Test (founder addition, 2026-07-20)

> **Every story element must either teach, motivate, orient, or celebrate. If it does none of those
> four, it does not belong in Numeria.**

| Purpose | Example |
|---|---|
| **Teach** | A concept animation showing a fraction being taken from a whole |
| **Motivate** | A bridge rebuilding itself as problems are solved |
| **Orient** | The guide explaining why the learner is travelling to the next province |
| **Celebrate** | An achievement animation after mastering a skill |

If an idea exists only because it looks impressive, it fails the test. This converts the doctrine
from something arguable into an objective filter any future contributor can apply alone.

### Wrap, don't rewrite

The educational engine is the hard part and it is done — `src/mathEngine.ts` (~2000 lines of
procedural generators) and the 65-level, 4-phase progression are verified by ~2,600 generated problems
per test run. **Numeria changes only what wraps them.** No milestone in this blueprint edits
`mathEngine.ts`, `phases.ts` level definitions, the progression rules, or the save format.

---

## 2. The provinces of Numeria

Ten named regions already exist in `src/game/levelContent.ts`, each with a committed colour identity
and emoji — but **nothing renders them spatially.** The `kingdomMap` feature flag was declared with no
home; this is its content spine. Nothing is invented to fill the map.

| Province | Region | Phase | Levels |
|---|---|---|---|
| **🌼 Meadow Gate** *(the threshold)* | *new — see below* | 1 | 1–15 |
| **Central Numeria** | 🏫 Academy of Numbers | 2 | 1–5 |
| **Western Numeria** | 🏪 Merchant's Guild | 2 | 6–10 |
| **Northern Numeria** | 🐉 Dragon's Tower | 2 | 11–15 |
| **The Highlands** | 🌟 Star Observatory | 2 | 16–20 |
| **The Western Reach** | 🏦 Merchant Republic | 3 | 1–5 |
| **Industrial Numeria** | 🏗️ Engineers' Citadel | 3 | 6–10 |
| **The Storm Highlands** | 🌩️ Storm Observatory | 3 | 11–15 |
| **The Far Peaks** | 🏔️ The Pinnacle | 4 | 1–5 |
| **The Forge Deeps** | ⚙️ The Geometry Forge | 4 | 6–10 |
| **The Summit** | 🏆 The Summit Academy | 4 | 11–15 |

### The geography already tells a story

Reading the existing content as a map reveals a structure nobody designed on purpose — the regions
**rhyme across phases**, and each pair is the same institution at a higher level of mastery:

- 🏫 **Academy of Numbers** (first province a learner enters) → 🏆 **The Summit Academy** (last).
  The world opens and closes on the same institution. That is the whole arc in two names.
- 🏪 **Merchant's Guild** → 🏦 **Merchant Republic** — a guild becomes a republic.
- 🌟 **Star Observatory** → 🌩️ **Storm Observatory** — the same watchers, harder skies.
- 🏗️ **Engineers' Citadel** → ⚙️ **The Geometry Forge** — building becomes making.

**Numeria does not need to be invented. It needs to be revealed.** This is the strongest argument
that the world layer is a wrap, not a rewrite.

### 🌼 Meadow Gate — the threshold (founder decision, 2026-07-20)

Phase 1 (Pre-School, ages 3–5, 15 levels) had **no province** — only P2/P3/P4 define worlds. It is the
one region that had to be genuinely *created* rather than revealed, and it is where the **Welcome
Moment** lands, so it was a founder decision.

**Meadow Gate** was chosen over *Foothills of Numeria* (assumes the child already knows they are
climbing) and *Numeria's Doorstep* (descriptive but static). The founder's rationale:

> You don't begin by entering a fortress. You begin by walking through a meadow.

It is gentle, visual, welcoming, and age-appropriate — and it makes the arc legible at a glance:
🌼 Meadow Gate → 🏫 Academy of Numbers → 🏪 Merchant's Guild → 🏗️ Engineers' Citadel →
🌟 Star Observatory → … → 🏆 The Summit Academy. **An adventure that grows with the learner.**

*Implementation note:* Phase 1 has no `P1_WORLDS` array today. MA-1 adds one in the shape of the
existing P2–P4 world definitions — the only genuinely new content in the province map.

### 🎓 The Academy is part of Numeria (founder decision, 2026-07-20)

**Yes — Numeria extends to ages 13–17.** The senior shell is not a second, disconnected universe.

> **The Academy is Numeria's highest institution of learning.**

Younger learners **travel through** Numeria; older learners **do not leave it** — they **graduate
within it**. The Academy of Numbers → Summit Academy pairing stops being a coincidence in the content
and becomes the world's narrative structure.

This also reinforces the educational philosophy that learning is **continuous rather than segmented**,
and it does so without imposing a child's visual register on a 17-year-old's exam preparation: The
Academy keeps its own tone as an *institution within* the world, not as an exception to it.

---

## 3. Milestones (build incrementally; freeze each before the next)

### MA-0 — The Numeria Constitution ⚖️ — 📝 DRAFT

**The immutable foundation for every future implementation decision.** Nothing is built until this is
founder-frozen. Full text: [`numeria-constitution.md`](./numeria-constitution.md).

Covers: Mission · Educational Principles · **Educational Invariants** · Experience Principles ·
Navigation Principles · Platform Principles · World Structure (the provinces, §2's two open questions
resolved) · The Guide · The Welcome Moment · the Four-Purpose Test · Wrap-Don't-Rewrite · Definition
of Success.

### MA-1 — Living World 🌤️ — ✅ BUILT 2026-07-21 (not frozen)

**Delivered:** `math-adventure-rpg/src/web/living-world/` — `atmosphere.ts` (deterministic sky: day
phase, per-day weather, gradients) · `provinces.ts` (all 11 provinces; the ten existing regions read
from `levelContent.ts`, never re-declared) · `ambientLife.ts` (seeded sprite generation) ·
`LivingWorld.tsx` · `livingWorld.css` (CSS-only motion) · 17 tests. Prerequisite §4.5 closed in the
same change: `src/index.css` reduced-motion guards + `src/lib/celebrate.ts` (reduced-motion-aware
confetti, all three call sites). Implementation notes: `math-adventure-rpg/docs/LIVING_WORLD.md`.

**Verified:** `tsc --noEmit` clean · 376/376 tests · Community chunk **3.3 kB gzipped**, lazy ·
`play-store` build emits **no** Living World asset · Play bundle **+0.54 KiB / +1 chunk, entirely the
accessibility fix and nothing from MA-1**.

**Three findings worth carrying forward:**

1. **A runtime flag is not enough to keep code out of the APK.** Gating only on `isEnabled()` still
   caused Rollup to emit the Living World chunk into the `play-store` build *and* the service-worker
   precache — unreachable, but shipped and cached. §4.11's "zero net growth" needs a **build-time**
   condition (`import.meta.env.VITE_PROFILE`, a literal after vite's `define`) so the dead branch
   folds away. **Both gates are kept**: build-time for size, runtime for the Stable Build Principle.
   *This applies to every future MA milestone and to any World-A app adopting the edition seam.*
2. **A defect in the inherited pattern.** `early-numeracy/src/lib/daylife.ts`'s per-day seed
   `(dayOfYear * 9301 + 49297) % 233280` advances by only ~0.04/day, so with thresholds at 0.68/0.90
   the weather is **identical for roughly seventeen consecutive days**. Numeria uses an avalanche hash
   instead. ⚠️ **The defect is still live in Early Numeracy** — recorded, deliberately not fixed here
   (different app, different milestone).
3. **Night is moonlit, not dark.** The obvious deep-navy night sky was built and rejected on sight:
   the game renders copy in `text-black`, so a dark sky put black text on a dark background and the
   question became hard to read — *the world competing with the maths*. Night is now expressed by the
   moon, stars, fireflies and a shadowed ground over a light sky. A test asserts **every stop of every
   sky gradient clears 7:1 contrast against black.** §1 made operable as a test, not a wish.

**Scope note — where Meadow Gate lives.** This section previously anticipated adding a `P1_WORLDS`
array to `src/game/levelContent.ts`. It was **not** added there: game content ships inside the Play
build and §4.3 requires that bundle unchanged. Meadow Gate is currently pure atmosphere with no
gameplay surface, so the web layer is its correct home. If it ever gains a level-intro banner, that
banner — and only then — belongs in game content.

**Still open:** MA-1 has passed structural review only. Whether Meadow Gate *feels* alive to a real
child is an **experiential** question ([`../patterns/experiential-gates.md`](../patterns/experiential-gates.md)),
and no such gate is attached to MA-1 — it carries no Welcome Moment and no Guide.

---

*Original intent, kept for the record:*

Ambient life, no gameplay change: sky and day phase · per-day-stable weather · drifting clouds ·
birds · butterflies · province-appropriate atmosphere. Deterministic and never-flickering.

**The proven pattern to extend:** `early-numeracy/src/lib/daylife.ts` achieved a convincing living
world in **57 lines with zero image assets** — pure functions over the device clock, CSS gradients,
emoji, and a stable per-calendar-day pseudo-random for weather. Numeria's ambient layer inherits that
approach wholesale. *This is not a speculative system; it is an extension of proven work.*

**Prerequisite (must land in MA-1, not later):** close the reduced-motion gap — see §4.5.

### MA-2 — Micro-animations ✨

Delight at every interaction. Correct → a flower blooms. Wrong → the guide gently points. The existing
`handleAnswer()` funnel (`src/game/Game.tsx:650`) already sequences sound, speech, haptics, confetti
and companion emotion, so there is exactly one hook point.

**The unclaimed opportunity:** `awardBadge()` (`src/game/Game.tsx:507`) is the single choke point for
all **10 achievements** — and it currently celebrates with **nothing at all**. A badge silently
appears in a drawer. This is the highest emotional return per line of code in the entire codebase.

### MA-3 — Concept animations 🍎

Show, don't read. Two apples join a group of two; a pizza rotates and one slice leaves. Five seconds,
then play resumes. **The most educationally load-bearing layer** — this is where animation does the
teaching rather than decorating it, and where the Four-Purpose Test's *Teach* case lives.

Natural home: the existing **reveal panel** (`Game.tsx:1161-1185`), shown on a second wrong attempt
with the correct answer and `problem.explanation`. A learner who has just missed something twice is
precisely the learner a concept animation should meet.

### MA-4 — Story episodes 📖

Gameplay-integrated narrative. *"The Lost Bridge"* — the bridge needs 5 logs, the learner counts them,
the bridge is rebuilt, the journey continues. The maths **is** the story beat; the story is not a
wrapper around a question. Province-anchored, so each region earns its identity.

Natural triggers already exist: `isP2WorldEntry` / `isP3WorldEntry` / `isP4WorldEntry`
(`Game.tsx:616-618`) detect crossing into a new province and currently show only a coloured banner.

### MA-5 — Story Theatre 🎭 *(includes cinematics)*

Unlockable, replayable, offline animated episodes. **Not gameplay** — a place to revisit the journey.

**Scope note:** the founder's original five-layer vision listed cinematics (opening sequences, world
introductions, festival celebrations) as a separate sixth phase. They fold into MA-5 because they are
Story Theatre's *presentation mode*, not a distinct capability — same renderer, same asset ceiling,
same skip rules. Recorded so the divergence is deliberate and visible rather than an omission.

---

## 4. Constraints & non-negotiables (the hard limits)

Every constraint below traces to a real file, a ratified principle, or a recorded product decision.

1. **The rejection constraint.** The "Expert Approved" badge was **refused 2026-06-17 for text volume
   + disruptive sounds.** Every story beat is measured against this. Less text and calmer sound for
   younger ages is a product rule, not a preference.
2. **Art ceiling = animated storybook SVG, built in code.** SVG + CSS gradients + gentle animation +
   emoji. **No illustrator, no asset pipeline, no raster art packs, no game engine, no physics
   library.** Keeps Numeria tiny and offline-forever. (Precedent: NK §4.2; proof: `daylife.ts`.)
3. **The Play build must not change.** Verification bar from Baseline 2026.1: the `play-store` profile
   reproduces the identical bundle hash. Everything ships behind `isEnabled()`, which double-gates on
   **profile AND web shell**, so no experiment can light up inside the Capacitor WebView.
4. **Determinism.** `daylife.ts`'s rule — *"no randomness that flickers."* Weather is stable for a
   whole calendar day. Ambient state is a pure function of the clock, never a live random.
5. **Reduced motion, fully.** `<MotionConfig reducedMotion="user">` in `App.tsx` covers **Motion
   components only** — the hand-rolled CSS keyframes in `src/index.css` (`popIn`, `pulseBeat`) and
   **both `canvas-confetti` bursts ignore the OS setting entirely.** Closing that gap is an **MA-1
   prerequisite**, not a later cleanup. Adding motion on top of a half-covered guard would make an
   accessibility gap worse at exactly the moment it becomes most visible.
6. **No runtime AI** (DNA 17). Scripted line pools selected contextually — never generative.
   #FreeForever cannot absorb per-learner API cost. Model: `early-numeracy/src/constants/pip.ts`
   (pools + `pipLine()` picking at random while avoiding immediate repeats).
7. **Narration is serial.** `useNarration` calls `synth.cancel()` before each utterance, so a new line
   **kills the previous one**. There is no VO queue. Multi-line dialogue requires one to be designed
   in MA-4 — this is a known architectural gap, not an oversight. Also: the naive `speak()` is banned
   ecosystem-wide (Science Sprouts shipped silent because of it); MAR owns the canonical
   `useNarration` and must keep it canonical.
8. **Subtitles are mandatory.** DNA 13: *"no audio-only or visual-only content without an
   alternative."* **No subtitle system exists today.** The precedent to generalise already lives in
   `TUTORIAL_SLIDES`: a `body` field (3–4 words, for non-readers) paired with a `say` field (the
   warmer spoken sentence). Every narrated Numeria line needs both.
9. **i18n gap — the trap.** `levelContent.ts` is **100% hardcoded English** (tutorial slides, level
   intros, hints, region names, badge descriptions) while `i18n.test.ts` only enforces parity between
   `en.ts` and `zu.ts`. New story content will inherit that gap **and the test will not catch it.**
   All Numeria copy routes through the dictionaries. isiZulu ships DRAFT until native-speaker review.
10. **PWA precache gap.** `globPatterns` in `vite.config.ts` omits `mp3|ogg|webm|m4a|json|webp` — any
    recorded voice-over, music file, or Lottie JSON would be **silently excluded from the service
    worker and break offline**. Recorded audio is **out of scope for Numeria v1** (procedural Web
    Audio only, as today); if it is ever introduced, this glob is the blocking prerequisite.
11. **Performance budget (net-new — no prior art in the Brain).** `research/README.md` lists offline
    bundle benchmarks as a known research gap. Numeria proposes the ecosystem's first:
    - the Numeria web-only chunk stays **lazy-loaded** and outside the initial paint;
    - **60fps on a 3-year-old mid-range Android** (DNA 13's stated device bar);
    - province scenes lazy-load per province, never all at once;
    - **no net growth in the `play-store` bundle. Zero. Verified by hash.**
    *Reclaimable headroom already identified:* `pwa-512x512.png` and `maskable-512x512.png` are
    **byte-identical 434 KB duplicates** — ~850 KB of a 2.4 MB `dist/`. Not touched here (it is
    Play-affecting), but recorded so a future release can reclaim it.
12. **Navigation contract** — [`patterns/world-a-navigation.md`](../patterns/world-a-navigation.md):
    back is never destructive · no dead ends · **exit is gentle** (an audible or animated farewell,
    never a silent jump) · 64×64px nav targets (never below the 44×44 floor) · desktop parity ≥768px.
13. **No-fail.** Wrong answers already wobble rather than penalise, and the second attempt teaches
    rather than blocks. Numeria never introduces a timer, a score, a percentage, or a losable state.

---

## 5. Cross-cutting systems

- **Companion and Guide are two entities, not one** (founder decision, 2026-07-20). A
  player-renamed companion **cannot serve as canonical narration** — the world cannot refer to a
  character whose name it does not know. So the roles split:

  | | **Companion** | **Guide** |
  |---|---|---|
  | Identity | chosen by the learner, **renameable** | **fixed** |
  | Role | emotional support | narrator |
  | Behaviour | reacts to gameplay, celebrates achievements | introduces provinces, explains the world, welcomes the learner, appears in Story Theatre |

  These are fundamentally different jobs, and **Sparky is not made to do both.** The existing
  companion (`src/game/Companion.tsx` — 6 emotions, 24 lines, default **"Sparky" 🐉**) stays exactly
  what it is: the learner's own.

  The Guide is specified in its own document:
  [`numeria-guide-constitution.md`](./numeria-guide-constitution.md) — purpose & belief · the
  **Keeper** archetype · personality, presence & voice · appearance *principles* · **the four Guide
  moments** (Welcome · Orientation · Encouragement · Celebration) and the silence between them ·
  architectural integration. It **extends** MA-0 and never redefines it.

  **🔓 Guide identity: FOUNDER DECISION PENDING.** Deliberately not invented — *once you name the
  guide, that character becomes part of Numeria's identity for years.* Ecosystem convention
  constrains it: **each world gets its own guide** (Ollie/Fifi/Lulu are Early Literacy's, 🐿 Pip is
  Number Kingdom's, Nova is Space Explorer's) — personalities are never borrowed, so **Numeria may
  not use Pip**.
- **Environment as reward** — the world visibly responds to progress; no new score surface.
- **Narration & subtitles** — every spoken line has a visual form (§4.8). Audio hierarchy already
  established and preserved: **narration > feedback SFX > background music**, with
  `duckForNarration()` ramping music to 0.18 gain during speech.
- **Accessibility** — voice-first, replay, large targets, reduced motion, high contrast, visual mode.
  Carried from the current app, **not regressed**. `scripts/a11y-audit.mjs` (Playwright + axe-core,
  WCAG AA contrast across 7 seeded URLs including `/play?phase=1`) is the existing check.
- **The Welcome Moment — a compliance gap to close.** DNA **Principle 18** applies to *every* World-A
  app, and **Math Adventure RPG is absent from its example list.** Numeria must deliver one: shown
  **once ever** (persisted flag) · warm and narrated · the single "begin" tap doubles as the browser's
  first user gesture so it **unlocks audio** · *"Welcome to Numeria."*

---

## 6. Definition of Done (Numeria v1)

- The learner **arrives in a place**, not a menu; the ten provinces are visible and coherent.
- The world is **alive** (MA-1) and **responds** to progress — no new numbers, stars, or percentages.
- Achievements **celebrate** (MA-2); concepts are **shown** before they are read (MA-3).
- At least one province carries a **story episode** where the maths *is* the story beat (MA-4).
- **Story Theatre** is reachable, replayable, and fully offline (MA-5).
- The Welcome Moment exists and unlocks audio.
- Every animated sequence is **skippable or brief**; nothing blocks a learner from continuing.
- `mathEngine.ts` and the 65-level progression run **unchanged**.
- Still: fully offline · no runtime AI · no-fail · `tsc --noEmit` 0 · all tests green · clean build ·
  **`play-store` bundle hash unchanged** · passes a **real-child play-test** · and re-earns the
  Google Play **"Expert Approved"** bar that was lost on 2026-06-17.

---

## 7. Execution protocol for the next AI

1. **Do not build anything until MA-0 (the Constitution) is founder-frozen.** Blueprint → Freeze →
   Build.
2. Build **one MA milestone at a time**, fully, then **await the founder's Freeze** before the next.
   **Never self-declare a freeze.**
3. **Never rewrite the educational engine.** `mathEngine.ts`, `phases.ts` progression, and the save
   format are frozen. Numeria is a wrap.
4. **Everything is web-only and flag-gated.** If a change can affect the `play-store` bundle, it does
   not belong in this blueprint. Verify by hash after every milestone.
5. Apply the **Four-Purpose Test** to every proposed element. Cool is not a purpose.
6. Honour the founder's working style: plan-first, phase-by-phase, don't invent scope.
   **This blueprint is the scope.**
7. After each milestone: `tsc --noEmit` 0 · `npm run test` green · clean build · `play-store` hash
   unchanged · deploy-verify · update this doc + [`math-adventure-rpg.md`](./math-adventure-rpg.md) +
   `SESSION_HANDOFF.md` · commit + push app and Brain · record the play-test outcome.
8. **Do not extract a shared Story Engine.** Numeria's story system stays app-local
   (`src/web/numeria/`) until DNA Principle 11's two-app trigger fires. See **D-16**.
9. **One documented exception to Blueprint → Freeze → Build.** The
   [Guide Constitution](./numeria-guide-constitution.md) ratifies in **two stages** — *architectural
   ratification* (unblocks building the Guide + Welcome Moment) then *experiential freeze* (after a
   real learner has passed the **🚪 First Welcome Gate**). Applied naively the rule deadlocks: a
   Guide cannot be validated without a Welcome Moment, which cannot be built before the freeze.
   **This exception applies to the Guide Constitution only.** MA-0 and every MA milestone freeze
   normally — and MA-1's Living World needs no Guide, so nothing is blocked.

## Related
- [`numeria-constitution.md`](./numeria-constitution.md) — MA-0 in full
- [`numeria-guide-constitution.md`](./numeria-guide-constitution.md) — the Guide (extends MA-0)
- [`math-adventure-rpg.md`](./math-adventure-rpg.md) — app memory
- [`math-adventure-release-policy.md`](./math-adventure-release-policy.md) — editions, channels, graduation
- [`number-kingdom-roadmap.md`](./number-kingdom-roadmap.md) — the template, and the app Numeria is *not*
- [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) → **D-16**
- [`../baselines/2026.1-community-release.md`](../baselines/2026.1-community-release.md) — the seam this builds on
