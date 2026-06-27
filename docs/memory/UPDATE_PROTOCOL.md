# Memory Update Protocol

> This is a **living** knowledge base, not a snapshot. It is only worth trusting if it stays
> current. This document is the contract for keeping it alive.

---

## The core principle

> **The repository is the canonical long-term memory of The People's Home.**
> Every significant architectural decision, milestone, or completed feature should leave a
> trace here — in the same change, not "later."

If the only record of *why* something was done lives in a chat transcript or one person's head,
it is one lost machine / one ended conversation away from gone. That is the exact failure this
system exists to prevent.

---

## When to update (triggers)

Update the memory system whenever **any** of these happen:

| Trigger | What to update |
|---|---|
| An app ships, or a major feature lands | the app's `apps/*.md` (state + iteration note) · [`CURRENT_STATE.md`](./CURRENT_STATE.md) · [`TIMELINE.md`](./TIMELINE.md) |
| A structural / architectural decision is made | [`DECISIONS.md`](./DECISIONS.md) (append) · the relevant `canon/*.md` if it changes a principle |
| A rename, pivot, or retired idea | [`HISTORY.md`](./HISTORY.md) + the affected app/platform memory |
| A new app or platform piece is born | a new `apps/*.md` or `platform/*.md` + add it to the indexes |
| A live fact changes (URL, repo, build flag, status) | the **operational** docs ([`ECOSYSTEM.md`](../../ECOSYSTEM.md) / [`ROADMAP.md`](../../ROADMAP.md)), **not** here |
| An incident (keystore, rejection, outage) | [`HISTORY.md`](./HISTORY.md) |

---

## How to update (rules)

1. **Append, don't rewrite.** Decision-log and history entries are point-in-time records.
   Superseding a decision means *adding* a new entry that references the old one — never
   silently editing the past. (The current-state and canon docs *are* edited in place to stay
   true, but a superseded principle gets a "previously / changed because" note.)
2. **Date every entry.** Use absolute dates (`2026-06-27`), never "today" / "last week."
3. **Capture the *why*, not just the *what*.** Especially: the original vision, what was
   rejected, and why the chosen path won. That is the irreplaceable part.
4. **Mark genuine gaps `Unknown`.** Do not invent history to fill a hole. An honest `Unknown`
   is more valuable than a plausible fabrication.
5. **Cross-link.** New facts should link to the related memory (`[[…]]`-style relative links).
   A dangling link to a doc that doesn't exist yet is fine — it marks something worth writing.
6. **Operational facts go to the operational layer.** Don't duplicate the live ECOSYSTEM/ROADMAP
   tables here; link to them. This memory is the *narrative*, not the *registry*.

---

## The split, restated

- **Operational docs** (`../../ECOSYSTEM.md`, `../../ROADMAP.md`, `../../DECISIONS.md`, `../../BLUEPRINT.md`):
  the live registry and status board. Change often. Edited in place.
- **Memory system** (`docs/memory/`): the reasoning and evolution. Changes slowly. Append-mostly.

When the two disagree about a *current fact*, the operational layer wins — then reconcile the memory.

---

## Quality bar

Assume this repo is still maintained **ten years from now**. A new engineer or future AI should
be able to clone it, read [`README.md`](./README.md) → [`AI_READING_ORDER.md`](./AI_READING_ORDER.md),
and understand the whole project with no other context. Every update either preserves that
standard or it doesn't belong.
