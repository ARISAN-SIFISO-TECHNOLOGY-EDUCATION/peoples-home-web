# MICRO FOUNDERS — App Blueprint (Pillar 05 · Real-World Empowerment)

> **"Turning skill into a living."** Pillar 05 · Real-World Empowerment.
> Blueprint **LOCKED 2026-06-23**. **LIVE** at https://micro-founders.pages.dev/ — full 5-stage journey
> playable + all 3 bespoke activities. Repo `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/micro-founders`.
> Last updated: 2026-06-23.

See also: [`BLUEPRINT.md`](./BLUEPRINT.md) (the master capability map) · [`ROADMAP.md`](./ROADMAP.md) ·
[`ECOSYSTEM.md`](./ECOSYSTEM.md) · [`DECISIONS.md`](./DECISIONS.md).

---

## What it is
Micro Founders is the **Real-World Empowerment** app (Pillar 05): it teaches a young South African
to turn a skill into a small venture. It is a sibling of Truth Seekers on the **same Atelier
chassis** — phone-frame UI, bead-path nav, `tone()` audio, Welcome front-door, picker,
parent/teacher Co-Pilot, Home/Back nav, PWA/offline.

**Locked constraints (same as every World-A app):** offline · no-login · no-server · no-data ·
#FreeForever · ages-not-grades · SA-first.

**Scope: teens 13–17 first.** Extend down only once The People's Home matures (same call as Truth
Seekers). This satisfies the age-ceiling-17 rule.

---

## The big structural call — Venture Journey, not age-tiers

**DECISION: the spine is a 5-stage VENTURE JOURNEY with sequential unlock — NOT Truth Seekers'
age-muscle shape.**

```
1. Spot it  🔍   find the opportunity / problem worth solving
2. Cost it  💰   price it, understand margin
3. Sell it  🤝   find customers, frame the offer
4. Build it 🛠️   make / deliver the thing
5. Pitch it 🎤   present the venture
```

Each stage unlocks the next.

**Why a sequence and not age-muscles:** entrepreneurship is *inherently directional* — you can't
cost what you haven't spotted, can't pitch what you haven't built. Truth Seekers used parallel
age-muscles because reasoning skills (fallacies / stats / bias) are independent competencies you can
attack in any order. Founding is the opposite — a chain. The two apps modelling differently is
deliberate: the shape teaches the difference between a *set of skills* and a *journey*.

**Age still matters — as a within-stage depth dial, not the top axis.** A 13- and a 17-year-old
doing *Cost it* need different complexity, so scenario content carries an internal age band that
scales difficulty *inside* each stage. Sequence is the skeleton; age scales the muscle on each bone.

---

## The "My Venture" through-line
One **persistent local venture** the learner picks early (from an SA idea bank) and enriches across
all five stages — carried in `localStorage`. This is the app's spine, not a side feature: *Spot it*
chooses it, *Cost it* prices it, *Sell it* finds its customers, *Build it* delivers it, *Pitch it*
presents it. The Venture Canvas (below) is its living summary.

**SA venture idea bank:** car wash · tutoring · vetkoek / food · hair braiding · airtime reselling ·
phone / appliance repairs · etc. Rand budgets, local contexts throughout.

---

## What we reuse vs build new
- **Reuse:** the Atelier chassis + the `ReasonCase` scenario engine from Truth Seekers (the
  working copy is the chassis template). Micro Founders is a *content sibling* on the same shell.
- **Build new — 3 bespoke activities** (the equivalent of Truth Seekers' bias slider / evidence
  board):
  - **Cost & Price board** (Stage 2 — Cost it)
  - **Venture Canvas** (the My-Venture summary, enriched across stages)
  - **Pitch Builder** (Stage 5 — Pitch it)

---

## Boundary with Mzansi Money (Pillar 06)
Hard line, keep them distinct:
- **Micro Founders** = *make* money via a venture (entrepreneurship).
- **Mzansi Money** = *manage* your own money (financial literacy).

---

## Deploy (the house pattern)
- New repo `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/micro-founders`.
- PWA manifest **unique `id` `/micro-founders/`** (sibling-collision rule).
- Cloudflare Pages — build `npm run build` · output `dist` · `NODE_VERSION=20` · **lockfile
  gitignored** (lenient `npm install`).
- Flip the People's Home **card 05 (Real-World Empowerment, 🚀)** from `soon` → `live`; capture the
  real `.pages.dev` URL; incognito-verify.

---

## Definition of done
Live PWA (offline-verified) + on this site (card 05 flipped to live) + unique manifest `id` +
**0 grade strings** + no runtime network calls + the 5-stage journey walks end-to-end with one
persistent "My Venture".
