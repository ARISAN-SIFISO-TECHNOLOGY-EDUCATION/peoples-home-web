# Early Literacy

> 🧮 **Foundations** · ages **3–7** · **BUILT — integrating** (World A — offline PWA) ·
> repo `SifisoScS/early-literacy` (private) · **not yet deployed** ·
> Product name: **Early Literacy Village** ("Magical Literacy Village") ·
> Integrated into the Brain 2026-07-02.
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
100% offline for the core loop: no network calls, all assets bundled, all state local. Speech
uses on-device TTS; if synthesis fails it falls back to timed visual captions (never silence
where a voice is expected). Satisfies [Principle 2 (Offline First)](../PROJECT_DNA.md).

### Accessibility model
`AccessibilitySettings` exposes `narrationSpeed`, `visualMode`, `reducedMotion`, `highContrast`.
Age selector uses large emoji buttons; no reading required to start; high-contrast restyles the
whole document. Aligns with [Principle 13 (Accessibility by Default)](../PROJECT_DNA.md) and the
[voice-first](../patterns/voice-first.md) pattern — Early Literacy is a strong future entry there.

---

## 8. Current state

**Built externally (Google AI Studio / Gemini), integrated into the Brain 2026-07-02, NOT yet
deployed.** Repo `SifisoScS/early-literacy` (PRIVATE), local checkout
`C:\Users\sifis\Next-Level-Projects\early-literacy`. Phases 1–4 + navigation framework complete.
For live facts (repo, URL, build) see [`../../ECOSYSTEM.md`](../../ECOSYSTEM.md); for status see
[`../../ROADMAP.md`](../../ROADMAP.md).

---

## 9. Future direction / roadmap

- **Phase 4.5** — the next authored step (planned; scope TBD by founder).
- **Deploy** — Cloudflare Pages PWA (unique manifest `id`), verify offline, add to the site.
- **Repo home** — migrate `SifisoScS/early-literacy` → the `ARISAN-SIFISO-TECHNOLOGY-EDUCATION`
  org for consistency with the other 10 apps (deviation, §12).
- **isiZulu** — English-first today; isiZulu narration is part of the ~December 2026 batch.
- **TPH Core reconciliation** — resolve the naming collision (§12); the app's behaviour engines
  are candidate contributions to (or a renamed sibling of) the canonical TPH Core SDK.

---

## 10. Known constraints

- Not deployed; no public URL yet.
- English-only content (isiZulu deferred to the December review, consistent with all apps).
- `package.json` `name` is the placeholder `"react-example"` (cosmetic; fix before publish).
- 10 first words authored (CAT, DOG, SUN, FROG, BIRD, RAIN, TRAIN, BEE, TREE, BELL) — a seed set.

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
| 17 · Wire AI, Don't Activate It | ⚠️ | See below |

### ⚠️ Deviations (documented, not silently changed — per the integration mandate)

1. **Declared cloud AI capability, unused.** `metadata.json` declares
   `MAJOR_CAPABILITY_SERVER_SIDE_GEMINI_API` and `package.json` depends on `@google/genai`, but
   **there are zero AI/Gemini calls in `src/`**. In practice this *honours*
   [Principle 17 (Wire AI, Don't Activate It)](../PROJECT_DNA.md) — wired, not activated. But a
   *declared* server-side cloud capability sits in tension with strict offline autonomy and should
   be removed (or the dependency dropped) before publish, since nothing uses it. Aligns with the
   AI principle established 2026-06-28. **Recommendation:** drop the unused capability + dependency.

2. **"TPH Core" naming collision** with the canonical [TPH Core SDK](../platform/tph-core.md)
   (see §5, §12). **Recommendation:** rename the app's engine runtime (e.g. "TPH Learning
   Engines") or formally fold it into the canonical core; do not leave two frozen/unfrozen "TPH
   Core" definitions in the ecosystem.

3. **Repo under personal account** `SifisoScS`, not the org. Consistency gap; migrate on publish.

4. **`package.json` name placeholder** `"react-example"`. Cosmetic; fix before publish.

None of these are security or child-safety violations. All are logged here rather than changed,
per the integration brief.

---

## 12. Architecture audit (identify, do not rewrite)

| Dimension | Assessment |
|---|---|
| **Scalability** | ✅ Event-bus + singleton engines scale cleanly; adding a place = add a module + events |
| **Maintainability** | ✅ Small, single-responsibility engines; ⚠️ two "TPH Core" definitions risk drift |
| **Modularity** | ✅ App engines (Word, Reading Journey) sit cleanly above platform engines |
| **Platform alignment** | ⚠️ Consumes an app-local engine set named "TPH Core" that isn't the canonical SDK — reconcile |
| **Accessibility** | ✅ Settings + audio-first + large targets; visual-mode fallback exists |
| **Offline readiness** | ✅ Core loop offline; ⚠️ verify PWA service worker + manifest `id` before deploy |
| **Educational integrity** | ✅ Confidence-before-correction enforced; no fail states |
| **Navigation consistency** | ✅ Establishes the World-A nav standard (now documented) |
| **Security alignment** | ✅ No secrets in source; no tracking; ⚠️ drop unused `@google/genai` to shrink supply-chain surface |

**No code changes were made. Findings are recorded for founder decision.**

---

## 13. Related

- [`early-numeracy.md`](./early-numeracy.md) — sibling Foundations on-ramp (number sense) ·
  [`read-africa.md`](./read-africa.md) — the literacy app it hands children up to ·
  [`math-adventure-rpg.md`](./math-adventure-rpg.md) — the numeracy elder sibling
- [`../platform/tph-core.md`](../platform/tph-core.md) — the canonical shared SDK (naming reconciliation)
- [`../architecture/04-early-literacy-integration.md`](../architecture/04-early-literacy-integration.md) — how it consumes core + the app-engine pattern
- [`../patterns/world-a-navigation.md`](../patterns/world-a-navigation.md) — the navigation standard it established
- [`../architecture/01-capability-architecture.md`](../architecture/01-capability-architecture.md) — Foundations slot #4
