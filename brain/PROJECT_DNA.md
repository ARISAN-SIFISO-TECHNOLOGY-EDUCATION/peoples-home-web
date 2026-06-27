# Project DNA — The People's Home

> These are the principles that cannot be negotiated, watered down, or "temporarily"
> suspended. They are not aspirational goals — they are the definition of what
> The People's Home is. If a proposal violates one of them, the proposal is wrong,
> not the principle.
>
> **If you are an AI and a feature request or architectural decision contradicts
> something in this file — say so. Do not implement it. Ask the human to resolve
> the contradiction first.**
>
> **Authored:** 2026-06-27 · **Change protocol:** append only, never rewrite.
> New principles may be added. Existing ones may only be *clarified*, never weakened.

---

## The Twelve Principles

---

### 1. #FreeForever

World-A learning apps are free. Not freemium. Not "free with ads." Not "free tier with
upgrade path." Free. Forever.

**What this means in practice:**
- No payment wall, no IAP, no subscription inside any World-A app
- No "premium features" in World-A — the full app is always accessible
- The revenue question for iKhaya (World B) must be resolved without ever taxing
  the free layer

**The tension to hold:** iKhaya (World B) may charge for opportunity services.
That is permitted. The bridge between World A and World B must never become a toll.

---

### 2. Offline First

The core learning loop of every World-A app must work with zero internet connectivity.

**What this means in practice:**
- Assets are bundled or service-worker-cached
- No API calls in the critical path of any learning activity
- Test offline before every release (Chrome DevTools → Network → Offline)
- AI features degrade gracefully (skip if offline; never block learning)

**What this does not mean:** apps cannot ever use the internet. It means they must
*not require* it. Optional enhancements that use connectivity are fine if the app
works fully without them.

---

### 3. No Accounts

World-A apps require no login, no account, no email, no phone number.

**What this means in practice:**
- Open the app → start learning. Immediately.
- Progress lives in `localStorage` / IndexedDB on the device
- The People's Home Passport (downloadable JSON) is the opt-in portability mechanism,
  not a mandatory account system
- Never prompt "Sign up to save your progress" — progress is always saved locally

---

### 4. No Ads. No Tracking.

World-A apps contain no advertising and no third-party tracking.

**What this means in practice:**
- No Google Analytics, no Meta Pixel, no ad network SDKs
- No behavioural data sold or shared with third parties
- First-party usage data (if collected) stays in the app on the device
- The business model for the ecosystem must never depend on monetising learner attention

---

### 5. Ages Not Grades

Content ranges use ages, never school grades.

**What this means in practice:**
- Write: "Ages 8–10" · Never write: "Grade 4"
- Grades are national-curriculum-specific; ages are universal
- A child in Grade 4 in SA may be 9 or 11 — the age range captures both
- Linting rule: any "Grade N" string in content is a defect

---

### 6. South Africa First

The primary context for every app is South Africa — its people, languages, geography,
economy, culture, and challenges.

**What this means in practice:**
- Scenarios, names, places, currencies (R, not $) are South African
- isiZulu is the priority second language after English
- Stories, examples, and characters reflect SA lived reality
- Global expansion is possible in the future, but SA must always feel like home in this project

---

### 7. Voice First (where audience demands it)

Apps serving low-literacy users or young children must make narration the primary
interface, not an accessibility add-on.

**What this means in practice:**
- The app reads content aloud; the learner does not need to read to learn
- Everyday Foundations and Our World: voice-first by default
- New "all ages" or "adults" apps: consider voice-first before assuming reading literacy
- isiZulu narration must go through native-speaker review before shipping

---

### 8. One Home

The apps are not separate products. They are expressions of one ecosystem.

**What this means in practice:**
- Visual language, language, and tone are consistent across apps
- The People's Home Passport connects them — a learner's identity and stamps travel
- TPH Core SDK is the shared foundation — duplication of core features is a defect
- The website (peoples-home-web.pages.dev) is the visible centre of the home

**What this does not mean:** apps must look identical. Each pillar has its own personality.
One Home is about shared identity, not visual uniformity.

---

### 9. Capability Before Content

Apps are built to develop a *capability* in the learner, not to deliver curriculum.

**What this means in practice:**
- The question is not "what content should this app teach?" but
  "what capability should this learner leave with?"
- Capability: mathematical thinking / reasoning / financial literacy / coding fluency
- Content serves the capability. The capability defines the app's purpose.
- Apps are classified by capability pillar (the six pillars), not by subject or grade

---

### 10. Journey Before Apps

Learners need a pathway through the ecosystem, not a list of apps to install.

**What this means in practice:**
- "The People's Guide" (Kilimanjaro) is the front door — it matches people to journeys,
  not to download links
- Within apps, the Journey Progression pattern matters more than feature lists
- The People's Home Passport is the thread that connects app experiences into one journey
- The measure of success is not "10 apps installed" but "one person, one continuing journey"

---

### 11. Platform Before Duplication

When a pattern appears in two or more apps, it becomes platform.

**What this means in practice:**
- TPH Core SDK exists precisely to stop copying narration engines, progress tracking,
  Passport logic, and activity scaffolds across apps
- Every new app should consume TPH Core, not reinvent it
- Shared patterns are documented in `brain/patterns/` — check there before building
- The extraction of TPH Core from ReadAfrica into a standalone `@tph/core` package is
  the lead platform item for H2 2026

---

### 12. Private by Default

All repositories and products in this ecosystem are private. They are an internal solo system.

**What this means in practice:**
- Never make a repo public without explicit instruction from Sifiso
- Never publish an npm package publicly without explicit instruction
- Never expose an API without auth unless explicitly designed to be open
- The People's Home website and apps are publicly accessible; the source code is not

---

## How to use this file

### If you are an AI

Before proposing any feature, architecture, or change, check it against the twelve principles.

If a proposal conflicts with any principle:
1. Name the conflict explicitly
2. Do not implement the feature as proposed
3. Ask whether the principle should be reconsidered, or whether there is a way to achieve
   the goal without violating it

### If you are a human

Before accepting any proposal (from yourself, an AI, or a collaborator), ask:
> *"Does this violate the DNA?"*

If yes: either the proposal is wrong, or the DNA needs to be updated. Both are valid.
But never implement something that violates the DNA without making the contradiction explicit.

---

## Evolution log

**2026-06-27 — v1.0:** Twelve principles extracted from:
- `brain/vision/01-product-rules.md` (rules 1–4 core)
- `brain/architecture/02-world-a-world-b-dna.md` (rules 1, 3, 12)
- Session knowledge from building all 10 World-A apps
- Founder guidance: "Capability Before Content", "Journey Before Apps",
  "Platform Before Duplication" identified as structural principles
