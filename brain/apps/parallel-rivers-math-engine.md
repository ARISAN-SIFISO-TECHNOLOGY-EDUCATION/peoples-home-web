# Parallel Rivers Math Engine

> 🌊 **Foundations** · ages **4–7** · **✅ LIVE** at
> `https://peopleshome.ikhaya-ai.com/math/` (2026-08-22) — installable offline PWA,
> South African English voice · River A = **101 micro-skills** across 16 tributaries
>
> **The first institution actually built.** Not an app in the old portfolio sense: an engine
> behind the Foundations room, reached from the house rather than standing beside it (**D-22**).

**Repo:** `SifisoScS/parallel-rivers-math-engine` — note this is under the *founder's personal*
account, not `ARISAN-SIFISO-TECHNOLOGY-EDUCATION` like the rest of the portfolio.

> For live build config see the operational [`../../ECOSYSTEM.md`](../../ECOSYSTEM.md).
> For deployment mechanics see `docs/deployment.md` **in the engine's own repo** — that is the
> authoritative technical record and is deliberately not duplicated here.

---

## Why it exists

The 2026-07-26 Launch Experience Review scored the previous portfolio **0/6 worthy as-is**. The
2026-08-17 founder ruling answered it by moving from *apps* to **systems / institutions**:
*"apps are dying during this era of AI, so we better build systems/institutions."* This is the
first pillar to get a real engine rather than a shell.

It is also a different *kind* of thing from Early Numeracy or Math Adventure RPG. Those are
experiences. This is a **pedagogical engine** — a governed kernel that decides what a child
meets next, and why.

## The constitution — five immutable laws

The engine's own `AI_CONTEXT.md` is its charter, and the laws are enforced in code by
`src/core/constitutional-validator.ts`, not merely documented:

1. **Mastery is 90%** plus time-fluency. A 0.85 floor exists only for `motor_skill` and
   `introductory_composition` exception nodes, which owe a 3/3 retest. *(Amended 2026-08-15 by
   founder ruling.)*
2. **Every question is tagged in four dimensions** — cognitive load, representation, error
   category, time-to-solve.
3. **CPA mandate** — Concrete → Pictorial → Abstract. **Teaching precedes testing**, always.
4. **A hidden bridge diagnostic** every 10th question, with silent re-rooting. The child is
   never told they are being diagnosed.
5. **No internet = no downtime.**

Law 5 is the one with a live dependency — see *Known debts* below.

## Architecture, briefly

**Three rivers**, of which only River A exists: **A — Mastery** (Singapore), **B — Applied**
(Finland/UK), **C — Olympiad**.

A **pure TypeScript kernel** (`src/core`, zero dependencies) sits under a Next.js shell in
`web/`, which integrates through exactly three calls. Questions are **seeded and deterministic**
per `(student, skill, session, index)` — any question is replayable without ever being stored.
The whole curriculum ships in the bundle, because Law 5 forbids fetching it.

**The UI never grades.** The session manager grades against the question it issued, so grading
truth never round-trips through the browser.

## State (2026-08-22)

- **Live and offline-verified on a real device.**
- **65 E2E checks across 9 suites**, green against the deployed shape.
- Reached from the Foundations room; the room no longer marks itself "explored" on entry,
  because progress is the engine's to observe, not the house's to claim.

## Known debts

- **Law 5 currently rests on host configuration.** The service worker does not precache its own
  content-hashed chunks — they are fetched before it claims the page — so offline works because
  `.htaccess` serves them immutably. A host that cannot set headers breaks offline **silently**.
  The durable fix is hardening the worker. **Not done.**
  *The People's Home shell has the identical defect. Check it on every new engine.*
- **No Content-Security-Policy.** The policy used by the portfolio's Vite apps would break this
  one on load, because Next's bootstrap uses inline script. Needs its own pass.
- **`__pr_debug`** is exposed in non-production builds. Founder-accepted; a server-authoritative
  boundary is a later phase.
- **Rivers B and C do not exist.** Neither does the Foundations pillar's second experience
  (literacy).

## Evidence status

**G6 is unmet.** This engine has **not been observed with a real child**. Being live is not
evidence — the [`../launch-readiness-2026-08-09.md`](../launch-readiness-2026-08-09.md) finding
stands unchanged: *the gap is evidential, not technical.*

## Related

- [[../session-2026-08-22-tph-and-math-engine-live.md]] — deployment session record
- [[../session-2026-08-17-institutions-pivot-and-deploy-prep.md]] — the institutions pivot
- **D-22** in [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) — room, not site
- [`early-numeracy.md`](./early-numeracy.md) — the *experience* for ages 3–5; the relationship
  between it and this engine is **Unknown / not yet ruled on by the founder.**
