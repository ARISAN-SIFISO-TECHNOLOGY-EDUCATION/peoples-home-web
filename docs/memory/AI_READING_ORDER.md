# AI Reading Order

> For a future AI (or new engineer) with **zero prior context**. Read in this order and you
> will understand the vision, philosophy, architecture, roadmap, every major decision, every
> application, every shared platform, and the current state — without any previous conversation.
>
> Estimated read: ~30–40 minutes for the whole system. The first five items (~10 minutes) are
> enough to act safely.

---

## Phase 1 — Understand the *why* (read first, in order)

1. **[`canon/00-vision-and-philosophy.md`](./canon/00-vision-and-philosophy.md)**
   The mission and the worldview. Start here or nothing else makes sense.
2. **[`canon/01-capability-architecture.md`](./canon/01-capability-architecture.md)**
   How ~40 imagined apps were collapsed into a capability *system*. The 6 pillars.
3. **[`canon/02-world-a-world-b-dna.md`](./canon/02-world-a-world-b-dna.md)**
   The single most important architectural idea: the World A / World B DNA split, and "the bridge."
4. **[`canon/03-product-rules.md`](./canon/03-product-rules.md)**
   The non-negotiables. Break one of these and you have broken the project.

## Phase 2 — Understand the *how*

5. **[`canon/04-delivery-model.md`](./canon/04-delivery-model.md)**
   Web-first PWAs, the Google Play wind-down, the house deploy pattern.
6. **[`canon/05-tph-core-and-passport.md`](./canon/05-tph-core-and-passport.md)**
   The shared platform thesis and how state moves between separate, offline apps.
7. **[`../../ECOSYSTEM.md`](../../ECOSYSTEM.md)** *(operational layer)*
   The live table: every repo, URL, stack, and build config. The map of the territory.

## Phase 3 — Understand the *what / where we are*

8. **[`CURRENT_STATE.md`](./CURRENT_STATE.md)**
   Where every app and track stands today. Read this before doing any work.
9. **[`../../ROADMAP.md`](../../ROADMAP.md)** *(operational layer)*
   The status board and near-term sequence.
10. **[`TIMELINE.md`](./TIMELINE.md)** — how we got here, chronologically.

## Phase 4 — Deep dives (as needed for your task)

11. **[`apps/`](./apps/)** — the memory for whichever app(s) you are touching.
12. **[`platform/`](./platform/)** — TPH Core, Passport, iKhaya.
13. **[`DECISIONS.md`](./DECISIONS.md)** + **[`HISTORY.md`](./HISTORY.md)** — the reasoning archive and the incident log.

---

## Before you change anything

- Re-read **[`canon/03-product-rules.md`](./canon/03-product-rules.md)**. The rules are
  load-bearing and easy to violate accidentally (a stray "Grade 4" string fails the build's intent).
- If you ship or decide something significant, you **must** update this memory system —
  see **[`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md)**. The memory only stays trustworthy if
  every meaningful change leaves a trace here.
- When a memory doc and an operational doc disagree about a *current fact*, the operational
  doc ([`ECOSYSTEM.md`](../../ECOSYSTEM.md) / [`ROADMAP.md`](../../ROADMAP.md)) wins — then fix the memory doc.
