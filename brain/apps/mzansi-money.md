# Mzansi Money

> 💰 **Money & Opportunity** (Pillar 06) · ages **13–17** · **LIVE** (web PWA) ·
> repo `…/mzansi-money` · https://mzansi-money.pages.dev/
> *"My Money, sorted."* The financial-literacy half of the Money pillar.

---

## What it is
A money-wisdom journey on a **5-stage Money Journey**: **Earn → Budget → Save → Borrow → Protect,
Grow & Plan.** Killer feature: a **Money Situations picker**. Bespoke activities: **Budget Board**,
**Credit Calculator**, **My Money Plan**. Palette is **indigo + gold + teal** (deliberately *not*
green).

## Why it exists
Pillar 06 — connect learning to economic mobility. Mzansi Money teaches a young South African to
**manage their own money** with dignity and local realism (Rand, SA situations), offline and free.

## Original vision
A teens-13–17 financial-literacy app built on the proven Micro Founders chassis.

## Design iterations / how the thinking evolved
- **Defined against Micro Founders.** The clarifying decision (2026-06-23): *make* money (Micro
  Founders) vs *manage* money (Mzansi Money). That boundary kept them as two distinct apps rather
  than one bloated "money" product.
- **"Money wisdom, never advice."** A firm content stance: no crypto / forex / trading. It teaches
  durable habits and judgment, not speculative product tips — avoiding both harm and regulatory risk.
- **Colour as positioning.** Chose indigo+gold+teal over the obvious "money green" to feel like
  wisdom/dignity rather than banking/cash.

## Architectural decisions (& rejected alternatives)
- **Reuse the Micro Founders chassis** (itself the Atelier chassis) — content sibling, not new
  framework. *Rejected:* a bespoke build.
- **Spans World A → B (the bridge):** teaches offline, hands off to iKhaya's Opportunity Hub for
  real jobs/funding (the Money pillar's "Job Ready" → iKhaya seam). *Rejected:* putting job/funding
  surfaces in the offline app (World B).

## Current state
Live web PWA, 13–17. 5-stage journey + Money Situations picker + Budget Board + Credit Calculator +
My Money Plan.

## Future direction
Deepen Money Situations; age-band depth; the iKhaya Opportunity-Hub handoff is the World-B
continuation (the 6 navigators, Side Hustle Hub, Funding Finder).

## Related
- [`micro-founders.md`](./micro-founders.md) (the *make* vs *manage* boundary; shared chassis) ·
  [`../platform/ikhaya.md`](../platform/ikhaya.md) (the bridge / Opportunity Hub) ·
  [`../architecture/02-world-a-world-b-dna.md`](../architecture/02-world-a-world-b-dna.md).
