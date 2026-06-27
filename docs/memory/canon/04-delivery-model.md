# Canon 04 — The Delivery Model

> How learning apps actually reach people. The web-first pivot, the Google Play wind-down, and the
> house deploy pattern every app follows. Operational specifics live in
> [`../../../ECOSYSTEM.md`](../../../ECOSYSTEM.md) and [`../../../DEPLOY.md`](../../../DEPLOY.md);
> this is the *thinking*.

---

## The pivot (2026-06-12)

- **Before:** Google Play as the primary channel — the "release machine" (keystore, AAB, signed
  bundles, target-audience declarations, staged rollout, review waits).
- **After:** ship each learning app as an offline, installable **Cloudflare Pages PWA**, then
  surface it as a card on the People's Home site.
- **Why:**
  - Play review was **slow and morale-sapping** for a solo developer.
  - The apps were **already React + Vite** → PWA conversion is cheap.
  - PWAs reach the **low-connectivity SA audience** better: install once from a `.pages.dev` link,
    then run **fully offline**. No store account, no 100 MB download gate.
  - Cloudflare's free tier gives **unlimited bandwidth** and strong **African edge** presence
    (Johannesburg, Cape Town, Durban).

## The wind-down (2026-06-21)

- **Science Sprouts is the last app on Google Play, ever.** It was already in the Play pipeline and
  *granted production access*, so it's finished out (promote the tested build → production, staged
  rollout). **After SS, the Play release machine is retired.**
- Math Adventure + Science Sprouts remain **maintenance-only** on Play. Every app from Truth Seekers
  onward is **web-first PWA only** — no Play track. This is the clean tail of the wind-down, not a
  return to Play.

---

## The house deploy pattern (every learning app)

1. **Stack:** React + Vite + TypeScript + Tailwind (a few exceptions: SIFISO is CRA; the umbrella
   site is plain static HTML). PWA via `vite-plugin-pwa` (Workbox for CRA).
2. **Host:** Cloudflare Pages — one project per app, auto-deploys from `main` on push. Build
   `npm run build`, output `dist` (CRA: `build`), `NODE_VERSION=20`.
3. **Surface it:** flip the app's card on the People's Home `index.html` from `soon` → `live`,
   capture the **actual** `.pages.dev` URL, incognito-verify.

### Hard-won gotchas (read before deploying)
- **Lockfile gitignored** on several apps (Tech Makers, SIFISO, Truth Seekers, Micro Founders, …)
  so Cloudflare uses lenient `npm install` not `npm ci` — `npm ci` breaks on Vite 8 `@emnapi` /
  CRA dep drift.
- **CRA (SIFISO)** must build with **`CI=false`** (else ESLint warnings fail the build); output is
  `build`, not `dist`.
- **Cloudflare URL trap:** if the bare project name is taken, Cloudflare suffixes it (Science
  Sprouts → `science-sprouts-65b`; Our World → `our-world-b0t`). Always capture the **real** URL
  from the dashboard — never assume the clean name.
- **Unique PWA manifest `id`** per app (e.g. `/our-world/`) — sibling apps on the same origin
  collide without it. (This bit during local `localhost:4173` testing of sibling apps.)
- **SW registered web-only** — gate native via Capacitor when a native wrapper is present.
- **Narration** uses Math Adventure's robust `useNarration`; device-audio is a release gate
  (see [`03-product-rules.md`](./03-product-rules.md)).

---

## The "chassis" lineage (why apps look alike)

Apps deliberately **inherit a chassis** rather than reinventing UI:
- **Truth Seekers** built the "Atelier" chassis (phone-frame UI, bead-path nav, `tone()` audio,
  Welcome front-door, picker, parent/teacher Co-Pilot, Home/Back nav, PWA/offline).
- **Micro Founders** reused it → **Mzansi Money** reused Micro Founders' → **Everyday Foundations**
  reused that → **Our World** reused EF's.
- **Why:** one solo developer can't hand-build ten bespoke UIs. A shared chassis makes each new app
  a *content* problem, not a *framework* problem — and is the informal precursor to extracting
  **TPH Core** ([`05-tph-core-and-passport.md`](./05-tph-core-and-passport.md)).

---

## Related
- [`../../../ECOSYSTEM.md`](../../../ECOSYSTEM.md) — the live per-app build table.
- [`../../../DEPLOY.md`](../../../DEPLOY.md) — the umbrella site's own deploy guide.
- [`05-tph-core-and-passport.md`](./05-tph-core-and-passport.md) — where the shared chassis is heading.
