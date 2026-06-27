# The People's Home — Memory System

> **This is the institutional memory of The People's Home.**
> Code lives in git across many repositories. *This* is the layer that usually
> doesn't survive: the vision, the philosophy, the architecture, the reasoning behind
> every major decision, and the evolution of the ideas themselves.
>
> Built so that a new engineer — or a future AI with **no prior context** — can clone
> this repository, read this folder, and understand the whole project without access to
> any previous conversation.
>
> **Authored:** 2026-06-27 · **Maintained as a living system** (see [`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md)).

---

## What this is (and is not)

This memory system has **two layers**, deliberately separated:

1. **The operational layer** — the existing root docs of this repo
   ([`../../BLUEPRINT.md`](../../BLUEPRINT.md), [`../../ECOSYSTEM.md`](../../ECOSYSTEM.md),
   [`../../ROADMAP.md`](../../ROADMAP.md), [`../../DECISIONS.md`](../../DECISIONS.md),
   [`../../MICRO_FOUNDERS.md`](../../MICRO_FOUNDERS.md), [`../../DEPLOY.md`](../../DEPLOY.md)).
   These are the **live source of truth** for current status, repos, URLs, build configs.
   They are tables and facts that change often. **This memory system does not duplicate them — it links to them.**

2. **The memory layer** — *this* `docs/memory/` folder. The **narrative and reasoning**:
   why each thing exists, the original vision, how the thinking evolved, what was rejected
   and why, and where each thing is going. This changes slowly and is **append-mostly**.

> **Rule of thumb:** if it's a *fact that changes weekly* (a URL, a build flag, a status),
> it belongs in the root operational docs. If it's *why we did it / how we got here*, it
> belongs here.

---

## How to read this (start here)

If you are new — human or AI — read in this order. The full annotated path is in
[`AI_READING_ORDER.md`](./AI_READING_ORDER.md).

1. [`canon/00-vision-and-philosophy.md`](./canon/00-vision-and-philosophy.md) — *what we are building and why it matters*
2. [`canon/01-capability-architecture.md`](./canon/01-capability-architecture.md) — *the shape of the system*
3. [`canon/02-world-a-world-b-dna.md`](./canon/02-world-a-world-b-dna.md) — *the single most important architectural idea*
4. [`canon/03-product-rules.md`](./canon/03-product-rules.md) — *the non-negotiables*
5. [`CURRENT_STATE.md`](./CURRENT_STATE.md) — *where everything stands right now*
6. Then dive into [`apps/`](./apps/) and [`platform/`](./platform/) as needed.

---

## Index

### Top level
| Doc | Purpose |
|---|---|
| [`AI_READING_ORDER.md`](./AI_READING_ORDER.md) | The canonical onboarding path for a fresh reader. |
| [`CURRENT_STATE.md`](./CURRENT_STATE.md) | Snapshot of where every app, platform piece, and track stands today. |
| [`TIMELINE.md`](./TIMELINE.md) | The chronological evolution of the whole project. |
| [`HISTORY.md`](./HISTORY.md) | Archive of incidents, pivots, renames, and retired ideas. |
| [`DECISIONS.md`](./DECISIONS.md) | Evolution-aware decision log (the *why* behind structural calls). |
| [`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md) | How to keep this memory system alive and trustworthy. |

### Canon (numbered, slow-changing)
| Doc | Purpose |
|---|---|
| [`canon/00-vision-and-philosophy.md`](./canon/00-vision-and-philosophy.md) | The mission, the philosophy, the long-term outcome. |
| [`canon/01-capability-architecture.md`](./canon/01-capability-architecture.md) | Capability → Implementation → DNA; the 6 pillars. |
| [`canon/02-world-a-world-b-dna.md`](./canon/02-world-a-world-b-dna.md) | The DNA split and "the bridge." |
| [`canon/03-product-rules.md`](./canon/03-product-rules.md) | Ages-not-grades, #FreeForever, offline/no-data, SA-first. |
| [`canon/04-delivery-model.md`](./canon/04-delivery-model.md) | The web-first pivot, PWA conventions, deploy patterns. |
| [`canon/05-tph-core-and-passport.md`](./canon/05-tph-core-and-passport.md) | The shared-platform thesis and the Passport mechanism. |

### Applications (World A — offline learning)
See [`apps/README.md`](./apps/README.md) for the index. One memory per app:
Math Adventure · ReadAfrica · Science Sprouts · Tech Makers · The Golden Hand ·
Truth Seekers · Micro Founders · Mzansi Money · Everyday Foundations · Our World.

### Platform & World B
See [`platform/README.md`](./platform/README.md):
TPH Core · People's Home Passport · iKhaya · iKhaya Learn.

---

## The shape in one breath

> **The People's Home** is a Sovereign Learning System by **iKhaya AI** (an
> **ARISAN SIFISO Holdings** initiative, supported by **The People's Home Foundation NPC**).
> A complete pathway to **learn, think, build, earn, and create opportunity** — for every
> South African, regardless of age, income, location, or schooling.
>
> Ten or so deep, **offline, free-forever** learning apps (World A), one server-backed
> **opportunity platform** (iKhaya / World B), and a shared core that carries identity,
> progress, and rewards between them.
>
> **One Home. Many Journeys. One Future.**
