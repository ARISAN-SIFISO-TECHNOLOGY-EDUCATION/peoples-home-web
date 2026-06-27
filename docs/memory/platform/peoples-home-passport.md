# People's Home Passport

> **Platform · cross-app shared state.**
> How a learner's progress travels *between* separate, offline, server-less apps.
> Conceptual context: [`../canon/05-tph-core-and-passport.md`](../canon/05-tph-core-and-passport.md).

---

## What it is
A **downloadable JSON file** a learner **exports** from one app and **imports** into another, carrying
their stamps / progress between apps. The learner literally holds their own record.

## Why it exists — the constraint that forced it
The apps are separate Cloudflare Pages projects on **separate origins**, all **offline**, with **no
server** (World-A rules). That combination rules out every conventional approach:

| Approach | Why it fails here |
|---|---|
| Central server store | Violates World-A no-server / no-data. |
| Shared `localStorage` | Impossible — separate origins can't read each other's storage. |
| Account/login sync | World B; breaks no-accounts. |
| **Downloadable, learner-held file** | ✅ The **only** thing that survives *separate origins + offline + no-server* at once. |

A learner-held file is also philosophically right: it matches **sovereign learning** — the learner
*owns* and *carries* their progress, on-device, no surveillance.

## Original vision
A way to make "ten apps" feel like "one Home, many journeys" — continuity of identity/progress across
apps — without breaking offline/no-server/no-data.

## Design iterations / how the thinking evolved
- **Reuse the TPH SDK's export-envelope idea, NOT its central store.** The Passport borrows the
  `@tph/core` *export envelope* concept but deliberately leaves behind any central/synced store.
- **First real implementation in Our World** (`content/passport.ts`) — the belonging-journey app
  whose first-person stamps were the natural first payload.
- **Second consumer: Math Adventure (2026-06-27, PRs #1/#2)** — adopted the Passport and the shared
  `@tph/core` envelope. Two real consumers is the threshold that makes a full `@tph/core` extraction
  worth doing (it was **deferred until it had real consumers** — now it does).
- **The pattern the next apps should adopt.** It's intended to generalise across the ecosystem.

## Architectural decisions (& rejected alternatives)
- **Export → import file transport.** *Rejected:* central store, shared storage, login sync (all
  above).
- **Envelope idea reused, central store dropped.** *Rejected:* taking the whole TPH SDK including its
  store (would drag in World-B assumptions).
- **Extraction deferred until ≥2 consumers.** *Rejected:* premature extraction with one consumer.

## Current state
Live pattern. Consumers: **Our World** (origin) + **Math Adventure** (on `@tph/core`). Full
`@tph/core` extraction is now justified and pending (see [`tph-core.md`](./tph-core.md)).

## Future direction
Adopt across more apps so a learner's stamps follow them through the Home; pair with extracted TPH
Core so progress both *exists* (Core) and *travels* (Passport). Long-term, the Passport is also the
clean, privacy-respecting seam toward any future iKhaya handoff *the learner chooses to make*.

## Related
- [`tph-core.md`](./tph-core.md) (where progress lives) ·
  [`../apps/our-world.md`](../apps/our-world.md) (origin) ·
  [`../apps/math-adventure-rpg.md`](../apps/math-adventure-rpg.md) (second consumer) ·
  [`../canon/05-tph-core-and-passport.md`](../canon/05-tph-core-and-passport.md).
