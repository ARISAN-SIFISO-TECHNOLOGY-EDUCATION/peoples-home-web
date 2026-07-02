# Pattern: World-A Navigation

> The official navigation specification for World-A learning apps, established by
> **[Early Literacy](../apps/early-literacy.md)** (2026-07). A single, predictable way to
> move *into* an activity, *back out* of it, and *resume* it — designed for a 3-year-old's
> thumb and a low-end phone.

---

## What it is

A small, consistent navigation contract every World-A app should follow so that a child (or a
caregiver) never gets lost and never loses progress. It has five parts: **hierarchical back**,
**edge/swipe back**, **resume**, **state preservation**, and **companion + accessibility
behaviour**. It is a UX + interaction pattern, not a shared code package (yet).

---

## Why we use it

- **Non-readers can't read a breadcrumb.** Navigation must be spatial, gestural, and audible.
- **Small thumbs, cheap phones.** Back must work by a big button *and* a natural swipe.
- **Sessions get interrupted.** A child leaves and returns; the app must resume exactly where
  it was, with zero "are you sure?" friction.
- **One Home.** If every app moves differently, the ecosystem feels like ten strangers.
  ([Principle 8 · One Home](../PROJECT_DNA.md).)

---

## How it is implemented

Reference implementation: `early-literacy/src/App.tsx` + each module component.

1. **Hierarchical back.** One level at a time — module → village map → (never a dead end).
   Every module renders a visible back control (`ArrowLeft`) and receives an `onClose` handler.
   Modals close back to the surface beneath them, not to the root.

2. **Edge / swipe back (mobile).** On viewports `< 768px`, a left→right swipe over the content
   triggers back. Reference thresholds: horizontal travel `> 100px` with vertical drift `< 60px`
   (tune toward a **~32px edge-initiated** swipe zone as the standard so mid-screen drags inside
   an activity aren't hijacked — *drag protection*). The gesture dispatches a `tph-back-gesture`
   DOM event the active module listens for.

3. **Resume.** On return (app re-open or `visibilitychange`), the app rehydrates from
   `localStorage` and lands the child on the same place/level — no relaunch to a home splash.

4. **State preservation.** All progress is written to `localStorage` on every update, so back /
   leave / return never loses a star, a letter, or a word. Back is always safe; there is no
   "discard?" prompt.

5. **Companion + accessibility behaviour.**
   - **Companion farewell.** Back plays a soft `bubble-pop` cue (and, where authored, a spoken
     companion "goodbye") so the exit is felt, not abrupt.
   - **Accessible controls.** Back / help / settings targets are large (target **64×64px**;
     never below the [Principle 13](../PROJECT_DNA.md) 44×44 floor) with no text label required.

---

## Where it is used

| App | Status | Notes |
|---|---|---|
| **Early Literacy** | ✅ Established here | Hierarchical back + swipe + resume + bubble-pop farewell |

**Marked reusable by** (adopt this spec when they next iterate):
- **Early Numeracy** — same 3–7 audience; natural first adopter
- **Science Sprouts** — module → map navigation
- **Our World** — journey/place navigation
- **ReadAfrica** — the literacy elder sibling

---

## Rules and constraints

1. **Back is never destructive.** It must never lose progress and must never show a
   confirmation prompt in the child-facing flow. State is saved *before* navigation, always.
2. **Never trap the child.** Every screen has a way back to the map; the map is the safe home.
3. **Gesture must not fight play.** Swipe-back must not fire during in-activity drags — prefer an
   edge-initiated zone and a vertical-drift guard (*drag protection*).
4. **Targets stay large.** Navigation controls target 64×64px; never below 44×44px.
5. **Exit is gentle.** Provide an audible/animated farewell cue on back — never a silent jump.
6. **Desktop parity.** Where swipe doesn't apply (≥768px / mouse), the visible back control is
   the primary path; behaviour is otherwise identical.

---

## Evolution

**2026-07 — Early Literacy** established the standard: hierarchical back, mobile swipe-to-back
(`tph-back-gesture`), `localStorage` resume, and a `bubble-pop` companion farewell, with
large no-text controls. Promoted here as the World-A navigation spec so Early Numeracy, Science
Sprouts, Our World, and ReadAfrica can adopt one consistent model.
