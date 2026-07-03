# Architecture 04 — Early Literacy: consuming the platform (and the app-engine pattern)

> How **[Early Literacy](../apps/early-literacy.md)** consumes shared educational engines
> **without modifying them**, how it layers its own application engines on top, and the one
> naming deviation this integration surfaced (**resolved 2026-07-03** — see §4). Companion to
> [`03-tph-core-and-passport.md`](./03-tph-core-and-passport.md).
>
> **Added:** 2026-07-02 (integration, no app code changed).

---

## 1. The layering (the thing to copy)

Early Literacy is the ecosystem's clearest example of the correct World-A layering:

```
  ┌─────────────────────────────────────────────────────────────┐
  │  UI COMPONENTS  (VillageMap + 8 module screens)              │  React 19 / Tailwind
  ├─────────────────────────────────────────────────────────────┤
  │  APPLICATION ENGINES  (this app only)                        │
  │    • WordEngine          — first-words content + spelling    │
  │    • ReadingJourneyEngine — milestones + recommendations     │
  ├─────────────────────────────────────────────────────────────┤
  │  PLATFORM ENGINES  (shared behaviour — NOT modified)         │
  │    Companion · Tracing · Vocabulary · Discovery · Environment│
  ├─────────────────────────────────────────────────────────────┤
  │  EVENT BUS  (type-safe pub/sub — the only inter-engine path) │
  └─────────────────────────────────────────────────────────────┘
```

**The rule demonstrated:** components and app engines never reach *into* platform engines;
coordination happens by **publishing namespaced events** on the bus. Direct engine-to-engine
calls are forbidden (prevents circular dependencies and keeps engines swappable). This is
[Principle 14 (Modular Architecture)](../PROJECT_DNA.md) made concrete.

### Events in use
`learning.word.mastered` · `learning.trace.completed` · `environment.tree.grown` ·
`environment.reward.earned` · `companion.help.requested` · `progress.saved`.
Example flow: Word Builder → `WordEngine.registerWordProgress()` → publishes
`learning.word.mastered` + `environment.reward.earned` → Discovery & Environment engines react →
UI re-renders. No component touches another engine directly.

---

## 2. Consuming the platform without modifying it

Early Literacy treats its engine set as a **production SDK**: it imports the public, typed
contracts and calls them; it does not edit engine internals. This is exactly the discipline
[Principle 11 (Platform Before Duplication)](../PROJECT_DNA.md) asks for — build the app *on*
shared services, don't re-implement them.

**The generalisable lesson for every future World-A app:** if a behaviour (mastery tracking,
tracing validation, reward/ecosystem maturation, companion dialogue) already exists as an engine,
consume it via its contract and the event bus. Author only your *content* logic as app engines.

---

## 3. The application-engine pattern

| App engine | Belongs to | Why it is NOT platform |
|---|---|---|
| **WordEngine** | Early Literacy | Holds *this app's* first-words content, phonics, spelling rules |
| **ReadingJourneyEngine** | Early Literacy | Encodes *this app's* curriculum milestones + recommendations |

Both are singletons that *use* platform engines (e.g. WordEngine records mastery via the
Vocabulary Engine and publishes on the bus) but are themselves app-specific. They are correctly
excluded from the core version manifest. When a pattern here recurs in a second app, that is the
signal to promote it to the platform ([Principle 11](../PROJECT_DNA.md)).

---

## 4. ✅ Resolved deviation — the "TPH Core" naming collision

This integration surfaced a genuine conflict — two different engine sets sharing the name
"TPH Core" — that was **documented, not silently reconciled**, and then put to the founder.

| | Canonical **TPH Core SDK** | Early Literacy's app runtime |
|---|---|---|
| Now called | **TPH Core** / `@tph/core` | **TPH Learning Engines** *(renamed 2026-07-03)* |
| Defined in | [`../platform/tph-core.md`](../platform/tph-core.md) | `early-literacy/brain/architecture/04-tph-core.md` |
| Nature | Shared **product services** | Educational **behaviour engines** |
| Contents | Identity · Progress · Rewards · Lore · Offline Engine · Dashboards | EventBus · Companion · Tracing · Vocabulary · Discovery · Environment |
| Status | **Mid-extraction** from ReadAfrica → `@tph/core` (not frozen) | Declared **frozen, v1.0.0, released 2026-07** |
| Origin | Grown inside ReadAfrica | Built independently inside Early Literacy (Gemini) |

**Decision (2026-07-03 — founder chose Option 1):** the app-local runtime is **renamed to the
"TPH Learning Engines."** The name "TPH Core" is now reserved exclusively for the canonical shared
SDK. Option 2 (fold the app engines into `@tph/core`) was deferred — `@tph/core` is still
mid-extraction, and folding a frozen app runtime into it is a larger, multi-app effort for later.

**Applied in the app repo (commit `49edf66`):** TypeScript symbols `TPHCore*` → `TPHLearning*`
(EventBus, EventMap, EventName, Callback), the Word Builder UI badge "TPH CORE V1.0" → "TPH LEARNING
ENGINES", and the app-local architecture doc rebranded (its `04-tph-core.md` filename kept for link
stability). Pure rename — no logic changed; `tsc` clean, build clean. **No collision remains.**

---

## 5. Related

- [`03-tph-core-and-passport.md`](./03-tph-core-and-passport.md) — the shared platform in depth
- [`../platform/tph-core.md`](../platform/tph-core.md) — canonical TPH Core SDK
- [`../apps/early-literacy.md`](../apps/early-literacy.md) — the app memory
- [`../patterns/world-a-navigation.md`](../patterns/world-a-navigation.md) — the navigation standard it established
