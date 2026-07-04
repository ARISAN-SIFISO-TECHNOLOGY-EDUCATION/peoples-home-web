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
| **Status** | In Development — **Phase 2 FROZEN ✅. Phases 2.5, 3, 4 & 5 BUILT & LIVE (2026-07-04); play-test pending → Freeze. Phase 6 is next.** |

### Where the code actually is right now (start here)
**Phase 2 is FROZEN** (founder-authorized 2026-07-04, `fa777a6`): six real no-fail modules —
`counting-garden`, `which-is-more`, `number-shapes`, `pattern-maker`, `make-five` + `make-ten` (old
`make-five-ten` split). Shared kit (`components/module-kit.tsx`), progress store (`lib/progress.ts`,
schema-drift-safe), environment-as-reward **Math Village**.

**Phase 2.5 (Numeracy Confidence) is built and deployed** (`22b5a0b`): a 🌞 **Today** home surface
(daily suggested activity + favourite replay + spoken real-world-counting nudge) and two **practice**
games — 🔢 **Number Match** (numeral↔quantity recognition) and 🔍 **Number Hunt** (find-the-called-
numeral). Home screen now groups modules into "Play & Learn" (the six) and "🎯 Practice"
(`ModuleDef.group`). tsc 0 / clean build (8 lazy chunks, precache 23, zero external) / logic invariants
checked / deploy verified.

**Phase 3 (Numbers Everywhere) is built and deployed** (`dacd6a6`): a 🌍 **Numbers Everywhere** module
with seven real-world scenes (Kitchen · Garden · Bedroom · Playground · Shops · Road · Home), each a
no-fail COUNT ("count the apples") or FIND ("find 3 windows") task over tagged scene objects. Added a
third home section **"🌍 Explore"** (`ModuleGroup` gained `'explore'`). App description made evergreen
(`680afbc`).

**Phase 4 (Addition Adventure) is built and deployed** (`7da1f98`): a ➕ **Addition Adventure** module —
concrete visual addition (no equations). Two groups are shown; the child taps each item into a
container while the voice counts up, then hears "a and b make total". One join-and-count engine cycles
the five roadmap themes (Add Together · Magic Basket · Feed the Animals · Treasure Chest · Bridge
Builder). New **"➕ Adding"** home section (`ModuleGroup` gained `'operations'`).

**Phase 5 (Taking Away) is built and deployed** (`420280d`): a ➖ **Taking Away** module — subtraction
as concrete take-away stories (no equations). A group is shown; the child sends some away (birds fly,
cookies eaten, fish swim off…), the "how many left" count ticks down, then they hear "n take away m
leaves left". One take-away engine cycles five themes (Birds Fly Away · Cookie Time · Fish Swim Away ·
Blocks Away · Balloons Float Away). Lives in the now "➕➖ Adding & Taking Away" home section.

**The gate left before freezing 2.5–5: a real-child play-test** (human step). Once confirmed, Freeze
those phases and start **Phase 6 (Shapes World)**.

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

### Phase 2 — Number Discovery — ✅ FROZEN (2026-07-04, `fa777a6`; founder-authorized)
The six core modules, all real no-fail gameplay (Make Five / Make Ten split out from `make-five-ten`).
- **🌼 Counting Garden** ✅ — tap-to-count, one-to-one correspondence, spoken counting, number recognition; wrong tap = gentle wobble.
- **🍎 Which Is More?** ✅ — compare quantities: more / fewer / equal (equal via the centre button); wrong tap re-asks.
- **✏️ Number Shapes** ✅ — trace the numeral by connecting ordered dots (drag or tap, any order, forgiving); numeral shown with quantity; 1–10.
- **🎨 Pattern Maker** ✅ — AB / ABC / AABB / ABB; gap at end then middle; tap-to-fill.
- **⭐ Make Five** ✅ — number composition on a five-frame; part–whole fact spoken.
- **🌟 Make Ten** ✅ — ten frame; part–whole thinking (shared engine with Make Five).
- **→ Freeze Phase 2** — *blocked only on the real-child play-test.*

### Phase 2.5 — Numeracy Confidence — ✅ BUILT & LIVE (2026-07-04, `22b5a0b`); play-test pending → Freeze
Before larger concepts. Delivered:
- **🌞 Today** home surface — daily suggested activity · favourite replay (most-played) · spoken
  real-world-counting nudge (from the transfer-prompt pool). Suggestions, never tasks or scores.
- **🔢 Number Match** — numeral↔quantity recognition/matching, both directions alternating by level.
- **🔍 Number Hunt** — find-the-called-numeral among decoys (three finds per round), spoken target cue.
- Home grouped into "Play & Learn" (the six) + "🎯 Practice" (the two confidence games).
- **→ Freeze Phase 2.5** — *blocked only on the real-child play-test.*

### Phase 3 — Numbers Everywhere — ✅ BUILT & LIVE (2026-07-04, `dacd6a6`); play-test pending → Freeze
*Mission: children discover mathematics exists everywhere.*
Delivered as the 🌍 **Numbers Everywhere** module — seven scenes (Kitchen · Garden · Bedroom ·
Playground · Shops · Road · Home). Each scene renders tagged objects and poses a no-fail task:
- **COUNT** a kind of thing — "count the apples", "count the birds", "count the chairs".
- **FIND** some of them — "find 3 windows", "find the round things" (shape find via a `round` tag).
Right taps count up aloud; other taps wobble gently. Object tags (apple/fruit/round/window/car/…) make
the tasks contextual without new mechanics.
*(Deferred to their own phases to avoid duplication: "measure/compare sizes" → Phase 7 Measurement;
"sort colours" → Phase 10 Data & Sorting.)*
- **→ Freeze Phase 3** — *blocked only on the real-child play-test.*

### Phase 4 — Addition Adventure — ✅ BUILT & LIVE (2026-07-04, `7da1f98`); play-test pending → Freeze
Joining groups · visual addition · **no equations — concrete experiences.**
Delivered as the ➕ **Addition Adventure** module: two groups of things are shown; the child taps each
one to move it into a container while the voice counts up, then hears the part-whole fact
("three and two make five"). The five listed modules — **Add Together · Magic Basket · Feed the Animals ·
Treasure Chest · Bridge Builder** — are the five **themes** this one adventure cycles through (each a
different item + container). Sums grow to 5, then to 10. No timers, no fail state.
*(Design note: kept as one "Addition Adventure" card rather than five separate cards — same mechanic,
calmer home screen for ages 3–5 — while still delivering all five themed experiences.)*
- **→ Freeze Phase 4** — *blocked only on the real-child play-test.*

### Phase 5 — Taking Away — ✅ BUILT & LIVE (2026-07-04, `420280d`); play-test pending → Freeze
Subtraction through stories — **still visual, no equations.** Delivered as the ➖ **Taking Away** module:
a group is shown; the child taps items to send them away (birds fly · cookies eaten · fish swim away ·
blocks removed · balloons float away), the "how many left" count ticks down, and they hear
"n take away m leaves left". One take-away engine cycles the five themes; N grows to 5, then to 9. Once
the story amount is gone the rest lock — no over-removing, no fail state.
- **→ Freeze Phase 5** — *blocked only on the real-child play-test.*

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
