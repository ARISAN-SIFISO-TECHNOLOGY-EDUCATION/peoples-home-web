# Early Literacy

> 🧮 **Foundations** · ages **3–7** · **✅ LIVE — installable offline PWA** (World A) ·
> repo `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy` (private) · **https://early-literacy.pages.dev/** ·
> Product name: **Early Literacy Village** ("Magical Literacy Village") ·
> Integrated into the Brain 2026-07-02 · **AI dropped + deployed + offline-PWA + Phase-1 audit fixes 2026-07-02.**
>
> This is v3 Foundations slot **#4 "Early Literacy Games"** — now actually built.
> Built externally (Google AI Studio / Gemini). This memory integrates it as a
> first-class World-A app; it does **not** redesign it.

---

## 1. What it is

An offline-first, audio-guided "magical village" that helps children aged **3–7** discover
the joy of language — sounds, letters, first words, and stories — through play. A child taps,
listens, and speaks their way through eight small learning places on a village map. No reading
is required to use it; narration is the primary interface.

It is the **literacy** counterpart, for the youngest learners, to [`early-numeracy.md`](./early-numeracy.md)
— the pre-reading on-ramp that sits *below* [`read-africa.md`](./read-africa.md) (ages 3–17)
in the Foundations pillar.

**Mission:** give every South African child a free, offline, joyful path into language before
formal schooling — sounds before letters, letters before words, words before reading, always
confidence before correction.

**Vision:** a child who cannot yet read can still *learn to read*, alone or beside a caregiver,
on a low-end phone with no data and no account — and arrive at ReadAfrica already in love with
language.

**Educational philosophy:**
- **Audio-first.** The interface is secondary; clear speech and phonic sound dominate.
- **Confidence over punishment.** No red "wrong" marks, no fail state, no game-over. Errors
  trigger a cheerful companion helper, never a scold.
- **Ages, not grades.** Four age bands (3–4, 4–5, 5–6, 6–7), never a grade label.
- **Play, not drill.** Every activity is a place to explore, not a test to pass.

---

## 2. Category & audience

| Field | Value |
|---|---|
| **Pillar** | Foundations |
| **v3 slot** | #4 (was "Early Literacy Games", 🔮 Future → now built) |
| **Capability gained** | Emergent literacy — phonemic awareness, letter knowledge, first-word decoding |
| **Primary audience** | Children ages 3–7 (pre-school → early Grade 1) |
| **Secondary audience** | Parents / caregivers playing alongside (Grown-Up Corner) |
| **World** | A — offline, no login, no server, no tracking, #FreeForever |
| **DNA** | Matches the Math Adventure / ReadAfrica / Early Numeracy World-A pattern |

---

## 3. Why it exists — the gap

ReadAfrica covers literacy across ages 3–17, but a true *non-reader* aged 3–5 needs a home
built entirely around sound and play — before letters carry meaning. Early Literacy fills that
gap the way Early Numeracy fills it for number sense: pure sensory, audio-first play that ends
by handing a confident, language-curious child up to ReadAfrica. It is an **on-ramp, not a
replacement.**

---

## 4. The educational journey (curriculum phases)

The village is authored as a four-phase progression, wrapped by a navigation framework:

```
Phase 1  Listening        →  Listening Forest   (hear & discriminate sounds)
Phase 2  Sound Discovery  →  Sound Safari       (phonemic awareness, first sounds)
Phase 3  Letter Garden    →  Letter Garden      (letter shapes + sounds, tracing)
Phase 4  First Words      →  Word Builder       (assemble letters into real words)
         ─────────────────────────────────────────────────────────────────
         Navigation Framework  (hierarchical back · swipe · resume · farewell)
         ─────────────────────────────────────────────────────────────────
         → Ready for Phase 4.5
```

**Status: Phases 1–4 COMPLETE. Navigation framework COMPLETE. Phase 4.5 PLANNED.**

Beyond the four core phases, the village also ships four supporting places (all live in-app):
**Story Village** (cozy read-along books), **Picture Talk** (oral language / describing),
**Writing Corner** (pre-writing / letter formation) and **Everyday Language** (situational
vocabulary). These deepen the journey rather than extend the phase count.

### Companions
Three narrating companions carry the emotional layer (see the Companion Engine):

| Companion | Emoji | Personality |
|---|---|---|
| **Ollie** | owl | Calm, patient, "wise little owl" — grounding voice |
| **Fifi** | fox | High-energy, playful, "let's go!" — momentum voice |
| **Lulu** | singer | Musical, celebratory — sings the rewards |

---

## 5. Platform engines consumed (frozen — not modified)

Early Literacy consumes a set of standardised educational engines through a **type-safe Event
Bus** (`src/lib/eventBus.ts`). Engines never call each other directly — they publish namespaced
events. **No consumed engine was modified by this app.**

| Engine | File | Responsibility |
|---|---|---|
| **Event Bus** | `eventBus.ts` | Type-safe pub/sub; the only inter-engine channel |
| **Companion Engine** | `companion.ts` | Ollie/Fifi/Lulu profiles, encouragement, helper prompts |
| **Tracing Engine** | `tracing.ts` | Validates ordered coordinate taps for letter tracing |
| **Vocabulary Engine** | `vocabulary.ts` | Word retention, mastery levels (`learning`→`known`→`mastered`) |
| **Discovery Book Engine** | `discovery.ts` | Catalogue of discovered items, facts, favourites |
| **Environment Engine** | `environment.ts` | Tree/ecosystem maturation, weather-time, reward fauna |
| *(Speech Manager)* | `speech.ts` | Web Speech API TTS + phonic SFX + visual-caption fallback |

> ⚠️ **Naming note (unresolved deviation — see §12).** The app documents these engines as
> **"TPH Core v1.0" (frozen, released 2026-07)** in its own repo
> (`early-literacy/brain/architecture/04-tph-core.md`). That is a **different** engine set from
> the Brain's canonical **[TPH Core SDK](../platform/tph-core.md)** (Identity · Progress ·
> Rewards · Offline Engine · Dashboards), which is *not* frozen — it is mid-extraction from
> ReadAfrica into `@tph/core`. Two things currently share the name "TPH Core." This is flagged,
> not silently reconciled. See [`../architecture/04-early-literacy-integration.md`](../architecture/04-early-literacy-integration.md).

---

## 6. Application engines (NOT part of TPH Core)

Two engines are **application-layer**, specific to Early Literacy, and correctly excluded from
the frozen core version list:

| Engine | File | What it does |
|---|---|---|
| **Word Engine** | `wordEngine.ts` | `FIRST_WORDS_DATABASE` (10 CVC/first words with emoji, syllables, rhymes, song lyrics, story blurb); phonics map; `checkSpelling`; publishes `learning.word.mastered` + `environment.reward.earned` |
| **Reading Journey Engine** | `readingJourney.ts` | Journey milestones (Letter Sprout → Word Explorer → Star Collector → Word Champion), next-activity recommender, companion commentary keyed to progress |

**Why this matters:** these are the reference example of the correct World-A layering — an app
builds its *educational content logic* on top of shared platform *behaviour engines* without
touching the platform. See [Principle 11 (Platform Before Duplication)](../PROJECT_DNA.md) and
[Principle 14 (Modular Architecture)](../PROJECT_DNA.md).

---

## 7. Architecture

| Layer | Choice |
|---|---|
| Framework | React 19 + Vite 6 + TypeScript |
| Styling | Tailwind v4 (`@tailwindcss/vite`) |
| Animation | `motion` (Framer Motion successor) |
| Icons | `lucide-react` |
| Speech | Web Speech API via `SpeechManager` (`speech.ts`) |
| Storage | `localStorage` only — keys `peoples_home_literacy_{progress,settings,age}_v1` |
| Coordination | In-app **TPH Core Event Bus** (singleton, type-safe) |
| Hosting (planned) | Cloudflare Pages PWA (not yet deployed) |

**Shape:** `App.tsx` holds `progress` / `settings` / `ageGroup` state, persists to `localStorage`
on every update, and switches a single active module over the `VillageMap`. Modules receive
`progress`, `settings`, `onUpdateProgress`, `onClose`. Rewards flow through the Event Bus, not
direct calls.

### Navigation model
This app introduced the **World-A navigation standard** — documented as a reusable pattern in
[`../patterns/world-a-navigation.md`](../patterns/world-a-navigation.md). In this app:
- **Hierarchical back** — every module exposes an `ArrowLeft` back control and an `onClose`
  handler returning to the village map; modals close to the map.
- **Swipe-to-go-back** — on mobile (`< 768px`) a left→right swipe (>100px, low vertical drift)
  closes the active module / modal, dispatching a `tph-back-gesture` event.
- **Companion farewell** — a `bubble-pop` sound plays on back, the audible "goodbye" cue.
- **State preservation** — progress is already in `localStorage`; returning resumes in place.

### Offline model
100% offline: **installable PWA** (service worker precaches the full shell; SPA navigateFallback),
zero network calls, all assets bundled, all state local. Speech uses on-device TTS; if synthesis
fails it falls back to timed visual captions (never silence where a voice is expected). Satisfies
[Principle 2 (Offline First)](../PROJECT_DNA.md).
> **Fixed 2026-07-02:** narration previously fetched some clips from `actions.google.com` (a
> Google-AI-Studio remnant) — removed, so the app now truly makes zero network calls. See §12.

### Accessibility model
`AccessibilitySettings` exposes `narrationSpeed`, `visualMode`, `reducedMotion`, `highContrast`.
Age selector uses large emoji buttons; no reading required to start; high-contrast restyles the
whole document. Aligns with [Principle 13 (Accessibility by Default)](../PROJECT_DNA.md) and the
[voice-first](../patterns/voice-first.md) pattern — Early Literacy is a strong future entry there.

---

## 8. Current state

**✅ LIVE at https://early-literacy.pages.dev/** as an **installable offline PWA** (Cloudflare
Pages, deployed 2026-07-02). Built externally (Google AI Studio / Gemini); the auto-added AI was
**dropped** so it ships as a true `#FreeForever` app. Repo
`ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy` (PRIVATE, transferred from `SifisoScS` on
2026-07-02), local checkout `C:\Users\sifis\Next-Level-Projects\early-literacy`. Phases 1–4 +
navigation framework complete; **Phase-1 audit fixes applied** (see §12). For live facts see
[`../../ECOSYSTEM.md`](../../ECOSYSTEM.md); for status see [`../../ROADMAP.md`](../../ROADMAP.md).

---

## 9. Future direction / roadmap

- **Remaster backlog (Phases 2–5)** — see §12. Next up: M3 (single tree-stage owner), M4
  (engine contract↔code truth + `@types/react`), M8 (code-split).
- **Add to the site** — surface a live card on peoples-home-web.
- **Phase 4.5** — the next authored step (planned; scope TBD by founder).
- **isiZulu** — English-first today; isiZulu narration is part of the ~December 2026 batch.
- ~~Deploy~~ ✅ · ~~Drop AI~~ ✅ · ~~Fix `react-example` name~~ ✅ · ~~Offline PWA~~ ✅ ·
  ~~Migrate repo to org~~ ✅ · ~~Phase-1 audit fixes~~ ✅ (all 2026-07-02).
- **TPH Core reconciliation** — resolve the naming collision (§12); the app's behaviour engines
  are candidate contributions to (or a renamed sibling of) the canonical TPH Core SDK.

---

## 10. Known constraints

- **Content depth:** letter tracing + the Discovery catalogue cover only **9 letters**
  (A,B,C,D,E,F,G,M,S); other letters fall back to a generic triangle. 10 first words authored
  (CAT, DOG, SUN, FROG, BIRD, RAIN, TRAIN, BEE, TREE, BELL). Seed content, not full.
- **`@types/react` not installed** → `tsc` type-checking is hollow for React APIs (false
  confidence). See §12 remaster backlog.
- English-only content (isiZulu deferred to the December review, consistent with all apps).

---

## 11. Governance review (against [PROJECT_DNA](../PROJECT_DNA.md))

| Principle | Verdict | Notes |
|---|---|---|
| 1 · #FreeForever | ✅ | No IAP, no paywall, no premium tier |
| 2 · Offline First | ✅ | No network in the core loop; TTS on-device; caption fallback |
| 3 · No Accounts | ✅ | No login; progress in `localStorage` |
| 4 · No Ads / No Tracking | ✅ | No analytics/ad SDKs; no third-party calls |
| 5 · Ages Not Grades | ✅ | Age bands 3–4…6–7; no grade strings |
| 6 · South Africa First | ⚠️ | English-only so far; isiZulu pending (consistent with all apps) |
| 7 · Voice First | ✅ | Narration is the primary interface |
| 12 · Private by Default | ✅ | Repo confirmed PRIVATE |
| 13 · Accessibility by Default | ✅ | Settings for speed/visual/motion/contrast; large targets |
| 14 · Modular Architecture | ✅ | Event-bus decoupling; app engines layered over platform engines |
| 17 · Wire AI, Don't Activate It | ✅ | **AI dropped 2026-07-02** — see below |

### Deviations — status

1. ✅ **RESOLVED — cloud AI removed.** `metadata.json` had declared
   `MAJOR_CAPABILITY_SERVER_SIDE_GEMINI_API` and `package.json` depended on `@google/genai` (both
   auto-added by Google AI Studio, **never used in `src/`**). Because this is a `#FreeForever` app
   — "we don't use AI in our apps as they are free" — the capability, the `@google/genai` dependency,
   and unused server cruft (`express`, `dotenv`) were removed on deploy (commit `2c2f211`). Now fully
   aligned with [Principle 17](../PROJECT_DNA.md). Verified build clean afterward.

2. ⚠️ **OPEN — "TPH Core" naming collision** with the canonical [TPH Core SDK](../platform/tph-core.md)
   (see §5, §12). **Recommendation:** rename the app's engine runtime (e.g. "TPH Learning
   Engines") or formally fold it into the canonical core; do not leave two frozen/unfrozen "TPH
   Core" definitions in the ecosystem. *(Founder decision pending.)*

3. ✅ **RESOLVED — repo moved to the org.** Transferred `SifisoScS/early-literacy` →
   `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy` (2026-07-02), consistent with the other 10 apps.

4. ✅ **RESOLVED — `package.json` name** fixed `"react-example"` → `"early-literacy"` (commit `2c2f211`).

None are security or child-safety violations.

---

## 12. Architecture audit (identify, do not rewrite)

| Dimension | Assessment |
|---|---|
| **Scalability** | ✅ Event-bus + singleton engines scale cleanly; adding a place = add a module + events |
| **Maintainability** | ✅ Small, single-responsibility engines; ⚠️ two "TPH Core" definitions risk drift |
| **Modularity** | ✅ App engines (Word, Reading Journey) sit cleanly above platform engines |
| **Platform alignment** | ⚠️ Consumes an app-local engine set named "TPH Core" that isn't the canonical SDK — reconcile |
| **Accessibility** | ✅ Settings + audio-first + large targets; visual-mode fallback exists |
| **Offline readiness** | ✅ Installable PWA (Workbox precache + navigateFallback); zero network calls after C1 fix |
| **Educational integrity** | ✅ Confidence-before-correction enforced; no fail states |
| **Navigation consistency** | ✅ Establishes the World-A nav standard (now documented) |
| **Security alignment** | ✅ No secrets; no tracking; `@google/genai` **and** remote Google audio removed — zero third-party surface |

### Full remaster audit (2026-07-02)

A senior-level, first-principles audit was run against the real code. **Phase 1 (critical) was
applied; Phases 2–5 are the tracked backlog.** No UI redesign was done.

**✅ Phase 1 — DONE (commit `b22bc6b`):**
- **C1 (critical):** `speech.ts` fetched narration from `actions.google.com` (a Google-AI-Studio
  remnant) — a network call in the learning path that broke offline-first, leaked to a third party,
  and defeated the PWA precache. **Removed** — all narration is now on-device TTS + local WebAudio.
- **C2 (high):** every sound effect created a **new `AudioContext`** (never closed) → hit the
  browser's ~6-context cap and killed audio mid-session. **Now one shared context**, resumed on gesture.
- **M5:** added an **ErrorBoundary** (gentle "village is resting" fallback vs. white screen).
- **M6:** **guarded `localStorage` writes** (Safari Private Mode / quota no longer crash saves).
- Also fixed a latent bug: `playCat` used a non-existent Web Audio method.

**⏳ Phases 2–5 — BACKLOG:**
| ID | Sev | Finding | Fix |
|---|---|---|---|
| M3 | Med | **Two conflicting tree-stage formulas** — `App.tsx` persists `treeStage` (4/12/25/45) while `EnvironmentEngine` computes (4/10/20/30). Split source of truth (SRP break). | One owner: App delegates to EnvironmentEngine. |
| M4 | Med | **Engine contracts ≠ code.** The app's `04-tph-core.md` claims Vocabulary has `attemptsCount` + "3 correct → mastered"; real code is a flat status map, mastered on first spell. Also **`@types/react` missing** → hollow type-checking. | Align docs to code (or implement); add `@types/react` + fix surfaced errors. |
| M8 | Med | **No code-splitting** — 548 KB (156 KB gzip) monolith; all 8 modules eager-loaded on a 3G target. | `React.lazy` per module + `manualChunks`. |
| M7 | Med | **Grown-Up Corner has no adult gate** — Reset Everything is reachable by a child (2-tap confirm only). | Add an adult gate on entry. |
| M9 | Low | Welcome `speak()` fires without a gesture (autoplay-blocked); no "tap to begin". | Add tap-to-begin gate. |
| M10 | Med | **Tracing/Discovery cover only 9 letters** (A–G,M,S); rest fall back to a triangle. | Author all 26. |
| M12 | Low | No child-facing per-session "Try this at home" transfer prompt (constitutional in Early Numeracy). | Add end-of-session transfer card. |
| — | Low | No `public/_headers` (CSP/clickjacking); typo "Suggeted". | Hygiene pass. |

**Verdict (2026-07-02):** production-readiness ~7.5/10 after Phase 1 (was ~6). Bones are right
(event-bus + app/platform engine layering). Remaining work is content depth (M10), type-safety
(M4), and consistency (M3) — not architecture.

---

## 13. Related

- [`early-numeracy.md`](./early-numeracy.md) — sibling Foundations on-ramp (number sense) ·
  [`read-africa.md`](./read-africa.md) — the literacy app it hands children up to ·
  [`math-adventure-rpg.md`](./math-adventure-rpg.md) — the numeracy elder sibling
- [`../platform/tph-core.md`](../platform/tph-core.md) — the canonical shared SDK (naming reconciliation)
- [`../architecture/04-early-literacy-integration.md`](../architecture/04-early-literacy-integration.md) — how it consumes core + the app-engine pattern
- [`../patterns/world-a-navigation.md`](../patterns/world-a-navigation.md) — the navigation standard it established
- [`../architecture/01-capability-architecture.md`](../architecture/01-capability-architecture.md) — Foundations slot #4
