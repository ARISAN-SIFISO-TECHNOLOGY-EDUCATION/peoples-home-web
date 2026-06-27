# The People's Home — Brain

> **This is the institutional memory of The People's Home.**
>
> Code lives in git across many repositories. *This* is the layer that usually doesn't
> survive: the vision, the philosophy, the architecture, the reasoning behind every
> major decision, and the evolution of the ideas themselves.
>
> Built so that a new engineer, a new collaborator, or a future AI with **zero prior
> context** can open this folder and understand the whole project — the *what*, the *why*,
> the *how*, and the *where we are* — without access to any previous conversation.
>
> **Authored:** 2026-06-27 · **Constitution version:** 1.0
> Maintained as a living system — see [`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md).

---

## What this is

The Brain is the **permanent AI-readable and human-readable institutional memory** of
The People's Home. It answers:

- *What is this?* — the mission, the philosophy, the pillars, the product rules
- *Why does it exist?* — the founding insight and the long-term vision
- *How is it built?* — the World A / World B architecture, the delivery model, the TPH Core
- *What is running now?* — 10 live learning apps, the current platform state
- *How did we get here?* — the full timeline, the decisions, the pivots
- *How does this AI work?* — onboarding, tool use, session continuity, glossary

---

## Two layers — operational and memory

The repository has two distinct layers:

### 1. Operational layer (root docs — change often)
These are the **live source of truth** for current status, URLs, and build configs.
Update them in place when facts change.

| Doc | What it tracks |
|---|---|
| [`ECOSYSTEM.md`](../ECOSYSTEM.md) | Every repo, URL, stack, build config |
| [`ROADMAP.md`](../ROADMAP.md) | Near-term priorities and status board |
| [`BLUEPRINT.md`](../BLUEPRINT.md) | Capability map, six pillars, app family overview |
| [`DECISIONS.md`](../decisions/DECISIONS.md) | Major cross-cutting decisions (stub; deep log in brain/decisions/) |
| [`MICRO_FOUNDERS.md`](../MICRO_FOUNDERS.md) | Micro Founders detailed spec |

### 2. Memory layer (this `brain/` folder — append-mostly)
The **narrative, philosophy, and reasoning** — why each thing exists, how the thinking
evolved, what was rejected and why. Changes slowly.

> **Rule of thumb:** if it's a *fact that changes weekly* (URL, build flag, status),
> it belongs in the root operational docs. If it's *why we did it / how we got here*,
> it belongs here.

---

## How to navigate this (start here)

If you have never read this project before → `brain/AI_ONBOARDING.md`
If you are continuing from a previous session → `brain/SESSION_HANDOFF.md`

### Quick reading path (10 minutes — enough to act safely)

1. [`vision/00-vision-and-philosophy.md`](./vision/00-vision-and-philosophy.md) — the mission and worldview
2. [`architecture/01-capability-architecture.md`](./architecture/01-capability-architecture.md) — the shape of the system
3. [`architecture/02-world-a-world-b-dna.md`](./architecture/02-world-a-world-b-dna.md) — the single most important idea
4. [`vision/01-product-rules.md`](./vision/01-product-rules.md) — the non-negotiables
5. [`CURRENT_STATE.md`](./CURRENT_STATE.md) — where everything stands today

---

## Full index

### Core navigation

| File | Purpose |
|---|---|
| [`AI_ONBOARDING.md`](./AI_ONBOARDING.md) | How any AI should read, work in, and update this project |
| [`SESSION_HANDOFF.md`](./SESSION_HANDOFF.md) | Session continuity log — the last thing an AI wrote before context ended |
| [`CURRENT_STATE.md`](./CURRENT_STATE.md) | Snapshot of every app, track, and platform piece right now |
| [`PROJECT_TIMELINE.md`](./PROJECT_TIMELINE.md) | Chronological evolution of the whole project |
| [`PROJECT_GLOSSARY.md`](./PROJECT_GLOSSARY.md) | Key terms, names, and concepts explained |
| [`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md) | Rules for keeping this memory system trustworthy |

### Vision (slow-changing — the why and the rules)

| File | Purpose |
|---|---|
| [`vision/00-vision-and-philosophy.md`](./vision/00-vision-and-philosophy.md) | The mission, the worldview, the long-term outcome |
| [`vision/01-product-rules.md`](./vision/01-product-rules.md) | Non-negotiable constraints: #FreeForever, offline-first, ages-not-grades, SA-first |
| [`vision/02-delivery-model.md`](./vision/02-delivery-model.md) | Web-first PWA pivot, Google Play wind-down, deploy patterns |

### Architecture (load-bearing — the how)

| File | Purpose |
|---|---|
| [`architecture/01-capability-architecture.md`](./architecture/01-capability-architecture.md) | Capability → Implementation → DNA; the six pillars |
| [`architecture/02-world-a-world-b-dna.md`](./architecture/02-world-a-world-b-dna.md) | The World A / World B DNA split and "the bridge" |
| [`architecture/03-tph-core-and-passport.md`](./architecture/03-tph-core-and-passport.md) | The shared-platform thesis and the Passport mechanism |

### Applications (World A — all 10 live)

See [`apps/README.md`](./apps/README.md). One memory file per app:

| App | Pillar | File |
|---|---|---|
| Math Adventure RPG | Foundations | [`apps/math-adventure-rpg.md`](./apps/math-adventure-rpg.md) |
| ReadAfrica | Foundations | [`apps/read-africa.md`](./apps/read-africa.md) |
| Everyday Foundations | Foundations | [`apps/everyday-foundations.md`](./apps/everyday-foundations.md) |
| Science Sprouts | Curiosity & Knowledge | [`apps/science-sprouts.md`](./apps/science-sprouts.md) |
| Our World | Curiosity & Knowledge | [`apps/our-world.md`](./apps/our-world.md) |
| Tech Makers | Creation & Technology | [`apps/tech-makers.md`](./apps/tech-makers.md) |
| SIFISO — The Golden Hand | Creation & Technology | [`apps/the-golden-hand.md`](./apps/the-golden-hand.md) |
| Truth Seekers | Thinking & Reasoning | [`apps/truth-seekers.md`](./apps/truth-seekers.md) |
| Micro Founders | Real-World Empowerment | [`apps/micro-founders.md`](./apps/micro-founders.md) |
| Mzansi Money | Money & Opportunity | [`apps/mzansi-money.md`](./apps/mzansi-money.md) |

### Platform & World B

See [`platform/README.md`](./platform/README.md):

| Piece | File |
|---|---|
| TPH Core SDK | [`platform/tph-core.md`](./platform/tph-core.md) |
| People's Home Passport | [`platform/peoples-home-passport.md`](./platform/peoples-home-passport.md) |
| iKhaya | [`platform/ikhaya.md`](./platform/ikhaya.md) |
| iKhaya Learn | [`platform/ikhaya-learn.md`](./platform/ikhaya-learn.md) |

### Deep dives

| Directory | Purpose |
|---|---|
| [`decisions/`](./decisions/) | Full decision log — the *why* behind structural calls |
| [`history/`](./history/) | Archive of incidents, pivots, renames, and retired ideas |
| [`patterns/`](./patterns/) | Reusable architectural and UX patterns |
| [`research/`](./research/) | Research notes, benchmarks, competitive context |
| [`assets/`](./assets/) | Diagrams, wireframes, reference images |

---

## The project in one breath

> **The People's Home** is a Sovereign Learning System by **iKhaya AI**
> (an **ARISAN SIFISO Holdings** initiative, supported by
> **The People's Home Foundation NPC**).
>
> A complete pathway to *learn, think, build, earn, and create opportunity* —
> for every South African, regardless of age, income, location, or schooling.
>
> Ten deep **offline, free-forever** learning apps (World A).
> One server-backed **opportunity platform** (iKhaya / World B, launching 2027).
> A shared **TPH Core** carrying identity, progress, and rewards between them.
>
> **One Home. Many Journeys. One Future.**

---

## Connection to engine-1000

The People's Home is a **permanent child of the repository-engine-1000 project**
(GitHub: `SifisoScS/repository-engine-1000`). The engine tracks, manages, and
cross-references all TPH repositories. See:
- `engine-1000/docs/peoples-home/` — the engine-side cross-reference and tracking docs

This relationship means: every repo in this ecosystem should eventually be registered
in the engine. The engine is the sovereign infrastructure layer; The People's Home is
the flagship product portfolio running on top of it.
