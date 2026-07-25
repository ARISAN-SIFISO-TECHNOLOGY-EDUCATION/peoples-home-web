<!-- ============================================================
     BRAIN INTEGRATION HEADER — added when this document entered the Brain.
     Everything above the "═══ FOUNDER DOCUMENT ═══" divider is Brain metadata.
     Everything below it is the founder's document, reproduced faithfully.
     ============================================================ -->

# 📝 Institutional Platform Strategy — DRAFT (Waiting), *not adopted*

> **Status in the Brain:** 📝 **DRAFT — PROPOSED, NOT ADOPTED · not scheduled for implementation.**
> **Entered the Brain:** 2026-07-24 · **Author:** Founder · **Version:** 0.1 (Planning Document).
>
> This is a **strategic direction**, deliberately non-executable. It is **not Canon** — that is why
> it carries a descriptive name rather than a `0N-` canon number like its neighbours
> ([`01-capability-architecture.md`](./01-capability-architecture.md) … `05-…`), which are adopted
> law. It does not govern any current design decision. It becomes binding only through formal
> Architecture Decision Records and an implementation roadmap (see the document's §13).

## ⚠️ Two reconciliations required before this is adopted — founder rulings, recorded here so a later reader does not miss them

**1. The word "capability" already has an owner in this folder — this document gives it a second, different meaning.**

| Term | Existing meaning (Canon) | This document's meaning |
|---|---|---|
| **capability** | **What a *learner gains*** — the eight capability *categories* (`01-capability-architecture.md`): Foundations, Curiosity, Thinking… the real unit of educational value. | **A software *service function*** exposed to interfaces — `getVision()`, `recommendApp()`, `getLaunchStatus()`. |

Both senses appear in the Brain the moment this file lands, and a future reader searching *capability*
hits both. This is the same collision class the project has ruled on before — **Number Kingdom vs
Numeria** (D-16), the **"TPH Core" → "TPH Learning Engines"** rename (D-13). It wants a disambiguating
name for the *software* sense (candidates: **institutional service**, **platform service**,
**capability endpoint**) — **a founder ruling, not made here.** Note the platform already has a
"services" concept: `01`'s **TPH Core — shared SERVICES**, which this document's *Institutional
Capability Layer* substantially overlaps and may simply be the meta-scoped extension of.

**2. It must be reconciled with the offline / no-accounts DNA — which it does not contradict, but is easily read as contradicting.**

Product Rule #3–#4 ([`../vision/01-product-rules.md`](../vision/01-product-rules.md)) make World-A
learning apps **#FreeForever · offline · no accounts · no server · no tracking**. This document's
authentication, permissions, multi-tenancy and APIs describe the **institutional platform** (the
meta-layer: knowledge, governance, launch status — accessed via website / AI / dashboards), **not**
the learning apps. Read carelessly, *"the institutional operating platform for the entire ecosystem"*
(§11) reads as putting a server under the learning apps. It must state explicitly that it does **not**
— accounts/servers remain a **World B / iKhaya** concern (`02-world-a-world-b-dna.md`), and the
offline learning apps stay sovereign. **Flagged for the same ruling.**

*Neither reconciliation is performed here. A review records what it finds; it does not rewrite the
document to resolve it. See [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) when these are ruled.*

---

<!-- ═══════════════════ FOUNDER DOCUMENT (reproduced faithfully, v0.1) ═══════════════════ -->

# The People's Home

## Institutional Platform Architecture Strategy

### Version 0.1 (Planning Document)

**Status:** DRAFT (Waiting)
**Purpose:** Strategic architecture proposal
**Decision State:** Not adopted

---

# 1. Purpose

This document defines the long-term architectural direction for **The People's Home** as an institutional platform rather than a traditional website.

It exists to record a strategic direction that should guide future design decisions but is **not yet scheduled for implementation**.

---

# 2. The Architectural Shift

Traditional thinking begins with a website.

```text
Website
   │
   ▼
Business Logic
```

The People's Home adopts a different model.

```text
                The People's Home
             Institutional Platform
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
    Website        Mobile Apps     AI Interfaces
        │              │              │
        ▼              ▼              ▼
    Humans         Humans       AI Assistants
```

The institutional platform is the product.

Every interface is simply another way to access it.

---

# 3. Core Principle

> **The People's Home owns institutional knowledge, institutional behaviour, and institutional governance. Interfaces present those capabilities to different audiences.**

This means:

* the website is not the source of truth;
* mobile applications are not the source of truth;
* AI integrations are not the source of truth.

Only the platform owns institutional state.

---

# 4. Architectural Principles

## Principle 1 — Platform First

Business capability belongs to the platform.

Never place business rules inside:

* websites;
* mobile applications;
* MCP servers;
* AI prompts.

---

## Principle 2 — Interfaces are Replaceable

Interfaces are adapters.

Examples include:

* Website
* Android application
* iOS application
* ChatGPT
* Claude
* Voice assistants
* Future AI protocols

Replacing an interface must not require rewriting institutional behaviour.

---

## Principle 3 — Expose Capabilities, Not Storage

Interfaces request services.

Never expose implementation details.

Instead of:

```text
docs/vision.md
```

Expose:

```text
getVision()
```

Instead of:

```text
roadmaps/apps.md
```

Expose:

```text
searchRoadmaps()
```

The platform decides where information comes from.

---

## Principle 4 — Platform Owns Behaviour

The platform determines:

* recommendations;
* permissions;
* governance;
* launch readiness;
* learning pathways;
* institutional policies.

Interfaces determine only presentation.

---

## Principle 5 — Protocols Are Adapters

MCP is important.

It is **not** the foundation.

Tomorrow another protocol may exist.

Therefore:

```text
Platform

↓

Capabilities

↓

Protocol Adapter

↓

Client
```

Never:

```text
Platform

↓

MCP

↓

Everything else
```

---

# 5. Institutional Capability Layer

The People's Home exposes capabilities.

Examples include:

## Discovery

* recommendApp()
* compareApps()
* searchApps()

---

## Knowledge

* searchDocuments()
* getVision()
* searchResearch()
* searchArchitecture()

---

## Governance

* getLaunchStatus()
* getProjectStatus()
* listActiveProjects()
* listUpcomingReleases()

---

## Education

* recommendLearningPath()
* searchCurriculum()
* findLearningResources()

---

## Community

* registerBetaInterest()
* createSupportRequest()
* searchPublicKnowledge()

---

# 6. Interface Layer

Every interface consumes the same capabilities.

```text
                   Interfaces

Website
Mobile
Desktop
ChatGPT
Claude
Future AI
Voice

        │

        ▼

Institutional Capabilities
```

No interface owns institutional logic.

---

# 7. Access Control Model

Capabilities remain consistent.

Permissions determine what each audience may see.

## Public

Examples:

* Search apps
* Download links
* Public documentation
* Vision
* Public roadmap

---

## Authenticated

Examples:

* My certificates
* My progress
* Purchases
* Support requests
* Beta participation

---

## Internal

Examples:

* Repository health
* Operational dashboards
* Governance
* Planning
* Release pipeline
* Institutional Brain

The capability remains the same.

The representation changes according to authorisation.

---

# 8. Example

```text
getProjectStatus()
```

Public response

```text
African Discoveries

Public beta planned.

Educational focus:
African history.
```

Internal response

```text
African Discoveries

Status:
DO NOT LAUNCH

Outstanding:

• C7
• C8
• Accessibility
• Performance

Gate:
Phase 3 pending
```

One capability.

Different authorised views.

---

# 9. Proposed Internal Architecture

```text
                    Interfaces
     ┌────────────┬────────────┬────────────┐
     ▼            ▼            ▼
 Website      Mobile App    AI Adapter
     │            │            │
     └────────────┴────────────┘
                  │
      Institutional Capability Layer
                  │
      ┌───────────┼───────────┐
      ▼           ▼           ▼
  Apps        Knowledge   Governance
                  │
         Institutional Domain
                  │
 Knowledge • Users • Policies • Memory
                  │
          Infrastructure Layer
      Files • Database • Search • Storage
```

---

# 10. Relationship to MCP

MCP is treated as an interface adapter.

It exposes selected institutional capabilities to AI assistants.

Examples:

* ChatGPT
* Claude
* Future AI assistants

The People's Home does **not** become MCP-centric.

It remains protocol-independent.

---

# 11. Long-Term Vision

The People's Home should become the institutional operating platform for the entire ecosystem.

Future interfaces may include:

* Website
* Android applications
* iOS applications
* Desktop applications
* AI assistants
* Internal operational dashboards
* Automation workflows
* Voice interfaces

Every interface should consume the same institutional capabilities.

---

# 12. Deferred Questions

The following decisions remain intentionally unresolved:

* Public capability catalogue.
* Authentication architecture.
* Capability versioning.
* Multi-tenant support.
* Internal vs external APIs.
* Event architecture.
* Search indexing strategy.
* Capability discovery.
* AI permission model.
* Observability and auditing.
* Rate limiting.
* Protocol adapter architecture.

These should be addressed when implementation planning begins.

---

# 13. Future Decision Records

Implementation should not begin until the following institutional decisions have been adopted:

* Capability taxonomy.
* Identity and permission model.
* Public information policy.
* AI interaction policy.
* API governance.
* Protocol adapter strategy.
* Platform service boundaries.
* Institutional observability.

---

# 14. Success Criteria

This strategy is considered successful when:

* Every interface consumes institutional capabilities rather than storage.
* Business behaviour exists only within the platform.
* Multiple interfaces can coexist without duplicating logic.
* New protocols can be supported through adapters rather than architectural change.
* Public, authenticated, and internal users experience different authorised views of the same institutional capabilities.
* The People's Home remains the single source of institutional truth.

---

# 15. Current Status

**Status:** DRAFT (Waiting)

This document records a strategic architectural direction for The People's Home. It is intentionally non-executable and should not drive implementation until supported by formal architectural decision records and an implementation roadmap. It serves as the reference point for future discussions about websites, mobile applications, AI integrations, and protocol adapters, ensuring that all such interfaces evolve around a single institutional platform rather than becoming independent systems.
