# The People's Home — Engine Cross-Reference

> **The People's Home is a permanent child of this project.**
>
> The repository-engine-1000 is the sovereign infrastructure layer.
> The People's Home is the flagship product portfolio running on top of it.
>
> This document is the engine-side pointer to The People's Home. For the full
> institutional memory of TPH, see the peoples-home repo's `brain/` directory.
>
> **Last updated:** 2026-07-02

---

## What is The People's Home?

A national capability-building ecosystem for South Africa — 10 offline, free-forever
learning apps (World A) + the iKhaya opportunity platform (World B, 2027) + shared
infrastructure (TPH Core SDK, People's Home Passport).

**The mission:** Give every South African a free, offline pathway to learn, think,
build, earn, and create opportunity.

**One Home. Many Journeys. One Future.**

---

## Connection to engine-1000

| Dimension | Detail |
|---|---|
| Relationship | TPH is the flagship product that the engine was built to support |
| Builder | Same founder (Sifiso Cyprian Shezi) — single-person team |
| Engine role | Tracks all TPH repos, generates scaffolding, validates quality gates |
| Status | All World-A apps live as of 2026-06-27 |

The engine manages the infrastructure layer (~1000 repos). The People's Home sits
on top of it as the primary product ecosystem. This is not a client-server relationship
but a **vertical stack**: engine = foundation, TPH = the visible structure built on it.

---

## Repository overview

### Primary repo (this cross-reference)

| Repo | Location | What it is |
|---|---|---|
| `peoples-home` | `C:\Users\sifis\Next-Level-Projects\peoples-home` | The institutional memory hub and root documentation |

### World-A learning apps (all 10 live)

| App | Pillar | GitHub org | URL |
|---|---|---|---|
| Math Adventure RPG | Foundations | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | math-adventure-rpg.pages.dev |
| ReadAfrica | Foundations | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | read-africa.pages.dev |
| Everyday Foundations | Foundations | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | everyday-foundations.pages.dev |
| Science Sprouts | Curiosity & Knowledge | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | science-sprouts-65b.pages.dev |
| Our World | Curiosity & Knowledge | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | our-world-b0t.pages.dev |
| Tech Makers | Creation & Technology | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | tech-makers.pages.dev |
| SIFISO — The Golden Hand | Creation & Technology | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | sifiso-learn-python.pages.dev |
| Truth Seekers | Thinking & Reasoning | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | truth-seekers.pages.dev |
| Micro Founders | Real-World Empowerment | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | micro-founders.pages.dev |
| Mzansi Money | Money & Opportunity | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | mzansi-money.pages.dev |

**Foundations on-ramps (ages 3–7):** Early Numeracy
(`ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-numeracy`) — built, not yet deployed · Early Literacy
(`ARISAN-SIFISO-TECHNOLOGY-EDUCATION/early-literacy`) — **✅ LIVE at early-literacy.pages.dev** as an
installable offline PWA (built externally in Gemini; AI dropped for #FreeForever, deployed + audited
+ Phase-1 fixes, repo moved to org 2026-07-02). Integrated into the TPH Brain; see
`peoples-home/brain/apps/early-literacy.md`.

### Supporting systems

| System | Description | Location |
|---|---|---|
| Kilimanjaro | WhatsApp AI agent ("The People's Guide") | `C:\Users\sifis\Next-Level-Projects\kilimanjaro` |
| peoples-home-web | The People's Home website (Cloudflare Pages) | peoples-home-web.pages.dev |
| iKhaya | Opportunity platform prototype (World B) | Lovable / separate repo |

---

## Roadmap alignment with engine milestones

| TPH Milestone | Target | Engine Relevance |
|---|---|---|
| All 10 World-A apps live | ✅ 2026-06-27 | Phase complete — apps now enter deepening/platform phase |
| TPH Core SDK extraction | H2 2026 | Shared package; engine may help scaffold it |
| isiZulu review (all apps) | ~Dec 2026 | Batch content update across all 10 repos |
| iKhaya one-suburb beta | H2 2026 | World B infrastructure begins; different DNA from World A |
| Keystore backup | URGENT | Security risk — `upload-new.jks` must be backed up off-machine |
| iKhaya flagship launch | 2027 | World B goes live; funding fork must be resolved first |

---

## The six capability pillars (summary)

| # | Pillar | Apps |
|---|---|---|
| 1 | Foundations | Math Adventure RPG · ReadAfrica · Everyday Foundations |
| 2 | Curiosity & Knowledge | Science Sprouts · Our World |
| 3 | Creation & Technology | Tech Makers · SIFISO — The Golden Hand |
| 4 | Thinking & Reasoning | Truth Seekers |
| 5 | Real-World Empowerment | Micro Founders |
| 6 | Money & Opportunity | Mzansi Money |

---

## Key invariants (critical — do not violate)

1. All World-A apps are **offline, free, no-login, ages-not-grades, SA-first**.
2. All repositories are **PRIVATE**. Do not make any TPH repo public.
3. **iKhaya AI** (commercial entity) and **The People's Home Foundation NPC** are distinct.
4. The engine is **advisory only** for TPH — it never auto-executes TPH code.

---

## Full memory

For the complete institutional memory of The People's Home — vision, architecture,
decisions, history, per-app documentation — see:

```
C:\Users\sifis\Next-Level-Projects\peoples-home\brain\
```

Start with `brain/AI_ONBOARDING.md` if you have no prior context.
Start with `brain/SESSION_HANDOFF.md` if you are resuming a session.
