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

## The Sixteen Principles

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

### 13. Accessibility by Default

Every app is designed for every learner from the first line of code.
Accessibility is never retrofitted. Never treated as an edge case.

**What this means in practice:**
- Touch targets are ≥44×44px on every interactive element
- Colour contrast meets WCAG AA minimum (4.5:1 for text) in every screen
- Cognitive load is evaluated: can a 6-year-old complete this activity?
- Motor accessibility is evaluated: can someone with limited fine motor control use this?
- Low-end devices: every app must run on a 3-year-old Android mid-range phone
- Shared devices: Household Mode is the standard for all-ages and adult apps
- Screen readers: interactive elements have accessible labels
- No audio-only or visual-only content without an alternative

**Relationship to Voice First (Principle 7):** Voice First covers narration as the
primary interface for low-literacy users. Accessibility by Default covers the full
spectrum: motor, cognitive, visual, auditory, and device constraints.
Both principles are required. Neither replaces the other.

---

### 14. Modular Architecture

No monoliths. Every component must be separable, reusable, and composable.

**What this means in practice:**
- Any logic that appears in two or more apps belongs in TPH Core SDK
- Any pattern that appears in two or more contexts belongs in `brain/patterns/`
- No app should contain functionality that another app has to reimplement
- Components within an app have clear, single responsibilities
- Adding a new feature must not require modifying unrelated code
- The "touch one thing, break another" failure mode is a design defect

**Why this matters at scale:** With 10+ apps sharing a foundation, monolithic design
compounds. A bug in duplicated code must be fixed 10 times. A refactor must be
coordinated across 10 repos. Modular design makes each of those 1 fix, 1 refactor.

**The test:** can this component be extracted and used in a new app tomorrow without
rewriting it? If no — it is not yet modular enough.

---

### 15. Long-Term Maintainability

Every decision must survive 10 years without a dedicated maintenance team.

**What this means in practice:**
- Prefer readable over clever — code that reads like prose beats code that requires
  deciphering
- Prefer stable over fashionable — a framework that will exist in 5 years beats the
  one that is popular today
- Prefer documented over implicit — a comment explaining *why* is more valuable
  than one explaining *what*
- Prefer boring technology over cutting-edge for its own sake
- Prefer composable over monolithic (see Principle 14)
- Dependencies must be evaluated for long-term support, not just capability

**The measure:** can a new developer — or a future AI with no prior context — read
this code, understand it, and safely extend it within one working day?

**Why this matters for The People's Home specifically:** This project is a decade-long
mission. The apps built in 2026 should still be running and updateable in 2036. Code
that is clever today is a liability in 5 years.

---

### 16. Secure by Design

Security is never added after the fact. It is designed in from the first architectural
decision. Every component, every data flow, every dependency, and every feature is
evaluated for security impact before it is built.

**What this means in practice:**
- Security is the first question, not the last — ask "what can go wrong?" before "does it work?"
- Never retrofit security controls onto an existing design; design them into the foundation
- Every new dependency is evaluated for supply chain risk before it is added
- Child data receives the highest protection — POPIA child protection rules apply always
- Secrets never appear in source code, git history, client-side JavaScript, or AI conversations
- The trust model is documented before any cross-boundary data flow is implemented
- Every new World-B (iKhaya) feature is threat-modelled before being built
- The Security Constitution (`brain/SECURITY_CONSTITUTION.md`) is the reference
  for all security review work

**What this does not mean:** every feature requires a formal security audit before shipping.
It means that security is a continuous engineering habit, not a one-time gate.

**Why this is DNA and not just a principle:** Principle 4 (No Tracking) covers privacy outputs.
Principle 12 (Private by Default) covers configuration. Neither covers the engineering
discipline of designing security into every component from the start. Secure by Design
fills that gap.

**The test:** before building any component, can you answer: what is the trust boundary?
What data crosses it? What happens if the input is malicious? What happens if this is stolen?

---

### 17. Wire AI, Don't Activate It

AI is used to **build** The People's Home. It must never **run** it at the learner's expense.

**The distinction:**
- **AI as a build tool** (Claude Code, ChatGPT planning, AI-assisted scaffolding) → ✅ acceptable.
  This is the builder's cost, paid once per feature, not per learner.
- **AI as a runtime feature** (per-learner API calls in production) → ❌ wired, not activated.
  This cost scales with every user. At 10,000 learners it becomes a bill no one is paying.
  #FreeForever means learners never pay — which means the builder absorbs it all. That is not sustainable.

**What this means in practice:**
- Build the AI infrastructure: consent flows, proxy endpoints, intelligence engines, local fallbacks.
  All of it. Wire it properly. Make it ready.
- Do not set production API keys. Do not activate the AI tier. Leave it dormant until a
  sustainable model exists that does not require learners to pay.
- The **local/offline tier** (tag matching, on-device inference, deterministic algorithms) is
  the real #FreeForever product. AI is the upgrade path for when the economics allow.
- "Sustainable" means: a grant, NGO funding, organisational payments (organisations pay to *post*
  opportunities; learners never pay), or on-device models with zero API cost. Any of these unlocks
  the AI tier without taxing the people the platform serves.

**What triggers activation:**
An AI feature may be activated in production only when all three are true:
1. A funding model covers the per-call cost without charging learners
2. The feature gracefully degrades to the free local alternative if the funding ends
3. The decision is logged in `DECISIONS.md` with the funding model documented

**Why this is DNA:**
#FreeForever (Principle 1) is the founding promise. AI is the fastest way to accidentally break it —
not through malice, but through cost that accumulates invisibly. This principle is the safeguard.
The People's Home was built because the alternatives were gatekept. AI must never become our own gate.

---

### 18. The Welcome Moment (World-A first entrance)

*(Added 2026-07-04, founder-ratified during the Number Kingdom NK-1 review. Applies to every World-A app.)*

Every World-A application should give the child **one unforgettable first entrance** into its world:

- **Once, ever** — shown on first entry only, never repeated (persist a flag).
- **Emotionally warm** and **narrated** — a short spoken welcome into the named world.
- **Unlocks audio** — the single "begin" tap doubles as the browser's first user gesture, so it also
  unlocks speech (solves autoplay restrictions, onboarding, and emotional introduction in one interaction).
- **Remembered forever** — it becomes the child's memory of *arriving in the world*, not "opening an app".

The world is the experience; the entrance is its threshold. Examples across the ecosystem:
Early Literacy → *"Welcome to Reading Village"* · Early Numeracy → *"Welcome to Number Kingdom"* ·
Space Explorer → *"Welcome to Spaceport"* · Our World → *"Welcome Home"*.

**Why this is DNA:** it is the emotional counterpart to Principle 10 (Journey Before Apps) — the moment a
product stops feeling like software and becomes a *place*. Reference implementation:
`early-numeracy` `WelcomeMoment.tsx` (Number Kingdom NK-1). See also
[`patterns/world-a-navigation.md`](./patterns/world-a-navigation.md).

---

## How to use this file

### If you are an AI

Before proposing any feature, architecture, or change, check it against the fifteen principles.

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

## Security DNA reference

For the full security engineering framework that supports Principle 16, see:
[`brain/SECURITY_CONSTITUTION.md`](./SECURITY_CONSTITUTION.md)

The Security Constitution contains the 22 security review domains, threat modelling
questions, adversarial review approach, and the Security Review Report template.

---

## Evolution log

**2026-06-27 — v1.0:** Twelve principles extracted from:
- `brain/vision/01-product-rules.md` (rules 1–4 core)
- `brain/architecture/02-world-a-world-b-dna.md` (rules 1, 3, 12)
- Session knowledge from building all 10 World-A apps
- Founder guidance: "Capability Before Content", "Journey Before Apps",
  "Platform Before Duplication" identified as structural principles

**2026-06-27 — v1.1:** Three new principles added (13–15):
- Accessibility by Default — from the Universal AI Engineering Prompt
- Modular Architecture — from the Universal AI Engineering Prompt
- Long-Term Maintainability — from the Universal AI Engineering Prompt
- Source: `brain/AI_SYSTEM_PROMPT.md` (founder-authored operating charter)

**2026-06-27 — v1.2:** One new principle added (16):
- Secure by Design — from the Universal Security Engineering Constitution
- Security is a permanent architectural constraint, not a feature or a gate
- Source: `brain/SECURITY_CONSTITUTION.md` (founder-authored security charter)

**2026-06-28 — v1.3:** One new principle added (17):
- Wire AI, Don't Activate It — from a founding clarification session (2026-06-28)
- AI builds The People's Home; AI does not run it at the learner's expense
- Protects #FreeForever (Principle 1) from per-learner API cost at scale
- Companion decision: `DECISIONS.md` → D-12
