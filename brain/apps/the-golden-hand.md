# SIFISO — The Golden Hand

> 🔧 **Creation & Technology** · **LIVE** (web PWA) ·
> repo `…/sifiso-learn-python` *(slug kept)* · https://sifiso-learn-python.pages.dev/
> **The original prototype of the whole People's Home idea** — "one shell, five apps."

---

## What it is
A **five-app-in-one system** presented as a journey:

```
Golden Learn (Python) → Golden AI (AI literacy) → Golden Quiz (mastery)
   → Golden Startup (1M Startups) → Golden Commons (Each One, Teach One)
```

100% offline — it **self-hosts Pyodide** (~12 MB) + **Monaco**, so it runs real Python with no
connection. Stack is CRA (react-scripts 5) · React 19 · Tailwind v3.

## Why it exists
Creation, at depth: not block-coding but **real programming + AI literacy + a path to building a
startup and teaching others.** It's the most ambitious single app — a whole arc from learner to
founder to teacher.

## Original vision
Began as **"SIFISO — Learn Python."** But it was always more than a Python course — it was a
five-stage system, effectively a working model of "one home, many journeys" before the People's
Home had that name. It is described as the **original prototype** of the whole platform.

## Design iterations / how the thinking evolved
- **The rename (2026-06-23): "Learn Python" → "The Golden Hand."** Recognising it was never a
  Python course but a five-app journey. The in-app title already said "The Golden Hand"; the rename
  propagated the true name across the ecosystem (cards, docs, manifest). **Repo slug + URL kept** to
  avoid breaking Cloudflare/the live link — display name only. (See [`../HISTORY.md`](../history/HISTORY.md).)
- **Golden Startup carries a bigger campaign.** Its "1 Million Startups in 12 Months" thread is the
  *same vision* that later became the **Micro Founders** app (Pillar 05) — one vision, two
  expressions. (See [`micro-founders.md`](./micro-founders.md).)
- **A second, server-backed framing exists.** Notes describe an AI-native, server-backed "v2"
  direction (Railway-hosted, a 5-app ecosystem of its own). **The relationship between the offline
  Golden Hand and any server-backed direction is UNRESOLVED** — flagged as an open question, because
  server-backed = World B DNA, which doesn't belong in an offline learning app.

## Architectural decisions (& rejected alternatives)
- **Stays a separate app from Tech Makers (2026-06-20)** — different audience/depth; merging would
  bolt Pyodide+Monaco onto Tech Makers' light bundle. *Rejected:* one combined Creation app.
- **Self-host Pyodide + Monaco for true offline.** *Rejected:* CDN-loaded Python (would break the
  offline rule).
- **CRA build quirks:** must build with **`CI=false`**; output dir is **`build`** not `dist`;
  **lockfile gitignored**. (See [`../canon/04-delivery-model.md`](../vision/02-delivery-model.md).)
- **"Listening, not analytics"** privacy framing — an offline mock-AI literacy engine, no tracking.

## Current state
Live web PWA, fully offline. Includes a standalone-worthy **420-question / 7-category Golden Quiz**.

## Future direction
A planned **Web (HTML/CSS/JS) track** inside the journey (AI literacy already ships as Golden AI).
**Resolve the offline-vs-server-backed question** before investing in any v2 direction — keep the
offline app World-A-pure. See open decisions in [`../DECISIONS.md`](../decisions/DECISIONS.md).

## Related
- [`tech-makers.md`](./tech-makers.md) (the separation decision) ·
  [`micro-founders.md`](./micro-founders.md) (shared "1M Startups" vision) ·
  [`../architecture/02-world-a-world-b-dna.md`](../architecture/02-world-a-world-b-dna.md) (why server-backed is a problem here).
