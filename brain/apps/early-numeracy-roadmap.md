# 🔒 Early Numeracy — Complete Product Roadmap (World A) — LOCKED

> **Status: LOCKED blueprint (2026-07-03). Authored by the founder.**
> This is the **authoritative execution plan** for Early Numeracy. The next AI **executes this**;
> it does **not** invent features or scope. It supersedes the older "Implementation phases" in
> [`early-numeracy.md`](./early-numeracy.md).
>
> **The brief:** don't "finish the app" — **finish the product.** Early Literacy became a
> platform-backed educational experience; Space Explorer a complete learning world; **Early Numeracy
> gets exactly the same treatment.**

---

## Project status

| | |
|---|---|
| **Project** | Early Numeracy |
| **World** | World A (offline learning) |
| **Target ages** | **3–5** (this roadmap; earlier notes said 3–7 — defer to this plan) |
| **Platform** | The People's Home |
| **Core platform** | TPH Core v1.0 (Frozen) — see the **naming note** below |
| **Repo** | `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-numeracy` (PRIVATE, branch `master`) |
| **Live** | https://early-numeracy.pages.dev/ — linked on The People's Home (Foundations) |
| **Status** | In Development — **Phase 2 BUILT & LIVE (2026-07-04); awaiting real-child play-test to Freeze. Phase 2.5 is next.** |

### Where the code actually is right now (start here)
**Phase 2 is built and deployed** (`fa777a6`, live at early-numeracy.pages.dev). The five stubs are now
six real, no-fail, audio-guided modules: `counting-garden`, `which-is-more`, `number-shapes`,
`pattern-maker`, and `make-five` + `make-ten` (the old `make-five-ten` was split). Shared kit added
(`components/module-kit.tsx`), a progress store (`lib/progress.ts`, schema-drift-safe), and an
environment-as-reward **Math Village** that grows on the home screen. tsc 0 / clean build / logic
invariants checked / deploy verified (live manifest + chunk hashes match).

**The one gate left before Freeze: a real-child play-test** (a human step — not yet done). Once that
passes, Freeze Phase 2 and start **Phase 2.5 (Numeracy Confidence)**.

Phase 1 (still true underneath): home screen, narration + instruction system (audio/visual paths
separated), child-lock, session state, offline PWA. Audit + security + bug fixes done (`8a03f92`,
`de7e06f`, and Phase-2 progress loader default-merge).

### ⚠️ Naming note (per decision D-13)
This roadmap says **"TPH Core v1.0 (Frozen)"** and lists Event Bus · Companion · Vocabulary ·
Discovery Book · Environment · Tracing · Progress. That is the **frozen educational engine set**
Early Literacy ships — which was **renamed "TPH Learning Engines"** (D-13) to free the name "TPH Core"
for the canonical `@tph/core` SDK. So: **build Early Numeracy on the "TPH Learning Engines" contracts**
(the same shared engine set Early Literacy consumes). Do **not** confuse it with `@tph/core`. Early
Numeracy currently has its **own** hooks (`useNarration`, `useInstruction`, `useSessionState`,
`useChildLock`) and does not yet consume that engine set — adopting it is part of "finishing the product."

---

## Mission

Help every child build strong mathematical thinking through **exploration, play, observation, and
confidence — not memorisation.** Children should leave believing:

> "Math is something I can understand."

---

## Educational philosophy (World A principles — non-negotiable)

Offline First · Audio First · Confidence Before Correction · No Failure States · No Timers ·
Child-Led Discovery · Learning Through Play · Environment As Reward · Companion Guided Learning ·
Ages Before Grades · No Ads · **#FreeForever**

---

## Product structure (phases)

Each phase ends with **Freeze** (see Quality Gates). Do not start the next phase until the current
one passes every gate.

### Phase 1 — Foundation ✅ DONE
Platform shell · navigation · Home · Village · Parent Corner · offline storage · TPH (Learning Engines) integration.

### Phase 2 — Number Discovery — ✅ BUILT & LIVE (2026-07-04, `fa777a6`); play-test pending → Freeze
The six core modules, all real no-fail gameplay (Make Five / Make Ten split out from `make-five-ten`).
- **🌼 Counting Garden** ✅ — tap-to-count, one-to-one correspondence, spoken counting, number recognition; wrong tap = gentle wobble.
- **🍎 Which Is More?** ✅ — compare quantities: more / fewer / equal (equal via the centre button); wrong tap re-asks.
- **✏️ Number Shapes** ✅ — trace the numeral by connecting ordered dots (drag or tap, any order, forgiving); numeral shown with quantity; 1–10.
- **🎨 Pattern Maker** ✅ — AB / ABC / AABB / ABB; gap at end then middle; tap-to-fill.
- **⭐ Make Five** ✅ — number composition on a five-frame; part–whole fact spoken.
- **🌟 Make Ten** ✅ — ten frame; part–whole thinking (shared engine with Make Five).
- **→ Freeze Phase 2** — *blocked only on the real-child play-test.*

### Phase 2.5 — Numeracy Confidence
Before larger concepts. Daily challenges · favourite activities · replay · independent practice ·
recognition games · number hunts · matching games · hidden objects · real-world counting. Play-test. **Freeze.**

### Phase 3 — Numbers Everywhere
*Mission: children discover mathematics exists everywhere.*
Scenes: Kitchen · Garden · Bedroom · Playground · Shops · Road · Home.
Activities: count apples · count birds · find 3 windows · find circles · count chairs · measure objects ·
compare sizes · sort colours. **Freeze.**

### Phase 4 — Addition Adventure
Joining groups · visual addition · story problems (animals, fruit, blocks, objects). **No equations first — concrete experiences.**
Modules: Add Together · Magic Basket · Feed the Animals · Treasure Chest · Bridge Builder. **Freeze.**

### Phase 5 — Taking Away
Subtraction through stories: birds fly away · cookies eaten · fish swim away · blocks removed. **Still visual.** **Freeze.**

### Phase 6 — Shapes World
2D shapes: circle · square · triangle · rectangle · oval · heart · star.
Activities: find shapes · build pictures · shape sorting · tracing · real-world objects. **Freeze.**

### Phase 7 — Measurement
Big/small · tall/short · heavy/light · long/short · full/empty.
Activities: compare · arrange · measure · estimate. **Freeze.**

### Phase 8 — Time & Daily Life
Morning/afternoon/night · days · simple clocks · daily routines · sequences. **Freeze.**

### Phase 9 — Money (South African context)
Coins · notes · buying · selling · simple change · pretend shop. **Freeze.**

### Phase 10 — Data & Sorting
Sort · group · count · graphs (favourite fruit, favourite colour, animal chart, weather chart). **Freeze.**

---

## Cross-cutting systems (integrate throughout)

### Companion system (use TPH Learning Engines)
**Ollie** — patient teacher · **Fifi** — explorer · **Lulu** — celebration. **Never break personality consistency.**

### Environment — the Math Village
The village **evolves as reward** (instead of stars): correct learning grows trees, flowers,
butterflies, birds, streams, windmills, bridges, animals, community. **Children literally build the village.**

### Discovery Book — "My Number Book"
Collect: numbers · shapes · patterns · animals counted · objects · achievements · favourite activities ·
replay narration · illustrations.

### Vocabulary integration (Vocabulary Engine)
Every math concept registers: more · less · equal · circle · triangle · five · ten · pattern · long ·
short · heavy · light … stored in the Vocabulary Engine.

### Parent Corner
Progress · skills mastered · favourite activities · replay suggestions · offline games ·
real-world practice · conversation starters · play ideas.

### Accessibility
Voice-first · replay narration · large buttons · reduced motion · high contrast · tap alternative ·
visual instruction mode · motor accessibility.

---

## Platform integration

**Consume the TPH Learning Engines (the frozen "TPH Core v1.0" set) via public contracts ONLY.**
Do **NOT** modify: Event Bus · Companion Engine · Vocabulary Engine · Discovery Book Engine ·
Environment Engine · Tracing Engine · Progress Engine.

### New application engines (introduce only if required)
Number Engine · Pattern Engine · Measurement Engine · Problem Engine. These stay **application-layer**
until proven reusable across apps (Principle 11 — promote to platform only on the second real use).

---

## Quality gates — every phase must pass, then Freeze

Educational review · Child UX review · Accessibility review · Offline review · Performance review ·
Regression testing · Production build · **Zero lint/type errors** · Play-testing → **Freeze.** Only then proceed.

---

## Google Play "Expert Approved" readiness (same bar as the Math Adventure RPG review)

**Design & appeal:** warm, inviting, age-appropriate visuals; calm, non-distracting animations;
consistent companion personalities.
**Words & sounds:** voice-first guidance for every activity; minimal on-screen text for ages 3–5;
gentle, encouraging corrective feedback; no harsh buzzers or repetitive background music.
**Accessibility:** large touch targets; visual demonstrations alongside narration; support for
different motor and hearing needs.
**Safety & privacy:** fully offline; no ads; no tracking; no in-app purchases; no external links
exposed to children.

---

## Production Definition of Done

The app is complete **only** when:
- Every planned numeracy domain is implemented and polished.
- All modules integrate cleanly with the TPH Learning Engines (frozen v1.0) via **public contracts only**.
- The educational progression is coherent from counting through early problem solving.
- Discovery Book, Vocabulary Engine, Environment Engine, Companion Engine, and Parent Corner are **fully integrated**.
- It passes internal QA, child play-testing, accessibility review, and offline verification.
- Production builds are clean with **zero lint/type errors**.
- It meets the **Google Play "Expert Approved"** quality bar.

> This roadmap turns Early Numeracy into a complete, production-ready World-A product — not a
> collection of math activities.

---

## Execution protocol for the next AI

1. **Start at Phase 2.** Phase 1 is done and live.
2. Build **one phase at a time**, fully, through its Quality Gate, then **Freeze** before the next.
3. Consume the **TPH Learning Engines** via public contracts; never modify them.
4. Honour the founder's working style ([[feedback_collaboration]]): work phase-by-phase, don't rush
   ahead or invent scope — **this locked plan is the scope.**
5. After each phase: `tsc --noEmit` 0 errors, clean `vite build`, update this app's Brain docs +
   `SESSION_HANDOFF.md`, commit, deploy verify, and record the play-test outcome.

## Related
- [[tph-early-literacy-status]] — the in-house/product playbook this mirrors
- [`early-numeracy.md`](./early-numeracy.md) — app memory + the completed audit/security/bug record
- [[skills-library]] — `bug-identifier` / `bug-fixer` for the per-phase quality gate
- [[tph-app-ecosystem]] · [[project-state]]
