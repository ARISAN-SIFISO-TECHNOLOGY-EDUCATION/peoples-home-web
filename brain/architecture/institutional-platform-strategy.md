<!-- ============================================================
     BRAIN INTEGRATION HEADER — added when this document entered the Brain.
     Everything above the "═══ FOUNDER DOCUMENT ═══" divider is Brain metadata.
     Everything below it is the founder's document, reproduced faithfully.
     ============================================================ -->

# 📝 Institutional Platform Strategy — DRAFT (Waiting), *not adopted*

> **Status in the Brain:** 📝 **DRAFT — PROPOSED, NOT ADOPTED · not scheduled for implementation.**
> **Entered the Brain:** 2026-07-24 · **Author:** Founder · **Version:** 0.2 (revised 2026-07-24 per **D-18**).
>
> This is a **strategic direction**, deliberately non-executable. It is **not Canon** — that is why
> it carries a descriptive name rather than a `0N-` canon number like its neighbours
> ([`01-capability-architecture.md`](./01-capability-architecture.md) … `05-…`), which are adopted
> law. It does not govern any current design decision. It becomes binding only through formal
> Architecture Decision Records and an implementation roadmap (see the document's §13).
>
> **v0.1 → v0.2 (2026-07-24):** the software layer was renamed **"capabilities" → "Institutional
> Services"** throughout, per **D-18**. The original v0.1 term is preserved only in the git history,
> not restated here — a living document is corrected, not annotated line-by-line.

## ✅ The two entry reconciliations are now RESOLVED by founder ruling — the document nonetheless remains DRAFT

Both flags raised when this document entered the Brain have been ruled on. **Neither ruling lets it
leave DRAFT** — its own §13 still lists the eight decisions required before implementation.

**1. ✅ RESOLVED by [D-18](../decisions/DECISIONS.md) — the "capability" collision.**
`01-capability-architecture.md` owns **"capability" = what a *learner gains*** (the eight categories).
This document originally reused it for a *software service function*. **D-18 renamed the software layer
to "Institutional Services" and reserved "capability" exclusively for human development** — the same
mechanism as **Number Kingdom vs Numeria (D-16)** and the **"TPH Core" rename (D-13)**. The rename is
applied throughout the body below. (Layering the ruling surfaced: **Institutional Services** — *what
the institution does* — sit above **TPH Core shared services** — *how apps implement their
responsibilities* — above infrastructure.)

**2. ✅ RESOLVED by [D-19](../decisions/DECISIONS.md) — the offline-DNA boundary.**
The auth/permissions/API machinery describes the institutional meta-layer, not the learning apps.
**D-19 makes this a constitutional boundary: the Institutional Platform may describe, distribute and
recommend World A, but is never a *runtime dependency* of it.** §11's *"institutional operating
platform for the entire ecosystem"* is to be read under D-19 — World A stays #FreeForever, offline and
account-free; accounts/servers remain a **World B / iKhaya** concern
([`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md)).

*The rulings were recorded as decisions (D-18, D-19) and the ruled rename applied; the founder's
strategic content is otherwise unchanged. Everything else in the document remains proposal, not law.*

---

<!-- ═══════════════════ FOUNDER DOCUMENT (reproduced faithfully, v0.1) ═══════════════════ -->

# The People's Home

## Institutional Platform Architecture Strategy

### Version 0.2 (Planning Document)

**Status:** DRAFT (Waiting)
**Purpose:** Strategic architecture proposal
**Decision State:** Not adopted
**Revised:** 2026-07-24 (D-18 — software layer renamed to *Institutional Services*)

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

> **The People's Home owns institutional knowledge, institutional behaviour, and institutional governance. Interfaces present those institutional services to different audiences.**

This means:

* the website is not the source of truth;
* mobile applications are not the source of truth;
* AI integrations are not the source of truth.

Only the platform owns institutional state.

---

# 4. Architectural Principles

## Principle 1 — Platform First

Business logic belongs to the platform.

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

## Principle 3 — Expose Institutional Services, Not Storage

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

Institutional Services

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

# 5. Institutional Services Layer

> **Term note (D-18):** these are **Institutional Services** — *what the institution does*. Not to be
> confused with **capability**, reserved in this project for *what a learner gains*
> ([`01-capability-architecture.md`](./01-capability-architecture.md)).

The People's Home exposes institutional services.

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

Every interface consumes the same institutional services.

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

Institutional Services
```

No interface owns institutional logic.

---

# 7. Access Control Model

Institutional services remain consistent.

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

The service remains the same.

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

One service.

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
      Institutional Services Layer
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

It exposes selected institutional services to AI assistants.

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

Every interface should consume the same institutional services.

---

# 12. Deferred Questions

The following decisions remain intentionally unresolved:

* Public service catalogue.
* Authentication architecture.
* Service versioning.
* Multi-tenant support.
* Internal vs external APIs.
* Event architecture.
* Search indexing strategy.
* Service discovery.
* AI permission model.
* Observability and auditing.
* Rate limiting.
* Protocol adapter architecture.

These should be addressed when implementation planning begins.

---

# 13. Future Decision Records

Implementation should not begin until the following institutional decisions have been adopted:

* Service taxonomy.
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

* Every interface consumes institutional services rather than storage.
* Business behaviour exists only within the platform.
* Multiple interfaces can coexist without duplicating logic.
* New protocols can be supported through adapters rather than architectural change.
* Public, authenticated, and internal users experience different authorised views of the same institutional services.
* The People's Home remains the single source of institutional truth.

---

# 15. Current Status

**Status:** DRAFT (Waiting)

This document records a strategic architectural direction for The People's Home. It is intentionally non-executable and should not drive implementation until supported by formal architectural decision records and an implementation roadmap. It serves as the reference point for future discussions about websites, mobile applications, AI integrations, and protocol adapters, ensuring that all such interfaces evolve around a single institutional platform rather than becoming independent systems.
