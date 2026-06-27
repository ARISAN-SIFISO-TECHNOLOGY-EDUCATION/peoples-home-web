# Tech Makers

> 🔧 **Creation & Technology** · ages **3–17** · **LIVE** (web PWA) ·
> repo `…/tech-makers` · https://tech-makers.pages.dev/
> Built 2026-06-11. Turns consumers into creators.

---

## What it is
A creation/technology app: **Maker Studio · a Coding arc (block → web → projects) · Robotics**
(electronics/automation basics). SA-first CAPS Technology, no-photo, 6 topics across 4 age bands.

## Why it exists
Pillar 3 — "turn consumers into creators." Most learning apps teach *consumption* of knowledge;
Tech Makers teaches *making* — the bridge from using technology to building with it.

## Original vision
A CAPS-Technology maker app for SA children, light-weight and offline, spanning age bands.

## Design iterations / how the thinking evolved
- **Stayed deliberately light.** A key boundary call (2026-06-20): **SIFISO — The Golden Hand stays
  a separate app**, *not* merged into Tech Makers — because merging would bolt heavy Pyodide+Monaco
  onto Tech Makers' light bundle. Tech Makers keeps the *block→web→projects* coding arc light;
  SIFISO carries the heavy, real-Python depth. (See [`the-golden-hand.md`](./the-golden-hand.md).)
- **Carries the narration rule.** Flagged early to use Math Adventure's robust `useNarration`
  (porting it), so it would not repeat Science Sprouts' silent-launch mistake; device-audio is a
  release gate.

## Architectural decisions (& rejected alternatives)
- **Capstone modules, not new apps.** "App Builder Lab / Open Source Builder" were considered as
  separate products but **folded** as candidate *capstone modules* inside Tech Makers / The Golden
  Hand (module-over-new-app). *Rejected:* spinning them as standalone apps.
- House stack: Vite 8 · React 19 · TS 6 · Tailwind v4 · Capacitor 8; **lockfile gitignored** (Vite 8
  `@emnapi` breaks `npm ci` on Cloudflare).

## Current state
Live web PWA, maker arc 3–17.

## Future direction
Deepen the coding arc and robotics; potentially host the folded capstone modules. The planned **Web
(HTML/CSS/JS) track** is shared conceptually with The Golden Hand — keep the boundary clean.

## Related
- [`the-golden-hand.md`](./the-golden-hand.md) (its Creation sibling; the separation decision) ·
  [`../canon/01-capability-architecture.md`](../canon/01-capability-architecture.md) (module discipline).
