# TPH Core

> **Platform · shared services (not an app).**
> The connective tissue that makes ten separate offline apps feel like **one Home**.
> Conceptual context: [`../canon/05-tph-core-and-passport.md`](../canon/05-tph-core-and-passport.md).

---

## What it is
The shared services every product needs:

> **Identity · Progress · Rewards · Lore · Offline Engine · Parent / Mentor / Community Dashboards.**

## Why it exists
Each learning app is its own Cloudflare Pages project with its own `localStorage` and **no server,
no shared login** (the World-A rules). Without shared services, every app would reinvent identity,
progress tracking, rewards, and the offline shell — ten times. TPH Core is the *"build it once"*
answer, and the thing that lets the apps share a coherent identity and progress model.

## Original vision
A shared core of services underpinning the whole ecosystem — the platform layer beneath the apps.

## Design iterations / how the thinking evolved
- **Grown inside a real app, not designed in the abstract.** TPH Core was first built and **embedded
  in ReadAfrica** as the "TPH Core SDK," rather than as a speculative standalone package. This is
  deliberate: build the shared thing where it has a real consumer, then extract.
- **The informal precursor: the shared "Atelier" chassis.** Before formal extraction, apps shared a
  *copied* chassis (Truth Seekers → Micro Founders → Mzansi Money → Everyday Foundations → Our
  World). Copying worked for shipping fast but doesn't scale — the same fix has to be made N times.
  That pain is exactly what motivates extraction.
- **Extraction is now the lead platform item (2026-06-27).** With every World-A pillar shipped, the
  frontier moved from *apps* to *platform*: pull TPH Core out of ReadAfrica into a shared package and
  adopt it across apps.

## Architectural decisions (& rejected alternatives)
- **Service, not app.** Identity/progress/rewards are infrastructure, not something a learner "uses."
  *Rejected:* a "profile app." (Module-over-new-app / capability architecture applied to the platform.)
- **Embed-then-extract.** *Rejected:* building a platform package up front with no consumer
  (speculative, likely wrong).
- **Export-envelope over central store** for cross-app state — see the
  [Passport](./peoples-home-passport.md). TPH Core provides the *services*; the Passport provides the
  *transport between* apps without a server.

## Current state
Embedded in ReadAfrica. Extraction to a shared package + cross-app adoption is the active platform
track (the lead item). Math Adventure already consumes the **`@tph/core` envelope** for its Passport
(PRs #1/#2) — an early real adoption.

## Future direction
Extract → publish a shared package → adopt across apps, starting with the apps that most need shared
identity/progress (Everyday Foundations' Household Mode, the teen apps' continuity). Pair with the
Passport so progress both *exists* (TPH Core) and *travels* (Passport).

## Related
- [`peoples-home-passport.md`](./peoples-home-passport.md) (the transport layer) ·
  [`../apps/read-africa.md`](../apps/read-africa.md) (its cradle) ·
  [`../canon/05-tph-core-and-passport.md`](../canon/05-tph-core-and-passport.md).
