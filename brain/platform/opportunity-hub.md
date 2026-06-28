# Opportunity Hub — iKhaya's Flagship Module

> **World B · iKhaya platform · flagship product.**
> This is the permanent definition of Opportunity Hub. Every AI working on this
> module must read this file first.
>
> **Authored:** 2026-06-27 · **Change protocol:** append only. Decisions to `brain/decisions/DECISIONS.md`.
> **Build playbook:** [`../playbooks/build-opportunity-hub.md`](../playbooks/build-opportunity-hub.md)
> **Platform context:** [`ikhaya.md`](./ikhaya.md)

---

## What Opportunity Hub is NOT

Before defining what it is: what it is not.

It is **not** a job board.
It is **not** LinkedIn, Indeed, Glassdoor, Careers24, or Job Mail.
It is **not** another app in the learning stack (teaching happens in World A).
It is **not** the iKhaya platform itself (iKhaya is the platform; this is a module within it).

If you are thinking "jobs app" — stop. That is a narrow slice of one of six opportunity types.

---

## The Single Sentence

> **Opportunity Hub is the transition layer of The People's Home, transforming demonstrated
> capability into discoverable real-world opportunities by matching learners, workers,
> founders, and families with education, employment, entrepreneurship, funding, and
> community pathways.**

---

## Purpose

The learning apps (World A) build capability. Opportunity Hub does not teach.

**Opportunity Hub connects capable people with real opportunities.**

Every learner who completes a journey in Math Adventure, or builds a venture in Micro Founders,
or earns a financial literacy badge in Mzansi Money — that learner has grown. They have
demonstrated something real. The question Opportunity Hub answers is:

> *Now that I have this capability — what doors can it open?*

---

## Mission

> To ensure that every learner, regardless of background, can discover pathways to
> education, work, entrepreneurship, funding, and community opportunities that match
> their growing capabilities.

Not: *find jobs.*
But: *discover pathways.* That is a fundamentally wider mandate.

---

## Vision

> A South Africa — and ultimately an Africa — where no opportunity remains hidden
> from someone who has the capability to pursue it.

This is an **opportunity equity platform**. The problem it solves is not that opportunities
don't exist. It is that they are invisible to the people who could pursue them.

---

## The Philosophy Chain

```
Capability
    ↓  (built in World A — the 10 learning apps)

Confidence
    ↓  (earned through journey completion, stamps, achievements)

Readiness
    ↓  (signalled through Capability Profile in TPH Core)

Opportunity
    ↓  (discovered through Opportunity Hub's 6 types + 7 engines)

Real-World Outcomes
       (education enrolled, job offered, venture funded, community joined)
```

Opportunity Hub owns only the last two steps. World A owns the first three.

---

## Position in The Ecosystem

```
The People's Home
├── World A (10 offline learning apps)
│     └── TPH Core SDK
│           └── Capability Profile ──────────────────────┐
│                                                         │ (with user consent)
└── World B                                               │
      └── iKhaya  ← the platform                         ↓
            ├── Opportunity Hub  ← THIS MODULE    7. Intelligence Engine
            │     (6 types · 7 engines)                  │
            ├── Learning Hub                              │
            ├── Skills Passport                           ↓
            ├── Funding Hub              Real-World Outcomes
            ├── Career Hub
            ├── Entrepreneurship Hub
            ├── Community Hub
            └── Future Modules
```

**iKhaya is the platform. Opportunity Hub is iKhaya's flagship product.**
This distinction must never collapse. Opportunity Hub is one module — iKhaya will grow to hold many.

---

## The 6 Opportunity Types

Every screen in Opportunity Hub serves one or more of these six types.

---

### 1. 🎓 Education

Opportunities that continue or formalise learning.

Examples:
- Bursaries and scholarships (merit-based and needs-based)
- Learnerships (SETA-accredited workplace learning)
- Apprenticeships
- Short courses and skills programmes
- University entrance pathways
- TVET College programmes
- Online learning platforms and certifications
- Further Education and Training (FET)

**Target:** learners who have reached a readiness level for formal education pathways.

---

### 2. 💼 Employment

Opportunities to earn income through formal or informal work.

Examples:
- Entry-level jobs and positions
- Internships and work-integrated learning
- Graduate programmes
- Casual and seasonal work
- Part-time and flexible roles
- YES Programme opportunities (Youth Employment Service)
- Public sector and municipal opportunities

**Target:** learners who have demonstrated capabilities that match employer needs.

---

### 3. 🚀 Entrepreneurship

Opportunities to build ventures and receive support.

Examples:
- Business incubators and accelerators
- Startup competitions and pitch events
- Entrepreneurship programmes (NYDA, SBP, etc.)
- Mentorship matching
- Co-working and shared resources
- SMME development programmes
- Franchise and licensing opportunities

**Target:** learners who have completed Micro Founders or Mzansi Money journeys, or have
demonstrated business-thinking capability.

---

### 4. 💰 Funding

Opportunities to access capital without employment.

Examples:
- Grants (SEDA, DTI, NYDA)
- Seed funding and angel investment
- Business competitions with cash prizes
- Government support programmes
- NGO and foundation funding
- Cooperative formation support
- Community savings schemes (stokvels)

**Target:** entrepreneurs and community builders who need capital to act on their capabilities.

---

### 5. 🤝 Community

Opportunities to contribute, connect, and lead.

Examples:
- Volunteering programmes
- Community development projects
- Youth leadership initiatives
- Civic and ward-level participation
- Sports, arts, and cultural programmes
- Environmental and social impact projects
- Peer mentoring and tutoring roles

**Target:** any learner who wants to act in their community with the capabilities they've built.

---

### 6. 🌍 Global & Digital Opportunities

Opportunities that transcend geography and connect South Africans to the wider world.

Examples:
- Freelancing platforms (Upwork, Fiverr, Toptal)
- Remote work opportunities (internationally distributed companies)
- Open-source contribution (GitHub, GitLab)
- Hackathons and coding competitions
- AI challenges and data science competitions
- Digital content creation (YouTube, podcasts, Substack)
- International exchange and fellowship programmes

**Target:** learners with Tech Makers, SIFISO — The Golden Hand, or Truth Seekers capability
who can work beyond SA borders.

---

## The 7 Engines

Opportunity Hub is not a content platform. It is an engine system.

---

### Engine 1: Opportunity Engine

**Purpose:** Store, index, and serve all opportunity records.

Every opportunity has:

| Field | Examples |
|---|---|
| `title` | "NYDA Youth Business Grant" |
| `category` | `education | employment | entrepreneurship | funding | community | digital` |
| `type` | More specific (bursary, internship, grant, volunteering...) |
| `location` | National / province / city / remote |
| `requirements` | Age range, qualification level, province eligibility |
| `closingDate` | ISO date |
| `organisation` | NYDA, Anglo American, SEDA... |
| `skills` | Linked to TPH Core capability tags |
| `ageRange` | Ages not grades |
| `languages` | English, isiZulu, Afrikaans... |
| `applicationProcess` | Link / form / walk-in |
| `isFree` | Boolean |
| `status` | Active / closing-soon / closed |

This engine is the data foundation. All other engines consume it.

---

### Engine 2: Eligibility Engine

**Purpose:** Answer the question "Can I apply?" without making the learner read 300 requirements.

Instead of a wall of text, the engine surfaces:

```
✓ Age requirement met (17 — within 16–25 range)
✓ Province eligible (KwaZulu-Natal — included)
✓ Qualification eligible (Grade 10 completed — meets minimum)
⚠ One requirement missing: you need a South African ID document
✗ Income eligibility not met (household income above threshold)
```

The eligibility check uses the learner's local profile (filled in manually or drawn
from the Capability Profile with consent). It never blocks browsing — it informs readiness.

---

### Engine 3: Discovery Engine

**Purpose:** Help learners find opportunities they didn't know existed.

Search becomes:

```
Show me opportunities for:
• Someone aged 17
• Based in KwaZulu-Natal
• Interested in technology and entrepreneurship
• Opportunities that are free to apply
• Closing in the next 60 days
```

The Discovery Engine powers:
- Full-text search
- Category, type, and location filters
- Age-range filtering (never by grade)
- Language preference
- Closing-date urgency sorting
- Opportunity Intelligence Engine recommendations (see Engine 7)

Works with locally cached opportunity data when offline.

---

### Engine 4: Application Engine

**Purpose:** Help learners prepare and track their applications.

The problem it solves: most South African learners have never written a CV, a motivation
letter, or prepared a document checklist. The Application Engine guides them through:

- **Preparation workspace**: what documents do I need?
- **CV builder**: structured, exportable, offline-capable
- **Motivation letter template**: guided writing, not blank-page terror
- **Document checklist**: tick as you gather
- **Deadline tracker**: what's due and when?
- **Application record**: where did I apply? When? What happened?

The Application Engine does not submit applications (most go via external sites or
walk-in). It prepares the learner to submit successfully.

---

### Engine 5: Progress Engine

**Purpose:** Track the learner's journey from interest to outcome.

Instead of a simple "Applied" status, the learner moves through:

```
Interested      → I found this opportunity; I want to know more
    ↓
Preparing       → I'm gathering documents, writing my letter
    ↓
Applied         → I submitted my application
    ↓
In Progress     → Waiting / Interview / Assessment
    ↓
Outcome         → Accepted / Declined / Withdrawn
```

Progress is stored locally. The learner owns their history.
Progress data is never sent to the opportunity provider without explicit consent.

---

### Engine 6: Notification Engine

**Purpose:** Surface relevant opportunities at the right time, without overwhelming.

**Offline-first design:**
- Opportunity preferences are stored locally
- When connectivity is available, the engine syncs and checks for new matches
- Notifications are generated locally based on locally cached data
- No push notification infrastructure required for the core feature
- Optional: cloud push notifications when accounts are introduced (Phase 10)

**Notification rules:**
- Only opportunities that match the learner's stated interests and eligibility
- Urgency alerts (closing in 7 days / 48 hours)
- New opportunities in saved categories
- No unsolicited notifications — the learner controls their preferences

---

### Engine 7: Opportunity Intelligence Engine

**Purpose:** Transform the learner's demonstrated capability into ranked, personalised
opportunity recommendations.

This is what separates Opportunity Hub from a directory.

Instead of:
> "Here are 847 opportunities."

The Intelligence Engine asks:
> "This learner has completed 3 Math Adventure journeys, earned a Tech Makers badge,
> and marked interest in entrepreneurship. What opportunities match what they have built?"

**How it works:**

1. The Capability Profile (from TPH Core SDK) signals what the learner has demonstrated
   (with explicit user consent — never automatic)
2. Opportunity records are tagged with capability requirements (linked to TPH Core tags)
3. The Intelligence Engine matches capability signals to opportunity requirements
4. An AI layer (Claude) refines and ranks recommendations, explains why each is relevant,
   and surfaces opportunities the learner might not have searched for

**Privacy constraint:** Capability matching is local by default. Cloud AI ranking only
activates if the learner explicitly enables it. The system is useful without cloud
— the Intelligence Engine degrades to local tag-matching when offline.

---

## Relationship to World A

World A builds the capability. Opportunity Hub helps realise its value.

**The handoff points:**
- **Mzansi Money** → learner completes a Money Journey → Opportunity Hub: Employment + Funding
- **Micro Founders** → learner completes a Venture Journey → Opportunity Hub: Entrepreneurship + Funding
- **Tech Makers / SIFISO** → learner completes a coding track → Opportunity Hub: Digital + Employment
- **All apps** → Capability Profile grows → Intelligence Engine improves its matching

**Privacy rule:** the Capability Profile flows into Opportunity Hub only with explicit,
revocable user consent. No automatic profiling. The learner decides.

---

## Relationship to TPH Core SDK

TPH Core generates the Capability Profile — the summary of what a learner has demonstrated
across all World-A apps. The Intelligence Engine consumes this.

TPH Core also provides:
- Progress tracking (used to infer readiness signals)
- People's Home Passport (the cross-app identity layer)
- Shared activity types and milestone records

Opportunity Hub does not build its own identity layer. It consumes TPH Core's.

---

## Relationship to iKhaya

**iKhaya is the platform. Opportunity Hub is the flagship module.**

iKhaya will eventually contain multiple modules:
- Opportunity Hub (this module — first)
- Learning Hub (server-backed tutoring — related to iKhaya Learn)
- Skills Passport (formal credentials and verified achievements)
- Funding Hub (dedicated funding discovery)
- Career Hub (long-term career pathway navigation)
- Entrepreneurship Hub (venture building support)
- Community Hub (local community projects and coordination)
- Future Modules (not yet defined)

Opportunity Hub sets the foundation — its engines, design patterns, and data model
will be reused and extended by future iKhaya modules.

---

## Architectural Tensions to Hold

These tensions must be actively managed. Do not resolve them by collapsing one side.

---

**1. Offline-capable UI vs. live opportunity data**

The UI and core discovery must work offline (cached data). But opportunities go stale —
closing dates pass, organisations update requirements. The resolution:

- Cache a recent snapshot of opportunity data locally (via sync when online)
- Show "last updated" timestamps so learners know when data is fresh
- Mark stale opportunities clearly
- Never block browsing because sync hasn't happened yet

---

**2. Privacy-first vs. capability-based personalisation**

The Intelligence Engine can give better results with more profile data. But The People's Home
never profiles learners without consent. The resolution:

- Local matching by default (works without any data leaving the device)
- Cloud matching is opt-in, revocable, clearly explained before activation
- No silent data collection; no inferred profiles
- The system is useful at every privacy level

---

**3. #FreeForever vs. backend costs**

Opportunity Hub requires server infrastructure (opportunity database, sync,
AI-assisted matching). This costs money. The resolution:

- Not yet resolved — this is the **#FreeForever funding fork** (see `ikhaya.md`)
- Candidate approaches: Foundation grants, Microsoft-for-Startups Azure credits,
  freemium opportunity listings (free to apply; paid for organisations to post featured listings)
- **Do not build a paywall for learners.** Ever.

---

## Guiding Principles

1. **Capability-first, not job-first.** Opportunities are matched to what someone has built,
   not filtered by what qualifications they lack.

2. **Opportunity equity.** The Hub exists precisely for the learner who doesn't know
   where to look. Surface what is hidden. Don't assume the user knows the landscape.

3. **Privacy by default.** No profiling without consent. Local first. Cloud opt-in.

4. **Opportunity breadth before depth.** Six types, not one. A learner's next step could
   be education, volunteering, or a digital freelance project — not necessarily a job.

5. **Dignity-first UX.** Never make the learner feel unqualified or rejected by the interface.
   "⚠ One requirement missing" is helpful. "You don't meet the criteria" is harmful.

6. **Offline-capable core.** The Discovery and Progress Engines work without connectivity.
   Sync is a feature, not a dependency.

7. **Africa-ready, SA-first.** The platform is built for South Africa. It must scale to
   the continent without needing a redesign. Use universal opportunity frameworks (not
   SA-specific jargon) where possible; localise content, not structure.

8. **Measurable outcomes.** Success is not "opportunities listed." Success is "pathways taken."
   Track the full chain from discovery to real-world outcome.

---

## Success Metrics

What "working" looks like — at every level:

| Metric | Definition |
|---|---|
| **Opportunities discovered** | Browse or search sessions where ≥1 opportunity was viewed |
| **Applications started** | Learner entered the Application Engine for a specific opportunity |
| **Applications completed** | Learner marked an application as submitted |
| **Opportunities accepted** | Learner marked an outcome as accepted / enrolled / hired / funded |
| **Learner transitions** | Learner moved from World-A learning into a confirmed real-world pathway |

The ultimate metric is **learner transitions**. Every other metric is a leading indicator.

---

## Current Status

**Phase 4–6 Live — 2026-06-28**

| Phase | Status | Date |
|---|---|---|
| 1 — Vision & Brain | ✅ Complete | 2026-06-27 |
| 2 — Domain model | ✅ Complete (as TypeScript types) | 2026-06-28 |
| 3 — UX & navigation | ✅ Complete (built alongside Phase 4) | 2026-06-28 |
| 4 — Offline-first foundation | ✅ Complete | 2026-06-28 |
| 5 — Discovery engine | ✅ Complete | 2026-06-28 |
| 6 — Eligibility engine (MVP) | ✅ Complete | 2026-06-28 |
| 7 — Application workspace | ⏳ Not started | — |
| 8 — Synchronisation layer | ⏳ Not started | — |
| 9 — Opportunity Intelligence Engine | ⏳ Not started | — |
| 10 — Production hardening | ⏳ Not started | — |

**Live URL:** https://ikhaya.pages.dev/
**Repo:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/ikhaya` (private)
**Stack:** Vite + React 19 + TypeScript + vite-plugin-pwa + idb + react-router-dom
**Deploy:** Cloudflare Pages, autodeploy from main
**Seed data:** 25 real SA opportunities across all 6 types
**Offline:** ✅ Service worker + workbox precaching active

---

## Build Playbook

For the phased implementation plan (Phases 1–10), see:
[`../playbooks/build-opportunity-hub.md`](../playbooks/build-opportunity-hub.md)

Phase 2 begins with the domain model. Do not start Phase 2 without:
1. This document reviewed and confirmed by the founder
2. `build-opportunity-hub.md` read and Phase 2 inputs confirmed as ready
