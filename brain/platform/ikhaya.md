# iKhaya — the Opportunity Layer (World B)

> **World B · opportunity infrastructure.** Server-backed, accounts, PII, POPIA, moderation.
> The 2027 People's Home flagship. *(iKhaya = "home".)*
> Context: [`../architecture/02-world-a-world-b-dna.md`](../architecture/02-world-a-world-b-dna.md).

---

## What it is
The **opportunity layer** of The People's Home — described as a "LinkedIn for blue-collar South
Africa." It is **one platform** that holds everything server-backed:
- **Opportunity Hub** — the 6 navigators (University · TVET · Bursary · Career · Learnership ·
  Internship) + Side Hustle Hub · Tender Starter · Funding Finder · Freelancer Toolkit.
- **Community & Mentor Services** — mentors, communities, cooperatives, civic action, impact tracking.

## Why it exists
The whole thesis is *"education → pathway."* The offline apps teach capability for free; **iKhaya is
where a *ready* learner connects to real opportunity** — jobs, funding, mentors. Without iKhaya, the
learning has no economic destination. It is the second half of the mission ("…earn, and create
opportunity").

## Original vision
A jobs/social network for blue-collar SA — the "Opportunity" layer of the People's Home, the 2027
flagship.

## Design iterations / how the thinking evolved
- **Everything World-B consolidates *into* iKhaya.** Earlier thinking imagined separate apps for
  jobs, mentors, the navigators, funding, community. The capability architecture (2026-06-21) folded
  them all into **one platform** — the 6 navigators are *in-app sections*, not 6 apps. (Same
  module-over-new-app discipline as World A.)
- **"The bridge" defines the seam.** The Money (Mzansi Money) and Empowerment (Micro Founders) apps
  *teach offline* then *hand off* to iKhaya. That clean handoff is what keeps the learning apps pure
  while still reaching real opportunity.
- **The funding fork surfaced.** Being server-backed + PII means Play "data IS collected" + POPIA,
  and a real **running backend cost.** This makes iKhaya **the one place #FreeForever needs a
  sustainability answer** — the *#FreeForever funding fork*.

## Architectural decisions (& rejected alternatives)
- **One platform, not many World-B apps.** *Rejected:* standalone jobs/mentor/navigator apps.
- **Server-backed + accounts + POPIA — contained here.** *Rejected:* letting any of this leak into
  the offline learning apps (would break their free/offline/no-data promise — the DNA split).
- **#FreeForever funding fork — must be resolved before the 2027 launch.** Candidate answers:
  Azure/Microsoft-for-Startups credits, freemium on the opportunity side, Foundation/grant support.
  **Open decision** — see [`../DECISIONS.md`](../decisions/DECISIONS.md).

## Current state
**Prototype ~4/10 (Lovable), own backend/stack.** 2026 goal: a **one-suburb closed beta.** 2027:
the People's Home flagship launch. The Opportunity Hub navigators currently exist as bundled static
data inside the prototype.

## Future direction
Build toward the one-suburb beta as a steady background track (parallel to the World-A deepen
passes); **resolve the funding fork before 2027.** This is the long arc — the apps are the proof,
iKhaya is the payoff.

## Related
- [`../architecture/02-world-a-world-b-dna.md`](../architecture/02-world-a-world-b-dna.md) (why it's separate) ·
  [`ikhaya-learn.md`](./ikhaya-learn.md) (a related server-backed learning portal) ·
  [`../apps/mzansi-money.md`](../apps/mzansi-money.md) · [`../apps/micro-founders.md`](../apps/micro-founders.md)
  (the apps that bridge into it).
