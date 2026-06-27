# AI Onboarding — The People's Home

> For a future AI (or new engineer) with **zero prior context**.
> Read this file first, then follow the reading path below.
> You should be able to act safely after reading sections 1–4 (~10 minutes).
>
> **If you are resuming a session**, go directly to
> [`SESSION_HANDOFF.md`](./SESSION_HANDOFF.md) first.

---

## 1. Who owns this project

**Sifiso Cyprian Shezi** — the founder and sole builder.

- GitHub personal: `SifisoScS`
- GitHub org (most TPH repos): `ARISAN-SIFISO-TECHNOLOGY-EDUCATION`
- Email: `sifiso.cyprianshezi28@gmail.com`
- All repositories and products are **PRIVATE**. This is an internal solo system.
  Do not suggest making repos public unless Sifiso explicitly directs it.

**Infrastructure:**
- Learning apps: Cloudflare Pages (offline PWAs, no server)
- WhatsApp bot (Kilimanjaro): Railway (Node.js, TypeScript)
- iKhaya prototype: Lovable (early stage)
- Engine / orchestration: `repository-engine-1000` (local, Windows 11)

---

## 2. What this project is

**The People's Home** is a national capability-building ecosystem for South Africa.

Ten offline learning apps (World A) + one opportunity platform (iKhaya / World B,
launching 2027) + shared infrastructure (TPH Core SDK, People's Home Passport).

**The mission:** Give every South African — child or adult — a free, offline pathway
to learn, think, build, earn, and create opportunity.

**Key invariant:** ALL World-A learning apps are:
- **Offline** — no server required to use; the learning loop works without internet
- **Free forever** (#FreeForever — not freemium, not "free tier")
- **No login required** — open and use immediately
- **South Africa-first** — content, language, context, scenarios are SA
- **Ages-not-grades** — never "Grade 4"; always "Ages 8–10"

Breaking any of these rules breaks the project's foundation.

---

## 3. The reading path

Read in this order. The first four (~10 minutes) are enough to act safely.

### Phase 1 — The why (read first, always)

1. [`vision/00-vision-and-philosophy.md`](./vision/00-vision-and-philosophy.md)
   The mission and the worldview. Start here or nothing else makes sense.

2. [`architecture/01-capability-architecture.md`](./architecture/01-capability-architecture.md)
   How ~40 imagined apps collapsed into a capability system. The six pillars.

3. [`architecture/02-world-a-world-b-dna.md`](./architecture/02-world-a-world-b-dna.md)
   The single most important architectural idea: World A vs World B, and "the bridge."

4. [`vision/01-product-rules.md`](./vision/01-product-rules.md)
   The non-negotiables. Break one and you have broken the project.

### Phase 2 — The how

5. [`vision/02-delivery-model.md`](./vision/02-delivery-model.md)
   Web-first PWAs, the Google Play wind-down, the house deploy pattern.

6. [`architecture/03-tph-core-and-passport.md`](./architecture/03-tph-core-and-passport.md)
   The shared platform thesis: how state moves between separate offline apps.

7. [`../ECOSYSTEM.md`](../ECOSYSTEM.md) *(operational layer)*
   The live table: every repo, URL, stack, and build config. The map of the territory.

### Phase 3 — Where we are now

8. [`CURRENT_STATE.md`](./CURRENT_STATE.md)
   Snapshot of every app, track, and platform piece. **Read before doing any work.**

9. [`../ROADMAP.md`](../ROADMAP.md) *(operational layer)*
   The near-term priorities and status board.

10. [`PROJECT_TIMELINE.md`](./PROJECT_TIMELINE.md)
    How we got here, chronologically.

### Phase 4 — Deep dives (as needed for your task)

11. [`apps/`](./apps/) — memory for whichever app(s) you are working on.
12. [`platform/`](./platform/) — TPH Core, Passport, iKhaya.
13. [`decisions/`](./decisions/) + [`history/`](./history/) — reasoning archive and incident log.
14. [`patterns/`](./patterns/) — reusable patterns (offline-first, journey-progression, etc.).
15. [`PROJECT_GLOSSARY.md`](./PROJECT_GLOSSARY.md) — terminology and names.
16. [`PROJECT_DNA.md`](./PROJECT_DNA.md) — the sixteen immutable principles; check before any build decision.
17. [`playbooks/`](./playbooks/) — step-by-step runbooks for recurring tasks.
18. [`AI_SYSTEM_PROMPT.md`](./AI_SYSTEM_PROMPT.md) — **the operating charter**. How to think,
    review, and act as an engineering partner. Read this after the reading path to understand
    the review frameworks, engineering philosophy, and Final Review format.
19. [`SECURITY_CONSTITUTION.md`](./SECURITY_CONSTITUTION.md) — **the security operating charter**.
    How to operate as a security engineering partner. 22 review domains, threat modelling,
    adversarial review, and the Security Review Report template. Read this whenever security
    review, threat modelling, or secure architecture is the task.

---

## 4. How to work in this project

### Before writing any code or making any recommendation

- Re-read [`vision/01-product-rules.md`](./vision/01-product-rules.md).
  The rules are load-bearing and easy to violate accidentally.
- Check [`CURRENT_STATE.md`](./CURRENT_STATE.md) — many things that might seem
  "not yet built" are already live.
- When the memory system and an operational doc disagree on a *current fact*,
  the operational doc (`ECOSYSTEM.md` / `ROADMAP.md`) wins — then fix the memory doc.

### When choosing a model for AI features

Default to the latest Claude model. As of 2026-06-27 the Kilimanjaro WhatsApp bot
uses `claude-sonnet-4-6`. For production features, always use the latest available
model. Never hard-code model names without a comment noting the version and date.

### When security comes up

All repos and products are **PRIVATE**. The repository-engine-1000 and The People's Home
are internal solo infrastructure. Do not suggest:
- Making repos public
- Publishing npm packages publicly
- Exposing APIs without explicit auth

For any security review, threat modelling, or security architecture work, read
[`SECURITY_CONSTITUTION.md`](./SECURITY_CONSTITUTION.md) before proceeding.
It defines the 22 review domains, the adversarial mindset, and the Security Review
Report format that every security review must produce.

### When working on the WhatsApp bot (Kilimanjaro)

The bot lives at: `C:\Users\sifis\Next-Level-Projects\kilimanjaro`
Deployed on: Railway (autodeploy from main branch)
Bot identity: "The People's Guide" — community-facing assistant for The People's Home.
Admin gating: only `ADMIN_PHONE_NUMBER` gets personal tools (notes, reminders, invoices).
All other users get the community guide experience (10 apps, pillars, navigation).

### When working on the engine

`C:\Users\sifis\Next-Level-Projects\repository-engine-1000`
Read `CLAUDE.md` in that repo before touching anything.
The engine manages ~1000 repos and has strict invariants.
The People's Home is a permanent child/client of the engine.

---

## 5. How to update the memory system

**The brain is only trustworthy if it is kept current.** After any significant session:

1. **Update `SESSION_HANDOFF.md`** — what was done, what is next, any unresolved issues.
2. **Update `CURRENT_STATE.md`** — if any app status or platform state changed.
3. **Update `PROJECT_TIMELINE.md`** — if a significant milestone was reached (date it).
4. **Update the relevant `apps/` or `platform/` file** — if an app changed materially.
5. **Add to `decisions/DECISIONS.md`** — if a structural decision was made (append, never edit).
6. **Add to `history/HISTORY.md`** — if there was an incident, pivot, or retired idea.

**The golden rule:** append don't rewrite. Never overwrite history — add a dated entry.
See full rules in [`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md).

---

## 6. Key people, entities, and tools

| Name | What it is |
|---|---|
| **Sifiso Cyprian Shezi** | Founder and sole builder |
| **iKhaya AI** | The builder entity (part of ARISAN SIFISO Holdings) |
| **ARISAN SIFISO Holdings** | Parent company; iKhaya AI is the AI/tech arm |
| **The People's Home Foundation NPC** | NPC providing public-benefit mandate |
| **The People's Home** | The product ecosystem (10 apps + iKhaya + TPH Core) |
| **World A** | All offline learning apps (no server, no login, free forever) |
| **World B** | iKhaya — server-backed opportunity platform (2027) |
| **The bridge** | People's Home Passport — carries identity from World A to World B |
| **TPH Core SDK** | Shared code: narration, progress, Passport, activities |
| **repository-engine-1000** | Sovereign repo infrastructure; TPH is its flagship child |
| **Kilimanjaro** | The WhatsApp AI agent for The People's Home |
| **Claude Code** | The AI coding assistant running all sessions |

---

## 7. The six capability pillars

| # | Pillar | World-A apps (all live as of 2026-06-27) |
|---|---|---|
| 1 | Foundations | Math Adventure RPG, ReadAfrica, Everyday Foundations |
| 2 | Curiosity & Knowledge | Science Sprouts, Our World |
| 3 | Creation & Technology | Tech Makers, SIFISO — The Golden Hand |
| 4 | Thinking & Reasoning | Truth Seekers |
| 5 | Real-World Empowerment | Micro Founders |
| 6 | Money & Opportunity | Mzansi Money |

---

## 8. Red lines — never cross these

1. **Never add a login requirement** to a World-A app.
2. **Never make a World-A app paid** (not even freemium).
3. **Never require internet** in a World-A app's core learning loop.
4. **Never use grades** ("Grade 4") — always ages ("Ages 8–10").
5. **Never make repos public** without Sifiso's explicit instruction.
6. **AI has no execution authority** in the engine layer — advisory only.
7. **Never rewrite history** in the memory system — append only, always date.
