# Project Glossary

> Definitions for every key term, name, and concept used in The People's Home ecosystem.
> When you encounter an unfamiliar word in this project, look here first.
>
> **Maintained:** append new terms as they are introduced. Never redefine — only expand.

---

## Organisations and entities

**ARISAN SIFISO Holdings**
The parent company. An umbrella for all initiatives by Sifiso Cyprian Shezi.
iKhaya AI is the AI/technology/education arm of Holdings.

**iKhaya AI**
The builder entity — the AI-focused technology and education company inside ARISAN SIFISO
Holdings. All TPH apps are built by iKhaya AI. The name "iKhaya" means "home" in isiZulu.

**The People's Home Foundation NPC**
A registered non-profit company (NPC) in South Africa. Holds the public-benefit mandate
for The People's Home. Distinct from iKhaya AI (which is a for-profit commercial entity).
The separation allows sustainability (commercial revenue from World B) without compromising
the mission (free-forever learning apps).

**The People's Home (TPH)**
The product ecosystem. Ten offline learning apps + iKhaya platform + shared infrastructure.
The umbrella brand that learners, parents, and the public interact with.

---

## Core architectural concepts

**World A**
All offline learning apps — the free-forever, no-server, no-login layer.
DNA: offline-first, free, open access, no revenue from learners.
Ten apps live as of 2026-06-27. Will grow slowly as existing apps deepen.

**World B**
iKhaya — the server-backed opportunity platform.
DNA: accounts required, server, potential revenue model, opportunity infrastructure.
Launching 2027. Still prototype (~4/10) as of 2026-06-27.

**The bridge**
The People's Home Passport — the mechanism that carries learner identity and progress
from World A (offline, no login) into World B (iKhaya, accounts, opportunity).
Implemented as a downloadable JSON file. First real consumer: Our World and Math Adventure.

**The six pillars**
The capability architecture: Foundations, Curiosity & Knowledge, Creation & Technology,
Thinking & Reasoning, Real-World Empowerment, Money & Opportunity.
Each pillar has ≥1 World-A app covering it. See
[`architecture/01-capability-architecture.md`](./architecture/01-capability-architecture.md).

**Capability → Implementation → DNA**
The three-level classification of every product in the system.
- Capability: what it builds (e.g., "mathematical thinking")
- Implementation: how it's built (e.g., "offline PWA, game-loop, ages-not-grades")
- DNA: World A vs World B (determines deployment model and business rules)

---

## Product and platform terms

**Opportunity Hub**
iKhaya's flagship module and discovery/matching engine. Transforms demonstrated capability
into discoverable real-world opportunity across 6 types: Education, Employment,
Entrepreneurship, Funding, Community, and Global & Digital Opportunities. Contains 7 engines.
The "transition layer" of The People's Home — it does not teach (World A does that);
it connects capable people to real-world pathways. Not a job board.
Full definition: `brain/platform/opportunity-hub.md`.

**iKhaya Platform Modules**
The full set of products that live inside iKhaya (World B):
Opportunity Hub (flagship, first to be built), Learning Hub, Skills Passport, Funding Hub,
Career Hub, Entrepreneurship Hub, Community Hub, and future modules.
iKhaya is the platform brand; these are its products. Never conflate one module with the platform.

**Opportunity Intelligence Engine**
The 7th engine in Opportunity Hub. Consumes the Capability Profile from TPH Core SDK
(with explicit learner consent) and surfaces ranked, AI-assisted opportunity recommendations.
Two layers: local tag-matching (offline, no consent needed) + Claude-powered ranking
(online, opt-in only). Separates Opportunity Hub from a directory.

**Eligibility Engine**
Engine 2 in Opportunity Hub. Answers "Can I apply?" by matching opportunity requirements
(age, province, qualification level, citizenship) against the learner's local profile.
Shows ✓ / ⚠ / ✗ indicators without making the learner read wall-of-text requirements.

**Discovery Engine**
Engine 3 in Opportunity Hub. Powers search, filter, and browse across all 6 opportunity types.
Works offline using locally cached opportunity data. Debounced search, multi-filter support.

**Application Engine**
Engine 4 in Opportunity Hub. Helps learners prepare and track applications: CV builder,
motivation letter helper, document checklist, deadline tracker, application history.
Addresses the core problem: most SA learners have never written a formal application.

**Capability Profile**
A TPH Core SDK construct. The structured summary of what a learner has demonstrated across
World-A apps: completed journeys, earned stamps, capability tags. Consumed by the Opportunity
Intelligence Engine (with explicit consent) to personalise opportunity recommendations.
Stored locally on the device; never shared without learner consent.

**#FreeForever Funding Fork**
The unresolved sustainability question for iKhaya/World B: the backend infrastructure
(server, database, AI calls) has real running costs, but learners must never pay.
Candidate resolutions: Foundation grants, Microsoft-for-Startups Azure credits, organisation-side
listing fees (free to apply; paid to post featured opportunities). Must be resolved before
the 2027 iKhaya flagship launch.

**TPH Core SDK**
The shared code library embedded across World-A apps: narration engine, progress tracking,
People's Home Passport, shared activity types. Currently embedded in ReadAfrica; extraction
into a standalone `@tph/core` package is the lead platform item as of mid-2026.

**People's Home Passport**
A learner's cross-app identity — a downloadable JSON file that moves progress between apps
without a server or login. Exported from one app, imported into another (or into iKhaya).
Inspired by a physical passport: stamps are earned, never lost, first-person voice.

**The house deploy pattern**
Every World-A app: Cloudflare Pages + offline PWA + card on peoples-home-web.pages.dev.
No Google Play (except Math Adventure + Science Sprouts, which were already granted access).
This is the standard after the web-first pivot on 2026-06-12.

**#FreeForever**
The non-negotiable product rule: World-A apps are always free. Not freemium. Not "free tier."
Fully free. The funding fork: how iKhaya (World B) generates revenue without touching World A.

**Ages-not-grades**
The non-negotiable content rule: content ranges use ages ("Ages 8–10"), never school grades
("Grade 4"). Grades are national-curriculum-specific and exclude many learners.

**Offline-first**
The core architectural discipline: the learning loop of every World-A app must work with
zero network connectivity. Assets are bundled or cached via service worker. No API calls
in the critical path.

**SA-first**
South Africa is the primary context. All scenarios, names, currencies (R, not $), geography,
and cultural references are South African by default. isiZulu is the priority language
after English.

---

## App-specific terms

**Atelier chassis**
The engine originally shared between Truth Seekers and Micro Founders. Micro Founders
started on the Atelier scaffold; Truth Seekers later purged it (Phase 2) to become
fully reasoning-native. Atelier = the shared "studio" activity framework.

**Journey-progression model**
The design pattern where a learner moves through named, sequential stages of a single
through-line. Used in: Micro Founders (5-stage Venture Journey), Mzansi Money
(5-stage Money Journey), SIFISO — The Golden Hand (5 journeys), Our World (6 Journeys).
Not the same as a "course with chapters" — the learner has ONE persistent thing
(a venture, a money plan, a passport) that grows across all stages.

**My Venture**
The through-line in Micro Founders: one business idea the learner develops across all
5 stages (Spot it → Cost it → Sell it → Build it → Pitch it).

**My Money Plan**
The through-line in Mzansi Money: one personal financial plan built across all
5 stages (Earn → Budget → Save → Borrow → Protect & Grow).

**My Passport** (Our World)
A stamp book in Our World — first-person, never percentages, one stamp per discovery.
Inspired by a physical travel passport. Related to but distinct from the People's Home
Passport (the cross-app JSON file).

**Household Mode**
A feature in Everyday Foundations and Our World: multiple learners can use one device
without each needing their own account. Profiles switch by name/icon.

**Voice-first**
Apps designed to read content aloud to the learner. Implemented in Everyday Foundations
(adult literacy on-ramp) and Our World. Critical for low-literacy users. Not the same
as voice input — it's TTS/narration-first.

**Pyodide**
The WebAssembly build of Python that runs in-browser. Used in SIFISO — The Golden Hand
to run Python code 100% offline without a server. Learners execute real Python without
any internet connection.

**Science Academy**
The teen tier (ages 13–17) within Science Sprouts, added on 2026-06-25 when the
age-ceiling-17 rule required every Curiosity app to reach age 17.

---

## Infrastructure and deployment

**Kilimanjaro**
The WhatsApp AI agent for The People's Home. Built in TypeScript, deployed on Railway.
Identity: "The People's Guide." Handles community navigation (all users) + personal
tools (admin only). Named after the mountain — the highest peak, the guide.

**The People's Guide**
The bot persona inside Kilimanjaro. A warm, community-first assistant that helps anyone
find the right app or pathway in The People's Home.

**Admin gating**
The Kilimanjaro pattern: personal tools (notes, reminders, invoices) are only available
to the phone number in `ADMIN_PHONE_NUMBER` env var. All other users get the community
guide experience.

**repository-engine-1000**
The sovereign infrastructure project that manages ~1000 GitHub repositories.
The People's Home is the flagship product portfolio running on top of the engine.
All TPH repos should eventually be tracked by the engine.

**Railway**
The cloud deployment platform for Kilimanjaro. Auto-deploys from the main branch.
Runs with `NODE_ENV=production` (Nixpacks), so build-time dependencies must be in
`dependencies`, not `devDependencies`.

**Cloudflare Pages**
The static hosting platform for all World-A learning apps. Free, global CDN, supports
offline PWA service workers. URL pattern: `https://<slug>.pages.dev/`.

---

## People

**Sifiso Cyprian Shezi**
The founder, sole builder, and architect of The People's Home ecosystem.
GitHub: `SifisoScS`.

**Claude Code**
The AI coding assistant running all development sessions in this project.
(Powered by Anthropic's Claude models.)

---

## Abbreviations

| Abbrev | Meaning |
|---|---|
| TPH | The People's Home |
| NPC | Non-Profit Company (SA legal entity) |
| PWA | Progressive Web App (installable, offline-capable web app) |
| SDK | Software Development Kit |
| SA | South Africa |
| TTS | Text-To-Speech (narration) |
| AAB | Android App Bundle (Google Play format) |
| RAG | Retrieval-Augmented Generation (search + inject context into AI prompt) |
| SAST | South Africa Standard Time (UTC+2) |
| E.164 | International phone number format (e.g., `+27821234567`) |
