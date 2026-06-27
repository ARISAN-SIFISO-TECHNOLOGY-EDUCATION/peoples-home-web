# Canon 05 — TPH Core & the Passport

> The shared-platform thesis: the connective tissue that makes ten separate apps feel like **one
> Home**. Two related ideas — **TPH Core** (shared services) and the **Passport** (shared state
> across separate origins). Deep memories: [`../platform/tph-core.md`](../platform/tph-core.md) ·
> [`../platform/peoples-home-passport.md`](../platform/peoples-home-passport.md).

---

## The problem

Ten offline apps, each its own Cloudflare Pages project on its own origin, each with its own
`localStorage`. By the rules ([`03-product-rules.md`](./03-product-rules.md)) there is **no server**
and **no shared login**. So:
- How does a learner have **one identity** across apps?
- How do **progress, rewards, and lore** carry between them?
- How do you avoid rebuilding the same shell ten times?

TPH Core and the Passport are the two answers.

---

## TPH Core — shared *services* (not an app)

The shared rails behind every product:

> **Identity · Progress · Rewards · Lore · Offline Engine · Parent / Mentor / Community Dashboards.**

- **Current state:** seeded as the **TPH Core SDK embedded in ReadAfrica**. The informal version is
  the **shared "Atelier" chassis** that apps copy ([`04-delivery-model.md`](./04-delivery-model.md)).
- **The platform track (now the lead item):** *extract* TPH Core from ReadAfrica into a shared
  package and *adopt* it across apps, so the shared services are maintained once, not copied N times.
- **Why a service, not an app:** identity/progress/rewards aren't something a learner "uses" — they
  are infrastructure every app needs. Implementing them as a shared service (not duplicated code) is
  the [capability architecture](./01-capability-architecture.md) applied to the platform itself.

---

## The Passport — shared *state* across separate origins

The hardest constraint: separate origins **cannot read each other's `localStorage`**, and there's
**no server** to sync through, and it all must work **offline**.

> **The Passport is a downloadable JSON file the learner exports from one app and imports into
> another, carrying their stamps/progress between apps.**

- **Why a file, and not the obvious alternatives:**
  - *Central server store* → violates World-A no-server/no-data.
  - *Shared `localStorage`* → impossible across separate origins.
  - *A downloadable, learner-held file* → the **only** mechanism that survives *separate origins +
    offline + no-server* all at once. It also fits the sovereignty ethos: the learner literally
    **holds their own record**.
- **Lineage:** reuses the **TPH SDK's export-envelope idea** (the `@tph/core` envelope), **not** its
  central store. First real implementation in **Our World** (`content/passport.ts`); adopted in
  **Math Adventure** (this repo, PRs #1/#2) on the shared `@tph/core` envelope.
- **Status:** the pattern the next apps should adopt. Full `@tph/core` extraction is **deferred
  until it has multiple real consumers** (Math Adventure + Our World are the first two).

---

## How the two relate

- **TPH Core** = the services *inside* each app (identity, progress, rewards, lore, dashboards).
- **Passport** = the *transport* that moves a learner's TPH state *between* apps without a server.

Together they're how "ten apps" becomes "one Home, many journeys" in practice — without ever
breaking the offline / no-server / no-data rules.

---

## Related
- [`../platform/tph-core.md`](../platform/tph-core.md) — TPH Core deep memory.
- [`../platform/peoples-home-passport.md`](../platform/peoples-home-passport.md) — Passport deep memory.
- [`04-delivery-model.md`](./04-delivery-model.md) — the shared chassis this grows out of.
