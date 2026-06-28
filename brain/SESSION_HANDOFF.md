# Session Handoff

> **Purpose:** Every AI session that does meaningful work in this project should end
> by updating this file. This is the only reliable way to bridge sessions when context
> windows end.
>
> **Protocol:** Append a new entry at the TOP (newest first). Never delete old entries.
> Date every entry. Be specific — future-you has zero context.
>
> **If you are starting a session:** read the most recent entry below, then check
> `CURRENT_STATE.md`. That's enough to resume.

---

## ✅ 2026-06-28 (session 9) — iKhaya Phase 10 (Production Hardening)

**Done this session:**

- **Phase 10 — Production Hardening (commit `22f0da9`):**

  **Security headers (`public/_headers`):**
  - `X-Frame-Options: DENY` — clickjacking protection
  - `X-Content-Type-Options: nosniff` — MIME sniffing protection
  - `Referrer-Policy: strict-origin-when-cross-origin`
  - `Permissions-Policy: camera=(), microphone=(), geolocation=(), payment=()`
  - CSP: `default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'`
    (unsafe-inline in style-src is an accepted trade-off for React inline styles)
  - `/api/*` gets `Cache-Control: no-store` to prevent caching of sync/AI endpoints

  **Error handling:**
  - `src/components/ErrorBoundary.tsx` — class component wrapping the whole app AND the
    inner route tree. Shows a safe fallback UI; error detail only in DEV mode.
  - `src/pages/NotFoundPage.tsx` — 404 page for the wildcard `*` route.

  **Performance — lazy loading:**
  - All 7 pages (`DiscoverPage`, `OpportunityDetailPage`, `ApplicationWorkspacePage`,
    `ApplicationsPage`, `ProfilePage`, `ConsentPage`, `NotFoundPage`) wrapped in
    `React.lazy()` + `<Suspense fallback={<PageLoader />}>`.
  - Initial JS bundle: 318 kB → 265 kB (−16.7%). Pages load on demand.

  **Connectivity (`src/hooks/useOnlineStatus.ts`):**
  - `useOnlineStatus()` tracks `navigator.onLine` reactively via window events.
  - SyncStatus updated: shows 📴 offline state; refresh button disabled when offline.
  - App skips auto-sync when offline.

  **Service worker (`vite.config.ts`):**
  - `navigateFallback: '/index.html'` — SPA routing works offline.
  - `navigateFallbackDenylist: [/^\/api\//]` — API routes never served from SW cache.

  **POPIA rights (`src/pages/ProfilePage.tsx` + `src/storage/db.ts`):**
  - `exportAllData()` — collects profile, applications, saved opportunities, notification
    prefs, AI consent → JSON download as `ikhaya-my-data-YYYY-MM-DD.json`.
    Excludes opportunity records (public server data) and sync record (app metadata).
  - `clearAllData()` — clears all 5 user-specific IndexedDB stores. App still works after
    (opportunity records remain). Implements POPIA Section 24 right to erasure.
  - "📥 Download my data" + "🗑 Delete all my data" buttons added to Profile.

  **POPIA documentation:**
  - `docs/popia-privacy-notice.md` — plain-language notice covering what data, where stored,
    third parties (Anthropic, Cloudflare), children, all 5 POPIA rights.
  - `docs/dpia.md` — full Data Protection Impact Assessment. Data flow diagrams, 7 risks
    assessed. 2 residual risks accepted (shared device, under-18 consent gap).
  - `docs/security-review-report.md` — 22-domain security review. 0 Critical, 0 High,
    5 Medium risks (all accepted for MVP, documented with resolution targets).

  **Build result:** 49 modules, 265 kB initial JS (−16.7%), 16 precached assets, 0 TS errors.

**iKhaya Opportunity Hub — ALL 10 PHASES COMPLETE. 🎉**

```
Phase 1  ✅  Vision & Brain (locked in peoples-home brain)
Phase 2  ✅  Domain model (Opportunity, UserProfile, Application types)
Phase 3  ✅  UX & navigation (bottom nav, PWA shell, 4 pages)
Phase 4  ✅  Offline-first foundation (service worker, IndexedDB, seed data)
Phase 5  ✅  Opportunity discovery engine (search, filter, browse)
Phase 6  ✅  Eligibility engine (profile matching)
Phase 7  ✅  Application workspace (CV builder, motivation letter, document checklist)
Phase 8  ✅  Synchronisation layer + Notification Engine
Phase 9  ✅  Opportunity Intelligence Engine (local tag scoring + Claude AI ranking)
Phase 10 ✅  Production Hardening (security headers, error boundary, lazy loading, POPIA)
```

**Pre-public-launch items (from security-review-report.md):**
1. Set `ANTHROPIC_API_KEY` in Cloudflare Pages → activate AI ranking
2. Add Cloudflare rate limiting to `/api/ai-match` (max 10 req/IP/hour)
3. Run `npm audit` and fix any High/Critical findings
4. Encrypt IndexedDB using Web Crypto API
5. Write formal incident response plan (72h POPIA breach notification)
6. Implement parental consent flow for under-18 learners (if school-facing)

**🔴 URGENT — Keystore backup:** `upload-new.jks` is local-only. Unrecoverable if lost.

**Files changed (Phase 10):**
- `ikhaya/public/_headers` — security headers (new)
- `ikhaya/src/components/ErrorBoundary.tsx` — new
- `ikhaya/src/components/SyncStatus.tsx` — `isOnline` prop + offline state
- `ikhaya/src/hooks/useOnlineStatus.ts` — new
- `ikhaya/src/pages/NotFoundPage.tsx` — new
- `ikhaya/src/pages/ProfilePage.tsx` — data export + delete rights
- `ikhaya/src/storage/db.ts` — `exportAllData()` + `clearAllData()`
- `ikhaya/src/App.tsx` — full rewrite: lazy pages, double ErrorBoundary, useOnlineStatus
- `ikhaya/src/index.css` — focus rings, error boundary page styles
- `ikhaya/vite.config.ts` — navigateFallback + denylist
- `ikhaya/docs/popia-privacy-notice.md` — new
- `ikhaya/docs/dpia.md` — new
- `ikhaya/docs/security-review-report.md` — new

**Next steps:**
1. Set `ANTHROPIC_API_KEY` in Cloudflare → ikhaya → Settings → Environment variables
2. Wait for ChatGPT brief on next wave (Wave 12 planning)
3. Keystore backup 🔴
4. TPH Core SDK extraction from ReadAfrica → `@tph/core` (when directed)

---

## ✅ 2026-06-28 (session 8) — iKhaya Phase 9 (Opportunity Intelligence Engine)

**Done this session:**

- **Phase 9 — Opportunity Intelligence Engine (commit `79e4efa`):**

  **Two-tier matching architecture:**

  *Tier 1 — Local (offline, instant, no consent needed):*
  - `src/engines/localMatcher.ts` — pure scoring (0–100): interest type match (30 pts),
    capability tag overlap (40 pts), province availability (15 pts), basic eligibility (15 pts).
    Min score 20 to appear. Zero network calls. Works offline.
  - `src/engines/intelligenceEngine.ts` — orchestrator. `getLocalRecommendations()` = offline,
    instant. `getAIRecommendations()` = async, consent-gated, returns null on any failure
    (graceful fallback to local).

  *Tier 2 — AI-enhanced (Claude, opt-in, requires connectivity):*
  - `functions/api/ai-match.ts` — Cloudflare Pages Function at `POST /api/ai-match`.
    Server-side proxy to Claude Haiku (fast, cheap, structured JSON). Receives anonymised
    profile + ≤10 candidates; returns ranked JSON with match explanations and strengthen tips.
    Returns 503 if `ANTHROPIC_API_KEY` not configured. API key NEVER reaches the client.
  - `src/services/aiMatchingService.ts` — client calls `/api/ai-match`; returns null on any
    error (offline, 503, timeout, JSON parse).

  *POPIA-compliant consent:*
  - `src/pages/ConsentPage.tsx` — `/consent` route. Full disclosure of what data is sent
    (interests, capability tags, age, province, qualification — NO name/ID/contact).
    Explicit two-button opt-in. Consent stored in IndexedDB.
  - DB version 1→2: `aiConsent` store added with upgrade path for existing users.
  - `getAIConsent()` / `setAIConsent()` in `db.ts`.
  - AI is NEVER called without explicit consent. Revocable at any time in Profile.

  *UI:*
  - `src/components/RecommendationsPanel.tsx` — "✨ For You" section above search bar
    on DiscoverPage. Shows top 5 local recommendations. "🤖 AI rank" button triggers AI
    (navigates to /consent first if needed). Collapsible. AI results show AI badge. "↩ Local"
    to revert.
  - `src/components/MatchExplanation.tsx` — match badge (Strong/Good/Some + score), local
    reasons as chips, AI explanation text, strengthen tip.
  - `src/pages/DiscoverPage.tsx` — RecommendationsPanel injected above search when
    profile has interests/capability tags.
  - `src/pages/ProfilePage.tsx` — "AI Matching" toggle section to enable/revoke consent.
  - `src/App.tsx` — `/consent` route added; consent page hides bottom nav.
  - `src/index.css` — Phase 9 styles (~200 lines added).
  - `src/types/opportunity.ts` — MatchScore, AIMatchResult, AIConsentRecord interfaces.
  - Build: 46 modules, 318 kB JS, 20.6 kB CSS. 0 TypeScript errors.

**To activate AI ranking on Cloudflare Pages:**
Go to Pages → ikhaya → Settings → Environment variables → Production
Add: `ANTHROPIC_API_KEY = sk-ant-...`
Local matching works immediately with no configuration.

**State of ongoing work:**
- Phase 9 complete and deployed (commit `79e4efa` → Cloudflare Pages).
- Local matching works for anyone with interests set in Profile.
- AI ranking ready but dormant until `ANTHROPIC_API_KEY` is set in Cloudflare.

**Next steps (in order):**
1. **Set `ANTHROPIC_API_KEY` in Cloudflare Pages** to activate AI ranking
2. **Phase 10 — Production hardening** (POPIA review, security review, auth if needed)
   - Replace static `/api/opportunities.json` with a real backend endpoint
   - Service worker caching review (ensure API routes not inadvertently cached)
   - Full security review per `brain/SECURITY_CONSTITUTION.md`
3. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. Unrecoverable if lost.

**Files changed:**
- `ikhaya/functions/api/ai-match.ts` — new Cloudflare Pages Function
- `ikhaya/src/engines/localMatcher.ts` — new
- `ikhaya/src/engines/intelligenceEngine.ts` — new
- `ikhaya/src/services/aiMatchingService.ts` — new
- `ikhaya/src/components/RecommendationsPanel.tsx` — new
- `ikhaya/src/components/MatchExplanation.tsx` — new
- `ikhaya/src/pages/ConsentPage.tsx` — new
- `ikhaya/src/types/opportunity.ts` — MatchScore, AIMatchResult, AIConsentRecord added
- `ikhaya/src/storage/db.ts` — DB v2, aiConsent store, getAIConsent/setAIConsent
- `ikhaya/src/pages/DiscoverPage.tsx` — RecommendationsPanel injected
- `ikhaya/src/pages/ProfilePage.tsx` — AI Matching consent toggle added
- `ikhaya/src/App.tsx` — /consent route + isDetail update
- `ikhaya/src/index.css` — Phase 9 styles

---

## ✅ 2026-06-28 (session 7) — iKhaya Phase 8 (Synchronisation Layer + Notification Engine)

**Done this session:**

- **Phase 8 — Synchronisation Layer (commit `1ec4edb`):**
  - `public/api/opportunities.json` — static "API" payload (all 25 seed opportunities).
    Served by Cloudflare Pages at `/api/opportunities.json`. When Phase 10 adds a real
    backend, only `SYNC_URL` in `opportunitySync.ts` changes.
  - `src/sync/opportunitySync.ts` — `fetchRemoteOpportunities()` fetches the JSON with
    a 10s timeout, returns null on any network failure (never throws)
  - `src/sync/syncManager.ts` — `checkAndSync()` (24h gate, fires on app open) and
    `performSync()` (force, called on manual refresh). Merges remote data into IndexedDB.
    Server is authoritative for opportunity records; local is authoritative for applications.
    Updates SyncRecord (idle / syncing / error). Detects new opportunities since last sync.
  - `src/engines/notificationEngine.ts` — `getActiveNotifications()` generates in-app
    deadline alerts from local data only. Critical (<48h), urgent (<N days from prefs, default 7).
    Filters by notification type preferences. No PII leaves the device. Push notifications
    deferred to Phase 10 (requires backend auth).
  - `src/components/SyncStatus.tsx` — replaces old static SyncBanner. Shows relative
    "last updated" time ("just now", "3h ago", "yesterday"), spinning ⟳ while syncing,
    manual 🔄 refresh button, "+N new" badge when new opportunities arrive
  - `src/components/NotificationBanner.tsx` — dismissible deadline alert stack
    (critical = red left-border, urgent = amber). Only shown on list/discover screens,
    hidden inside detail/workspace views.
  - `src/App.tsx` — wired: seed → stamp SyncRecord → load notifications →
    background checkAndSync on mount; manual refresh via handleRefresh(); urgent
    notification badge (red dot) on My Applications nav tab
  - `src/pages/ProfilePage.tsx` — new "🔔 Alert Preferences" section: toggle for
    new-opportunity alerts, range slider for closing-soon window (1–30 days),
    per-type chip filter
  - `src/storage/db.ts` — added `getNotificationPrefs()` and `saveNotificationPrefs()`
    (uses existing `notificationPrefs` store; no DB version bump needed)
  - `src/index.css` — Phase 8 styles: `.sync-banner-left`, `.sync-spinner`,
    `.sync-new-badge`, `.sync-refresh-btn`, `.notification-panel`, `.notification-item`
    (critical/urgent/info variants), `.notification-dismiss`, `.nav-badge`,
    `.notif-pref-section`, `.notif-toggle-row`
  - Build: 40 modules, 307 kB JS, 16.8 kB CSS. 0 TypeScript errors.

**State of ongoing work:**
- Phase 8 complete and deployed to ikhaya.pages.dev (commit `1ec4edb` → Cloudflare Pages).
- Sync works offline (falls back to local data; shows error state in status bar).
- Notifications are in-app only (no push); alerts reset on new session (dismissed via sessionStorage).

**Next steps (in order):**
1. **Phase 9 — Opportunity Intelligence Engine** (AI matching, Capability Profile integration)
   Requires: TPH Core SDK extraction from ReadAfrica → `@tph/core`; Claude API access from client
2. **Phase 10 — Production hardening** (POPIA review, security audit, auth if needed)
3. **Real backend** — Railway or Cloudflare Workers endpoint to replace static JSON "API".
   When built, only `SYNC_URL` in `src/sync/opportunitySync.ts` needs to change.
4. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. Unrecoverable if lost.

**Files changed:**
- `ikhaya/public/api/opportunities.json` — new static API payload
- `ikhaya/src/sync/opportunitySync.ts` — new
- `ikhaya/src/sync/syncManager.ts` — new
- `ikhaya/src/engines/notificationEngine.ts` — new
- `ikhaya/src/components/SyncStatus.tsx` — new (replaces inline SyncBanner)
- `ikhaya/src/components/NotificationBanner.tsx` — new
- `ikhaya/src/App.tsx` — wired sync + notifications; new imports
- `ikhaya/src/pages/ProfilePage.tsx` — added Alert Preferences section
- `ikhaya/src/storage/db.ts` — getNotificationPrefs / saveNotificationPrefs added
- `ikhaya/src/index.css` — Phase 8 styles (~100 lines added)

---

## ✅ 2026-06-28 (session 6) — iKhaya Phase 7 (Application Workspace) + deploy fix

**Done this session:**
- **Blank page fix (deploy):** Cloudflare Pages was serving the raw source `index.html`
  (with `<script src="/src/main.tsx">`) because `NODE_ENV=production` caused npm to skip
  devDependencies — so `vite`, `typescript`, `@vitejs/plugin-react` were never installed
  and the build silently failed. Fix: moved all build tools to `dependencies`; simplified
  build script to `vite build`; added `wrangler.toml` locking `pages_build_output_dir = dist`.
  Commit `024a2f6`.

- **Phase 7 — Application Workspace (commit `1fffea9`):**
  - `src/engines/applicationEngine.ts` — creates/updates ApplicationRecord locally;
    `startApplication`, `updateStage`, `saveNotes`, `saveCVData`, `saveMotivation`,
    `toggleDocument`, `addDocument`; text-export formatters for CV and motivation letter
  - `src/pages/ApplicationWorkspacePage.tsx` — 4-tab workspace: Overview (notes, status
    summary, history, apply button), CV, Letter, Documents; stage progress bar
    (Interested → Preparing → Applied → In Progress → Accepted) + outcome buttons
    (Declined / Withdrawn); debounced 600ms saves; clipboard copy for CV and letter
  - `src/components/CVBuilder.tsx` — SA CV form: Personal info, Education, Experience
    (incl. volunteer flag), Skills (chip input), Languages (chip input), References
  - `src/components/MotivationHelper.tsx` — 4-section guided letter with prompts and
    word count; auto-saves on change
  - `src/components/DocumentChecklist.tsx` — tick-off checklist with required/optional
    badges, progress counter, custom document add
  - `src/components/DeadlineTracker.tsx` — days-remaining badge (green/amber/red/rolling)
  - `src/types/opportunity.ts` — CVData, CVEducation, CVExperience, CVReference,
    MotivationDraft interfaces added
  - `src/pages/OpportunityDetailPage.tsx` — "Start / Continue Application Workspace"
    primary button; loads existing application state on mount
  - `src/pages/ApplicationsPage.tsx` — tapping card navigates to workspace
  - `src/App.tsx` — `/application/:opportunityId` route; workspace hides bottom nav
  - `src/index.css` — full Phase 7 styles (~200 lines)
  - Build: 35 modules, 300 kB JS, 14 kB CSS. 0 TypeScript errors.

**State of ongoing work:**
- Cloudflare Pages should now be deploying the correct built version. Verify at ikhaya.pages.dev.
- Phase 7 complete and deployed.

**Next steps (in order):**
1. Phase 8 — Synchronisation layer (live opportunity data, notification engine)
   Requires: server-side opportunity API endpoint (no backend exists yet)
2. Phase 9 — Opportunity Intelligence Engine (AI matching with Capability Profile)
3. Phase 10 — Production hardening (POPIA, security review, auth)
4. Keystore backup (URGENT 🔴) — `upload-new.jks` local-only. Unrecoverable if lost.

**Files changed:**
- `ikhaya/src/engines/applicationEngine.ts` — new
- `ikhaya/src/pages/ApplicationWorkspacePage.tsx` — new
- `ikhaya/src/components/CVBuilder.tsx` — new
- `ikhaya/src/components/MotivationHelper.tsx` — new
- `ikhaya/src/components/DocumentChecklist.tsx` — new
- `ikhaya/src/components/DeadlineTracker.tsx` — new
- `ikhaya/src/types/opportunity.ts` — CVData + MotivationDraft interfaces added
- `ikhaya/src/App.tsx` — new route + nav hide
- `ikhaya/src/pages/OpportunityDetailPage.tsx` — workspace entry button
- `ikhaya/src/pages/ApplicationsPage.tsx` — navigate to workspace
- `ikhaya/src/index.css` — Phase 7 styles
- `ikhaya/package.json` — build tools moved to dependencies
- `ikhaya/wrangler.toml` — new, locks Cloudflare output dir

---

## ✅ 2026-06-28 (session 5) — iKhaya wired into The People's Home website + Kilimanjaro bot

**Done this session:**
- **`peoples-home/index.html`** — Opportunity Hub placeholder `<span>` converted to a live link:
  `<a class="app live" href="https://ikhaya.pages.dev/" target="_blank" rel="noopener">Opportunity Hub ↗</a>`
  iKhaya is now discoverable from the People's Home website. Commit `08b0f09`.
- **`kilimanjaro/src/knowledge/platform.ts`** — Added `IKHAYA` WorldBEntry constant and updated
  `formatPlatformContext()`. The bot now knows iKhaya is ✅ LIVE (was "coming 2027"), knows all
  6 opportunity types, highlights 25 SA opportunities, and can direct learners to `ikhaya.pages.dev`
  when they ask about bursaries, jobs, grants, learnerships, freelancing, or community opportunities.
  Commit `91debf6`.

**State of ongoing work:**
- iKhaya Opportunity Hub Phase 7 (Application workspace) is the next build phase — not started.

**Next steps (in order):**
1. Phase 7 — Application workspace (CV builder, motivation helper, document checklist, deadline tracker)
2. Phase 8 — Synchronisation layer (live opportunity data, notification engine)
3. Phase 9 — Opportunity Intelligence Engine (AI matching with Capability Profile)
4. Phase 10 — Production hardening (POPIA, security review, auth)
5. Keystore backup (URGENT 🔴) — `upload-new.jks` local-only. Unrecoverable if lost.

**Files changed:**
- `peoples-home/index.html` — Opportunity Hub is now a live link (commit `08b0f09`)
- `kilimanjaro/src/knowledge/platform.ts` — iKhaya added as live World-B entry (commit `91debf6`)

---

## ✅ 2026-06-28 (session 4) — iKhaya Opportunity Hub Phase 4+5 built and pushed

**Done this session:**
- **GitHub repo created:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/ikhaya` (PRIVATE)
- **Local path:** `C:\Users\sifis\Next-Level-Projects\ikhaya`
- **Stack:** Vite + React 19 + TypeScript + vite-plugin-pwa + idb + react-router-dom
- **Commit:** `305414c` — 25 files, 8,697 insertions
- **Phases done:** Phase 2 (domain model as TS types) + Phase 4 (offline PWA foundation) + Phase 5 (discovery engine) + Phase 6 MVP (eligibility engine)

**What was built:**
- `src/types/opportunity.ts` — full domain model: 6 opportunity types, 9 provinces, 9 qualification levels, all entities
- `src/data/seed-opportunities.ts` — 25 real SA opportunities (NSFAS, YES, NYDA, WeThinkCode_, GADS, Upwork, Harambee, etc.)
- `src/storage/db.ts` — IndexedDB layer (idb), namespace: `tph_oh_db`
- `src/engines/discoveryEngine.ts` — full-text search, 8 filter types, sorted results
- `src/engines/eligibilityEngine.ts` — age/province/qualification/citizenship checks, ✓/⚠/✗/— verdicts
- `src/pages/DiscoverPage.tsx` — search bar, type chips, filter chips, opportunity cards with eligibility
- `src/pages/OpportunityDetailPage.tsx` — full detail, eligibility breakdown, Apply Now CTA
- `src/pages/ApplicationsPage.tsx` — application tracking (empty state — Phase 7 needed)
- `src/pages/ProfilePage.tsx` — local profile: age, province, qualification, citizenship, interests
- PWA: service worker, workbox precache, manifest, `_redirects` for SPA routing
- Build: ✓ 275 kB JS, 6 kB CSS, no errors

**Cloudflare Pages deploy — ✅ LIVE:**
- URL: **https://ikhaya.pages.dev/**
- Auto-deploys from `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/ikhaya` main branch

**Next steps (in order):**
1. ⏳ **Connect Cloudflare Pages** (manual — see above)
2. Phase 7 — Application workspace (CV builder, motivation helper, checklist)
3. Phase 8 — Sync layer (fetch live opportunities, notification engine)
4. Phase 9 — Opportunity Intelligence Engine (AI matching)

**Files changed (this session):**
- `C:\Users\sifis\Next-Level-Projects\ikhaya\` — new repo, 25 files

---

## ✅ 2026-06-27 (session 3) — Opportunity Hub defined and locked in Brain

**Done this session:**
- **`brain/platform/opportunity-hub.md`** (NEW) — Full permanent definition of Opportunity Hub:
  purpose, mission, vision, the 5-step philosophy chain, the single sentence definition,
  position in the iKhaya ecosystem, all 6 opportunity types with examples, all 7 engines
  with full specs, relationship to World A / TPH Core / iKhaya, 3 architectural tensions,
  8 guiding principles, 5 success metrics, current status, link to build playbook.
- **`brain/playbooks/build-opportunity-hub.md`** (NEW) — 10-phase implementation blueprint:
  Phase 1 (done) through Phase 10 (production hardening). Each phase has goal, inputs needed,
  key decisions, key files, done condition, and POPIA/security considerations.
- **`brain/platform/ikhaya.md`** (UPDATED) — Platform module map appended. iKhaya's full
  module set documented: OH, Learning Hub, Skills Passport, Funding Hub, Career Hub,
  Entrepreneurship Hub, Community Hub. Cross-reference to opportunity-hub.md added.
- **`brain/PROJECT_GLOSSARY.md`** (UPDATED) — 7 new entries added: Opportunity Hub,
  iKhaya Platform Modules, Opportunity Intelligence Engine, Eligibility Engine,
  Discovery Engine, Application Engine, Capability Profile, #FreeForever Funding Fork.

**Architecture locked:**
- iKhaya = platform brand. Opportunity Hub = flagship module. This distinction is now
  in the brain and must never collapse.
- Capability chain: Capability → Confidence → Readiness → Opportunity → Real-World Outcomes
- 6 opportunity types: Education, Employment, Entrepreneurship, Funding, Community, Global & Digital
- 7 engines: Opportunity, Eligibility, Discovery, Application, Progress, Notification, Intelligence

**Next steps (in order):**
1. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. Back up now.
2. **Wave 12 planning** — wait for ChatGPT brief before starting.
3. **TPH Core SDK extraction** — extract from ReadAfrica into `@tph/core`.
4. **Opportunity Hub Phase 2** — domain model. Begin only when directed.
   Start with: tech stack decision, opportunity data source, entity ownership.

**Files changed:**
- `brain/platform/opportunity-hub.md` — new: full definition
- `brain/playbooks/build-opportunity-hub.md` — new: 10-phase build blueprint
- `brain/platform/ikhaya.md` — updated: platform module map + cross-reference
- `brain/PROJECT_GLOSSARY.md` — updated: 7 new entries

---

## Entry format

```markdown
## [YYYY-MM-DD] — Short description of what happened

**Done this session:**
- Bullet points of what was actually completed and committed

**State of ongoing work:**
- What is mid-flight (started but not finished)
- Exactly where to pick up

**Next steps (in order):**
1. The very next action needed
2. The action after that
...

**Unresolved issues / risks:**
- Anything that needs attention but wasn't resolved

**Files changed (key ones):**
- `path/to/file.ts` — what changed
```

---

## 2026-06-27 (session 2) — Security Constitution + DNA extended to 16 principles

**Done this session:**
- **`brain/SECURITY_CONSTITUTION.md` (NEW):** Full Universal Security Engineering Constitution stored permanently. Covers: security roles + mission, 12 security principles, security mindset assumptions, all 22 review domains (Data, Child Safety, Privacy, Trust Boundaries, Identity & Auth, Authorization, Platform, AI Security, Brain Security, Knowledge Governance, Secrets, Supply Chain, Input Validation, Cryptography, APIs, Databases, File Handling, Business Logic, Availability, Secure Defaults, Deployment, Compliance), 10 threat modelling questions, adversarial review (6 attacker personas), security governance rules, Security Review Report template (Security/Privacy/Resilience/Child Safety/Supply Chain/Production Ready scores /10), Final Principle.
- **`brain/PROJECT_DNA.md` (v1.2):** Principle 16 added — Secure by Design. "Security is not a feature. Security is a permanent architectural constraint." Header updated (Fifteen → Sixteen). Cross-reference to SECURITY_CONSTITUTION.md added. Evolution log appended.
- **`brain/AI_ONBOARDING.md`:** Phase 4 extended with item 19 (SECURITY_CONSTITUTION.md). Security section updated to point to Constitution for security-focused sessions.
- **`brain/README.md`:** Core navigation table updated with SECURITY_CONSTITUTION.md entry. DNA entry corrected to "sixteen principles."
- **`brain/AI_SYSTEM_PROMPT.md`:** Security Review Framework section updated — cross-reference to SECURITY_CONSTITUTION.md added (quick-check list + pointer to full 22-domain reference).
- **Commit:** `3be6bff` — 695 insertions, 5 files. Pushed to `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/peoples-home-web` main.

**State of ongoing work:**
- Security Constitution is complete. Brain now has a three-layer security model:
  - `PROJECT_DNA.md` principle 16 — what cannot be broken
  - `SECURITY_CONSTITUTION.md` — how to operate as security engineering partner
  - `AI_SYSTEM_PROMPT.md` — quick-check list + pointer to Constitution
- All planned brain documents are now complete for this sprint.

**Next steps (in order):**
1. **Keystore backup (URGENT 🔴)** — `upload-new.jks` is local-only. If lost, Math Adventure Google Play account is unrecoverable. Back up now.
2. **TPH Core SDK extraction** — extract shared code from ReadAfrica into `@tph/core` standalone package. This is the lead platform item for H2 2026.
3. **Wave 12 planning** — wait for ChatGPT brief before starting. Do not plan ahead of the brief.
4. **Engine playbooks** — `new-wave.md`, `debug-batch.md` in engine-1000 `docs/playbooks/`.
5. **Engine `PROJECT_GLOSSARY.md`** — follow the same pattern as `brain/PROJECT_GLOSSARY.md`.
6. **Deepening passes** — more Journeys, more areas in the live apps.
7. **isiZulu native-speaker review** — ~December 2026.
8. **iKhaya one-suburb beta** — 2026 H2.

**Unresolved issues / risks:**
- Keystore backup: `upload-new.jks` at local path only. HIGH risk of permanent loss. Action required immediately.

**Files changed (key ones):**
- `brain/SECURITY_CONSTITUTION.md` — new: full 22-domain security operating charter
- `brain/PROJECT_DNA.md` — extended: principle 16 (Secure by Design), v1.2
- `brain/AI_ONBOARDING.md` — updated: item 19 added to Phase 4 reading path
- `brain/README.md` — updated: SECURITY_CONSTITUTION indexed in Core navigation
- `brain/AI_SYSTEM_PROMPT.md` — updated: cross-reference to SECURITY_CONSTITUTION

---

## 2026-06-27 — The People's Home Brain built + Kilimanjaro Phases 5–7

**Done this session:**
- **Phase 5 (Platform Knowledge):** Added `src/knowledge/platform.ts` to Kilimanjaro with all 10 live World-A apps, correct URLs, descriptions, and age ranges. Added admin gating (`ADMIN_PHONE_NUMBER` env var).
- **Phase 6 (RAG / live search):** Added `src/knowledge/fetcher.ts` (daily Cloudflare Pages snapshot) and `src/knowledge/search.ts` (keyword-overlap search). Bot can now answer questions from live website content.
- **Phase 7 (Interactive messages):** Added WhatsApp button and list-picker support to the bot. New types in `src/whatsapp/types.ts` and `src/whatsapp/client.ts`. Brain now returns `BotResponse` union (`text | buttons | list`). `receive.ts` routes interactive replies. Welcome message is buttons. App menu is a list picker with all 10 apps in 2 sections.
- **Railway fix:** Moved `@types/express`, `@types/node`, `@types/node-cron`, `typescript`, `prisma` from devDependencies to dependencies (Nixpacks uses `NODE_ENV=production` → skips devDependencies at build time).
- **Knowledge correction:** Discovered all 10 World-A apps are live (bot previously thought only 1–2 were). Complete rewrite of `platform.ts` with accurate URLs and states.
- **Math Adventure Play link fixed:** Correct package ID is `com.sifiso.mathadventurerpg` (was incorrectly `com.ikhaYaai.mathadventurerpg`).
- **THE PEOPLE'S HOME BRAIN:** Built this entire `brain/` directory structure — migrated `docs/memory/` content, restructured canon into `vision/` and `architecture/`, wrote AI_ONBOARDING.md, SESSION_HANDOFF.md, PROJECT_GLOSSARY.md, patterns/, history/, decisions/ subdirectories.
- **Engine-1000 integration (A, B, C):** Created `docs/peoples-home/` in engine-1000 repo with cross-reference docs, TPH tracking, and roadmap mirror.

**State of ongoing work:**
- All Kilimanjaro phases 5–7 are deployed and verified working on Railway.
- Brain construction is complete as of this commit.
- Engine-1000 integration files created.
- Bot persona is "The People's Guide."

**Next steps (in order):**

1. **Add ADMIN_PHONE_NUMBER in Railway Variables**
   - Go to Railway → kilimanjaro project → Variables
   - Add: `ADMIN_PHONE_NUMBER=<your number in E.164 without +, e.g. 27821234567>`
   - This gates personal tools (notes, reminders, invoices) to admin only

2. **Brain deepening passes** — review existing app memory files for accuracy
   - `brain/apps/*.md` — some may predate the final shipped state
   - `brain/platform/tph-core.md` — update with `@tph/core` extraction status

3. **TPH Core SDK extraction** — pull TPH Core out of ReadAfrica into a shared `@tph/core`
   package; this is now the lead platform item

4. **isiZulu review** — deferred to ~December 2026 per ROADMAP

5. **Keystore backup** — the signing `.jks` files are local-only; back them up off-machine
   (high priority security risk — data loss = unrecoverable)

6. **iKhaya one-suburb beta** — background track for 2026 H2

**Unresolved issues / risks:**
- **Keystore backup outstanding** — if the local machine is lost, Math Adventure and
  Science Sprouts cannot be updated on Google Play. Back up `upload-new.jks` immediately.
- **Science Sprouts Play rollout** — in progress (rolling out to Google Play);
  the web PWA is fully live but Play may still be in review stages.
- **iKhaya #FreeForever funding fork** — must be resolved before 2027 launch.
  World A is free; iKhaya needs a revenue model that doesn't compromise the mission.
  This decision is deferred but must be made before iKhaya goes to production.

**Files changed (key ones, this session):**
- `kilimanjaro/src/knowledge/platform.ts` — complete rewrite, all 10 apps
- `kilimanjaro/src/knowledge/fetcher.ts` — snapshot cron
- `kilimanjaro/src/knowledge/search.ts` — keyword search
- `kilimanjaro/src/whatsapp/client.ts` — button + list message types
- `kilimanjaro/src/whatsapp/types.ts` — interactive webhook types
- `kilimanjaro/src/agent/brain.ts` — "The People's Guide" persona, interactive responses
- `kilimanjaro/src/webhook/receive.ts` — interactive reply routing
- `kilimanjaro/package.json` — moved types/build deps to dependencies
- `peoples-home/brain/` — entire directory (new)
- `repository-engine-1000/docs/peoples-home/` — new (engine integration)

---

*(Older entries will appear below as sessions accumulate.)*
