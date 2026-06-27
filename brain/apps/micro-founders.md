# Micro Founders

> 🚀 **Real-World Empowerment** (Pillar 05) · ages **13–17** (first) · **LIVE** (web PWA) ·
> repo `…/micro-founders` (private) · https://micro-founders.pages.dev/
> *"Turning skill into a living."* Blueprint LOCKED 2026-06-23. Full brief:
> [`../../MICRO_FOUNDERS.md`](../../MICRO_FOUNDERS.md).

---

## What it is
An app that teaches a young South African to turn a skill into a small venture, via a **5-stage
Venture Journey**:

```
1. Spot it  🔍   find the opportunity / problem worth solving
2. Cost it  💰   price it, understand margin
3. Sell it  🤝   find customers, frame the offer
4. Build it 🛠️   make / deliver the thing
5. Pitch it 🎤   present the venture
```

Each stage unlocks the next. A single persistent **"My Venture"** (chosen from an SA idea bank —
car wash, tutoring, vetkoek, hair braiding, airtime reselling, repairs…) is carried and enriched
through all five stages in `localStorage`.

## Why it exists
Pillar 05 — empowerment. The "make a living from your skill" capability. It's also the app
expression of the user's enduring **"1 Million Startups in 12 Months"** campaign (shared with The
Golden Hand's *Golden Startup*).

## Original vision
The Real-World Empowerment app on the same offline, no-login, SA-first constraints as every World-A
app, teens-first.

## Design iterations / how the thinking evolved
- **THE BIG CALL: a Venture *Journey*, not parallel age-muscles (2026-06-23).** It is built on the
  same **Atelier chassis** as Truth Seekers, but its *spine is deliberately different* — a sequential
  5-stage chain, not Truth Seekers' independent muscles.
  - **Why:** founding is *inherently directional* — you can't cost what you haven't spotted, can't
    pitch what you haven't built. Reasoning skills are independent; founding is a chain. *Two apps
    modelling differently is intentional — the shape teaches the difference between a set of skills
    and a journey.*
  - **Age survives as a within-stage difficulty dial**, not the top axis.

## Architectural decisions (& rejected alternatives)
- **Reuse the Atelier chassis + `ReasonCase` engine** from Truth Seekers; build **3 bespoke
  activities**: Cost & Price board (Stage 2) · Venture Canvas (the My-Venture summary) · Pitch
  Builder (Stage 5). *Rejected:* Truth Seekers' parallel-muscle structure (wrong for a directional
  skill).
- **Hard boundary with Mzansi Money:** Micro Founders = *make* money (entrepreneurship); Mzansi
  Money = *manage* money (financial literacy). Kept as distinct apps. *Rejected:* one combined
  "money" app.
- **Spans World A → B:** teaches offline, then hands off to iKhaya's Community & Mentor Services
  ("the bridge"). *Rejected:* baking mentor/community features into the offline app (that's World B).

## Current state
Live web PWA, 13–17. Full 5-stage journey + all 3 bespoke activities playable end-to-end with one
persistent "My Venture."

## Future direction
Extend down in age as TPH matures; the iKhaya handoff (mentors, cooperatives, impact) is the
World-B continuation. Deepen scenario content per age band.

## Related
- [`../../MICRO_FOUNDERS.md`](../../MICRO_FOUNDERS.md) (full blueprint) ·
  [`mzansi-money.md`](./mzansi-money.md) (the boundary) ·
  [`truth-seekers.md`](./truth-seekers.md) (the shape contrast) ·
  [`the-golden-hand.md`](./the-golden-hand.md) (shared "1M Startups" vision) ·
  [`../platform/ikhaya.md`](../platform/ikhaya.md) (the bridge).
