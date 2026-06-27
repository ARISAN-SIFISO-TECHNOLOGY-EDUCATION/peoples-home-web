# Our World

> 🌱 **Curiosity & Knowledge** · **all ages** · **LIVE** (web PWA, shipped 2026-06-27) ·
> repo `…/our-world` (private) · https://our-world-b0t.pages.dev/
> Science Sprouts' companion. The app whose launch meant **every World-A pillar now has a live app.**

---

## What it is
A humanities/belonging app — **NOT a geography quiz**. A **belonging journey** structured as
**Place · People · Planet**, travelling outward from 🏡 **My Home**. Six Journeys (South Africa
authored **deep** — 7 hand-verified discoveries; Africa · The World · Nature · Cultures · Big Trips
"Coming soon"). Has a 📘 **My Passport** of **first-person stamps** (never %), voice-first,
Household Mode.

## Why it exists
Pillar 2 (Curiosity) needed a humanities counterpart to Science Sprouts' science. Where Science
Sprouts asks *how does the world work?*, Our World asks *where do I belong in it?* — geography,
history, and cultures reframed as **belonging**, outward from the learner's own home.

## Original vision
A humanities app (Explore SA / History Alive / World Explorer per the BLUEPRINT) — but reframed
during build from "learn facts about places" into a **belonging journey**.

## Design iterations / how the thinking evolved
- **Reframed from quiz → belonging journey.** The decisive design move: not "test what you know
  about South Africa," but "discover your place in widening circles" (Home → SA → Africa → World).
  Progress is **first-person "I discovered…" stamps**, never percentages — dignity by design.
- **First real home of the Passport.** Our World's `content/passport.ts` is the **first real
  implementation** of the [People's Home Passport](../platform/peoples-home-passport.md) — the
  downloadable-JSON mechanism for carrying stamps *between* apps. This app is where the cross-app
  shared-state pattern became concrete.
- **Inherited the EF chassis** (voice-first, Household Mode, all-ages) — the latest link in the
  Atelier chassis lineage.

## Architectural decisions (& rejected alternatives)
- **Passport = downloadable JSON, learner-held.** *Rejected:* a central store (World B) and shared
  `localStorage` (impossible across origins). The file is the only thing that survives offline +
  separate origins + no-server. See [`../canon/05-tph-core-and-passport.md`](../architecture/03-tph-core-and-passport.md).
- **First-person stamps, not scores.** *Rejected:* quiz %/leaderboards (wrong emotional register
  for "belonging").

## Current state
Live web PWA, all ages. South Africa journey deep (7 discoveries); other five Journeys "Coming soon."
**With it shipped, every World-A pillar has ≥1 live app** — the build-the-apps phase closes; deepen
passes + platform + iKhaya are the frontier.

## Future direction
Author the other five Journeys; age-band depths; bespoke activities; multilingual. As the Passport's
origin app, it's central to proving cross-app continuity once Math Adventure (the second consumer)
and more apps adopt it.

## Related
- [`../platform/peoples-home-passport.md`](../platform/peoples-home-passport.md) (its signature pattern) ·
  [`science-sprouts.md`](./science-sprouts.md) (Curiosity companion) ·
  [`everyday-foundations.md`](./everyday-foundations.md) (chassis parent: voice-first, Household Mode).
