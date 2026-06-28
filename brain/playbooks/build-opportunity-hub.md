# Build Playbook — Opportunity Hub

> **Phased implementation blueprint for Opportunity Hub.**
>
> This is not a coding session. It is the reference that every future AI and developer
> follows when building begins. Each phase has a clear goal, defined inputs, and a
> specific "done" condition. Do not begin a phase until its inputs are confirmed ready.
>
> **Definition reference:** [`../platform/opportunity-hub.md`](../platform/opportunity-hub.md)
> **Platform context:** [`../platform/ikhaya.md`](../platform/ikhaya.md)
>
> **Current status:** Phase 1 complete. All other phases pending.

---

## Phase Map

| Phase | Name | Status |
|---|---|---|
| 1 | Vision & Brain | ✅ Complete (2026-06-27) |
| 2 | Domain model | ⏳ Not started |
| 3 | UX & navigation | ⏳ Not started |
| 4 | Offline-first foundation | ⏳ Not started |
| 5 | Opportunity discovery engine | ⏳ Not started |
| 6 | Eligibility engine | ⏳ Not started |
| 7 | Application workspace | ⏳ Not started |
| 8 | Synchronisation layer | ⏳ Not started |
| 9 | Opportunity Intelligence Engine | ⏳ Not started |
| 10 | Production hardening | ⏳ Not started |

---

## Phase 1 — Vision & Brain

**Status: ✅ Complete — 2026-06-27**

**Goal:** Lock the canonical definition of Opportunity Hub permanently in the brain before
any code is written.

**Done:** `brain/platform/opportunity-hub.md` created. Plan approved. Brain updated.

---

## Phase 2 — Domain Model

**Status: ⏳ Not started**

**Goal:** Define the complete data model before touching any code. Every entity, every
relationship, every key field. This is the schema that all future phases build on.

### Inputs needed before starting
- [ ] Phase 1 confirmed complete (the vision document is reviewed and approved)
- [ ] Technology stack decision: what database? (PostgreSQL / SQLite / Supabase / PlanetScale)
- [ ] Hosting decision: where does the iKhaya backend live? (Railway / Supabase / Render)

### Key decisions to make
1. **Entity ownership**: which entities are local-only (device) vs. server-side?
2. **Capability Profile shape**: how does TPH Core express a learner's capabilities?
   What tags, scores, or achievement records does it export?
3. **Opportunity data source**: how are opportunities ingested? (manual curation / scraping /
   partner API / curated CSV?) This affects the data model significantly.
4. **Learner identity model**: is there a server-side account, or is identity purely
   local (Passport JSON)?

### Entities to define

| Entity | Description | Local / Server |
|---|---|---|
| `Opportunity` | A real-world opportunity with all fields | Server (canonical) + Local (cached) |
| `Organisation` | The entity posting the opportunity | Server |
| `OpportunityTag` | Capability tags linking to TPH Core | Server |
| `UserProfile` | Learner's stated profile (age, province, interests) | Local |
| `CapabilitySignal` | What TPH Core exports about a learner | Local (consent required for cloud) |
| `EligibilityResult` | Computed result of eligibility check | Local (derived) |
| `ApplicationRecord` | Learner's track of one specific application | Local |
| `ProgressStage` | One stage in the application pipeline | Local |
| `SavedOpportunity` | Bookmarked opportunity | Local |
| `SyncRecord` | When local data was last synced | Local |

### Key files to create
- `docs/domain-model.md` — entity relationship diagram + all field definitions
- `docs/capability-profile-spec.md` — the exact shape of the Capability Profile
  as exported from TPH Core (coordinate with TPH Core SDK extraction)

### Done condition
- All entities documented with fields and types
- All relationships diagrammed (entity relationship diagram)
- Local vs. server ownership decided for every entity
- Tech stack selected and justified
- No code written yet

### POPIA/Security considerations
- `UserProfile` contains PII: age, location, language preference — store locally, encrypt at rest
- `CapabilitySignal` is potentially sensitive: it reflects a learner's progress history
- All server-side entities are subject to POPIA data subject rights (access, deletion, correction)
- Define the data retention policy before writing any schema migrations

---

## Phase 3 — UX & Navigation

**Status: ⏳ Not started**

**Goal:** Design the user experience before building it. Define the journey for each
of the 6 opportunity types. No code; only journeys, wireframes, and navigation maps.

### Inputs needed before starting
- [ ] Phase 2 complete (domain model confirmed)
- [ ] Decision: native app (React Native) vs. PWA (React + Vite) for the iKhaya frontend

### Key decisions to make
1. **Entry point**: how does a learner arrive at Opportunity Hub? (From the TPH website?
   From a World-A app? From a WhatsApp message from Kilimanjaro? All of the above?)
2. **Onboarding**: does the learner fill in a profile, or can they browse anonymously first?
3. **Home screen**: what does the user see first? Categories? Recommendations? Search?
4. **Navigation structure**: tab bar? sidebar? card-based home?

### User journeys to design (one per opportunity type)

For each of the 6 types, document:
- The entry scenario ("A 17-year-old in KZN who just finished Micro Founders...")
- The first screen they see
- The path to finding a relevant opportunity
- The eligibility check moment
- The application preparation moment
- The progress tracking moment
- The outcome recording moment

### Key files to create
- `docs/ux/user-journeys.md` — all 6 opportunity type journeys
- `docs/ux/navigation-map.md` — the full navigation structure
- `docs/ux/wireframes/` — low-fidelity wireframes for key screens

### Done condition
- All 6 user journeys documented
- Navigation structure agreed
- Home screen wireframe approved
- Onboarding flow decided

### POPIA/Security considerations
- Anonymous browsing must be the default — no forced onboarding
- Profile data (if collected during onboarding) must be clearly labelled as optional
- "Why do we ask this?" explanations for every data field collected

---

## Phase 4 — Offline-First Foundation

**Status: ⏳ Not started**

**Goal:** Build the shell of the Opportunity Hub app with offline capability proven
before any real feature is built. A working PWA that can browse cached opportunity data
with zero connectivity.

### Inputs needed before starting
- [ ] Phase 3 complete (UX/navigation decided)
- [ ] Tech stack confirmed (Vite + React + TypeScript assumed)
- [ ] PWA manifest assets ready (icons, theme colour, name)

### Key files to create
- `vite.config.ts` — with `vite-plugin-pwa` configured
- `public/manifest.json` — PWA manifest
- `src/` — project scaffold (see `brain/playbooks/new-app.md` for the standard pattern)
- `src/offline/syncManager.ts` — manages offline/online state and sync triggers
- `src/storage/opportunityStore.ts` — local IndexedDB schema and CRUD
- `src/storage/profileStore.ts` — local profile storage
- `src/storage/applicationStore.ts` — local application records
- `public/_redirects` — SPA routing for Cloudflare Pages: `/* /index.html 200`

### Key decisions to make
1. **IndexedDB library**: use `idb` (recommended) vs raw IndexedDB
2. **Opportunity data seed**: what does the initial cached dataset look like?
   (Can use a static JSON of curated SA opportunities for the MVP)
3. **Sync trigger**: on app open? On user request? Timer? All of the above?

### Done condition
- App loads and renders with network offline (Chrome DevTools → Offline verified)
- Service worker caches app shell
- Can browse a hardcoded seed dataset of 20 opportunities offline
- localStorage/IndexedDB schema established with correct namespacing
- Zero API calls in the critical path

### POPIA/Security considerations
- Namespace all localStorage/IndexedDB keys: `tph_oh_*` (no collisions with other TPH apps)
- No opportunity data contains PII about other users
- Static seed dataset: verify all opportunity data is publicly available and correctly attributed

---

## Phase 5 — Opportunity Discovery Engine

**Status: ⏳ Not started**

**Goal:** Build the full search, filter, and browse experience using locally cached data.
A learner should be able to find a relevant opportunity without any connectivity.

### Inputs needed before starting
- [ ] Phase 4 complete (offline foundation working)
- [ ] Seed dataset of ≥50 real SA opportunities (manually curated or scraped)
- [ ] All 6 opportunity types represented in the seed data

### Key files to create
- `src/engines/discoveryEngine.ts` — search, filter, and browse logic
- `src/components/OpportunityCard.tsx` — opportunity display component
- `src/components/SearchBar.tsx` — search input with instant results
- `src/components/FilterPanel.tsx` — category, province, age, closing date filters
- `src/pages/DiscoverPage.tsx` — the main browse/search screen
- `src/pages/OpportunityDetailPage.tsx` — full opportunity detail view

### Done condition
- Search returns results as the learner types (debounced, instant)
- Can filter by all 6 opportunity types
- Can filter by province, age, closing date
- Results show clearly: title, category, organisation, closing date, province
- Works with zero connectivity (all from local cache)
- Empty state handled gracefully ("No results — try a broader search")
- Stale data indicator shown if cache is >7 days old

### POPIA/Security considerations
- Search queries must not be logged or sent to any server
- Filter state lives in component state only (not persisted between sessions unless user opts in)

---

## Phase 6 — Eligibility Engine

**Status: ⏳ Not started**

**Goal:** Build the "Can I apply?" feature. The learner fills in a profile and the engine
evaluates their eligibility for each opportunity without them having to read every requirement.

### Inputs needed before starting
- [ ] Phase 5 complete (Discovery Engine working)
- [ ] UserProfile storage layer from Phase 4 confirmed ready
- [ ] Eligibility rules defined for the seed dataset (what fields are checked?)

### Key files to create
- `src/engines/eligibilityEngine.ts` — computes eligibility from profile + opportunity
- `src/components/EligibilityBadge.tsx` — ✓ / ⚠ / ✗ indicator on opportunity cards
- `src/components/EligibilityDetail.tsx` — full breakdown of what meets/doesn't meet requirements
- `src/pages/ProfilePage.tsx` — learner fills in their profile (age, province, qualification, language)
- `src/storage/profileStore.ts` — update schema with all eligibility-relevant fields

### Eligibility fields to implement (MVP)
- Age (compared to `ageRange` in opportunity)
- Province (compared to `location` in opportunity)
- Qualification level (e.g., Grade 9 / Grade 12 / Diploma / Degree)
- South African citizenship / ID document

### Done condition
- Learner can fill in profile in <2 minutes
- Eligibility badge shows on every opportunity card (✓ eligible / ⚠ partial / ✗ not eligible / — unknown)
- Detailed breakdown available on opportunity detail page
- Profile editable at any time without re-entering everything
- Profile stored locally (never sent to server without consent)

### POPIA/Security considerations
- Profile is the most sensitive local data: age + province is location-ish data
- Encryption at rest for IndexedDB profile data (use Web Crypto API)
- Clear "your profile stays on your device" explanation in the UI
- Deletion: "Clear my profile" option must exist and actually delete the data

---

## Phase 7 — Application Workspace

**Status: ⏳ Not started**

**Goal:** Help learners prepare and track their applications. The Application Engine turns
"I want to apply" into "I have submitted."

### Inputs needed before starting
- [ ] Phase 6 complete (Eligibility Engine working)
- [ ] Understanding of the most common SA application requirements (from seed dataset research)

### Key files to create
- `src/engines/applicationEngine.ts` — application state management
- `src/pages/ApplicationWorkspacePage.tsx` — the full workspace for one application
- `src/components/CVBuilder.tsx` — structured CV creation (name, contact, education, experience, skills)
- `src/components/MotivationHelper.tsx` — guided motivation letter structure
- `src/components/DocumentChecklist.tsx` — tick-off list for required documents
- `src/components/DeadlineTracker.tsx` — days until closing date, urgency indicator
- `src/pages/ApplicationsListPage.tsx` — all applications in progress/completed

### CV fields for SA context
- Full name
- ID number (optional, stored locally only)
- Contact: phone + email
- Location: city / province
- Education: institution, level, year
- Experience: role, employer, duration (even informal/volunteer work)
- Skills: tagged from TPH Core Capability Profile if available
- Languages: spoken and written
- References (optional)

### Done condition
- Learner can start an application workspace for any opportunity in one tap
- CV builder produces a readable, structured CV (exportable to PDF or shareable text)
- Motivation letter helper guides through introduction / why this opportunity / what I bring
- Document checklist customisable per opportunity
- Deadline shown prominently with urgency colouring (green > 30 days, yellow 7–30, red < 7)
- Application record saved locally with full history

### POPIA/Security considerations
- CV data is highly sensitive PII: full name, ID number, contact, work history
- ID number must be optional and must not be transmitted anywhere by default
- Export to PDF must warn "your ID number is in this document — share carefully"
- Deletion: clearing an application workspace must clear all CV data for that application

---

## Phase 8 — Synchronisation Layer

**Status: ⏳ Not started**

**Goal:** Keep opportunity data fresh when connectivity exists. Add the Notification Engine
so the learner is alerted to relevant new opportunities and approaching deadlines.

### Inputs needed before starting
- [ ] Phase 7 complete (Application Workspace working)
- [ ] Server-side opportunity API operational (basic GET /opportunities endpoint)
- [ ] Decision: what is the sync interval? (Daily recommended for opportunity freshness)

### Key files to create
- `src/sync/syncManager.ts` — orchestrates all sync operations
- `src/sync/opportunitySync.ts` — fetches latest opportunities from server, merges with local
- `src/engines/notificationEngine.ts` — generates local notifications from preferences + new data
- `src/pages/NotificationSettingsPage.tsx` — learner controls what they're notified about
- `src/components/SyncStatus.tsx` — "Last updated 2 hours ago" indicator

### Sync strategy
1. On app open: check if >24 hours since last sync; if so, attempt background sync
2. On user request: manual "Refresh" button always available
3. Conflict resolution: server data is authoritative for opportunity records;
   local data is authoritative for application records and profile
4. Offline: never block the app; show "data last synced [date]" indicator

### Notification rules
- New opportunity matches learner's saved preferences → notify
- Opportunity the learner saved closes in 7 days → urgent notify
- Opportunity the learner is preparing for closes in 48 hours → critical notify
- No unsolicited notifications; learner always controls notification categories

### Done condition
- App syncs opportunity data in background when online
- New opportunities appear after sync without page refresh
- Closing-soon notifications shown for saved/in-progress opportunities
- Learner can control all notification categories
- Sync status is always visible and honest about data freshness
- App works identically offline (cached data) and online (live data)

### POPIA/Security considerations
- Sync API must require authentication if learner accounts are introduced in Phase 10
- All sync traffic over HTTPS (TLS 1.2+)
- Server-side: log sync requests without user-identifying information (use anonymous session IDs)
- Notification content must not include PII in the notification payload

---

## Phase 9 — Opportunity Intelligence Engine

**Status: ⏳ Not started**

**Goal:** Build the AI-assisted matching layer that transforms the Capability Profile into
ranked, personalised opportunity recommendations. The step that separates Opportunity Hub
from a directory.

### Inputs needed before starting
- [ ] Phase 8 complete (Synchronisation Layer working)
- [ ] TPH Core SDK extraction complete (capability profile available as structured data)
- [ ] Decision: which Claude model for matching? (Default: `claude-sonnet-4-6` or latest)
- [ ] Learner consent flow designed and approved

### How the Intelligence Engine works

**Step 1: Local matching (no AI, no network)**
Tags on the learner's Capability Profile are matched against tags on opportunity records.
This works offline and requires no consent beyond profile creation.

```
Learner has: [math-thinking, data-analysis, entrepreneurship-basics]
Opportunity tags: [math, business, data]
Match score: high → surface this opportunity prominently
```

**Step 2: AI ranking (optional, requires connectivity + consent)**
When the learner opts in, the full Capability Profile + their interest signals are sent
to Claude. Claude returns:
- Ranked top 5–10 opportunities with explanations
- Reasoning in plain language ("Based on your Math Adventure journeys, you would be
  competitive for this data science learnership")
- Gaps to address ("This opportunity requires a Grade 12 certificate — you indicated
  Grade 10; here's what could help bridge that gap")

### Key files to create
- `src/engines/intelligenceEngine.ts` — orchestrates local matching + optional AI ranking
- `src/engines/localMatcher.ts` — tag-based local matching (no AI, no network)
- `src/services/aiMatchingService.ts` — sends to Claude API, handles response
- `src/components/RecommendationsPanel.tsx` — "Recommended for you" section on home screen
- `src/components/MatchExplanation.tsx` — "Here's why this matches your profile"
- `src/pages/ConsentPage.tsx` — explicit opt-in to AI matching (POPIA-compliant)

### Prompt design for AI ranking
The prompt must include:
- Capability Profile summary (what the learner has demonstrated)
- Top N opportunities from the discovery engine (pre-filtered by eligibility)
- Instruction: rank by relevance, explain why in plain SA-appropriate language
- Instruction: never say "you are not qualified" — always frame as "here is what would
  strengthen your application"

### Done condition
- Local matching works offline with zero AI calls
- AI ranking is opt-in only, with clear explanation before consent
- Recommendations shown on home screen with plain-language explanations
- Learner can turn off AI matching and revert to local matching at any time
- AI never recommends an opportunity the learner is clearly ineligible for (eligibility check first)

### POPIA/Security considerations
- **AI matching consent must be explicit, informed, and revocable**
- The Capability Profile sent to Claude must be anonymised (no name, ID, contact)
- Use Claude's privacy-preserving features; do not train on this data
- Do not log AI matching requests server-side in a way that links to learner identity
- Document: what data leaves the device, where it goes, how long it's retained

---

## Phase 10 — Production Hardening

**Status: ⏳ Not started**

**Goal:** Take Opportunity Hub from "works in testing" to "safe for real learners." Full
security review, POPIA compliance review, authentication (if accounts are introduced),
and deployment to production.

### Inputs needed before starting
- [ ] Phases 1–9 all complete and stable
- [ ] #FreeForever funding fork resolved (know how the backend is sustained)
- [ ] Decision: are learner accounts needed? (If yes: auth strategy, POPIA obligations increase)
- [ ] POPIA privacy notice drafted and reviewed by a qualified practitioner

### Security review (use `brain/SECURITY_CONSTITUTION.md`)
Complete all 22 domain reviews. Key domains for Opportunity Hub:
- **Data Security**: classify all data (profile, CV, application records, capability profile)
- **Child Safety**: learners may be under 18; POPIA child protection rules apply
- **Privacy**: complete POPIA Data Protection Impact Assessment (DPIA)
- **Trust Boundaries**: local device ↔ sync API ↔ AI service — each boundary reviewed
- **AI Security**: prompt injection, hallucination in recommendations, capability profile leakage
- **Deployment**: Railway security config, environment variables, TLS

### Authentication strategy (if accounts introduced)
If the funding fork is resolved and accounts are needed:
- OAuth via a trusted SA provider (or email/phone OTP)
- Session tokens must be short-lived (max 30 days)
- Household Mode must work with accounts (multiple profiles per account)
- Logout must clear all local sensitive data (CV, profile, application records)

### Key files to create
- `docs/popia-privacy-notice.md` — the learner-facing privacy notice
- `docs/dpia.md` — Data Protection Impact Assessment
- `docs/security-review-report.md` — completed Security Review Report (see SECURITY_CONSTITUTION.md)
- Deployment config files (Railway, Cloudflare) per `brain/playbooks/cloudflare-pages.md`

### Done condition
- Security Review Report completed with no Critical/High unmitigated risks
- POPIA compliance review signed off
- All 6 opportunity types have real, current, SA-specific opportunity data
- App deployed to production URL under iKhaya brand
- Smoke test: end-to-end journey (discover → eligibility → prepare → apply → track) confirmed
- Brain updated: `brain/SESSION_HANDOFF.md`, `brain/CURRENT_STATE.md`, `opportunity-hub.md` status

---

## Cross-Cutting Concerns (apply to every phase)

### Testing approach
There is no automated test suite. Validation is done by running the app and observing behaviour.
After any significant change: verify the offline scenario first (Chrome DevTools → Offline).

### Brain update rule
After every phase completion:
1. Update `brain/SESSION_HANDOFF.md` (prepend entry)
2. Update `brain/CURRENT_STATE.md` (edit in place)
3. Update this file's Phase Map (mark phase ✅ Complete with date)
4. If a significant architectural decision was made: append to `brain/decisions/DECISIONS.md`

### The "build order" rule
Do not skip phases. The offline-first foundation (Phase 4) must exist before the Discovery
Engine (Phase 5). The Discovery Engine must exist before the Eligibility Engine (Phase 6).
Each phase builds on the previous one. Shortcuts here create compounding architectural debt.

### The #FreeForever rule
The backend (API, AI matching) must not require learners to pay. If a sustainability model
is introduced, it must be directed at organisations (posting opportunities) or at Foundation
funding — never at learners.
