# African Discoveries

> 🔭 **Curiosity & Knowledge** · ages **3–17** · **✅ LIVE** at
> **https://african-discoveries.pages.dev/** — installable offline PWA · linked on The People's Home ·
> brought in-house 2026-07-06

The **fourth Curiosity & Knowledge app** (after Science Sprouts, Our World and [[space-explorer]]).
Built externally by the founder in **Gemini** via a **Manus/Builder "forge" scaffold**, then brought
fully in-house — the same path as [[space-explorer]] / [[early-literacy]]. Repo:
`ARISAN-SIFISO-TECHNOLOGY-EDUCATION/african-discoveries` (PRIVATE, branch **`main`**), local
`C:\Users\sifis\Next-Level-Projects\african-discoveries`.

---

## What it is

A curiosity-driven celebration of Africa for children 3–17 — **heroes**, **wildlife**, **innovations**
and a **timeline**, with a discovery-unlocking loop, an adventure **Journal**, and age-adaptive
**activities** (matching · timeline-ordering · innovation quiz). Six screens via a bottom nav: **Home ·
Explore** (Africa-map illustration + country cards) **· Discover** (50+ discoveries) **· Activities ·
Journal · Profile**. All state is local — `localStorage: ad_discovered_items`, `ad_user_progress`.
**React 19 · Vite 7 · TypeScript · Tailwind v4 · wouter · shadcn/radix · framer-motion**, **pnpm**.
Self-hosted **Fredoka** font. No reading gate, no fail state, **no runtime AI**.

## In-house conversion (2026-07-06)

Same playbook as Space Explorer / Early Literacy. **No educational content or UI logic changed** —
the scaffold was stripped and the app hardened for offline #FreeForever.

- **Scaffold stripped** (commit `c7affc3`): deleted dead **Google-Maps `Map.tsx`** (+ forge image
  proxy `forge.butterfly-effect.dev`), the **Manus OAuth login** (`ManusDialog` + `const.ts`, never
  rendered), `public/__manus__` **debug collector**, the **umami analytics** script, and the
  **Manus/Builder vite plugins** (`vite-plugin-manus-runtime`, `@builder.io/vite-plugin-jsx-loc`,
  storage-proxy + debug-collector). **Dropped the express `server/`** → deploys as pure static. Pruned
  dead deps; `tsc --noEmit` 0.
- **Image recovery:** all 6 image assets were missing (they lived on Manus hosting, not in the export).
  Recovered from the **published Manus app** (`https://africandis-3iutr9kd.manus.space`, signed
  CloudFront 307s) into `client/public/manus-storage/`. They're **WebP bytes named `.png`** (browsers
  render fine); `hero-home.png` didn't exist on Manus → aliased from the hashed copy.
- **True offline:** **self-hosted Fredoka** (variable woff2 latin + latin-ext in `public/fonts/`, local
  `@font-face`) — removed the live `fonts.googleapis.com` `@import`. **Zero external requests** confirmed.
- **Security `public/_headers`:** strict **CSP** (`default-src 'self'`, everything pinned to `'self'`,
  `object-src 'none'`, `frame-ancestors 'none'`; `style-src 'unsafe-inline'` for Tailwind/radix) +
  X-Frame-Options DENY, nosniff, no-referrer, locked Permissions-Policy.
- **Offline PWA:** `vite-plugin-pwa` (Workbox generateSW, autoUpdate) — precache **28 entries / 4.7 MB**
  → fully offline after first load. Unique manifest **`id: "african-discoveries"`**; **true-PNG**
  any + maskable icons + favicons generated from the Kito hornbill logo (Python/Pillow). `registerSW.js`
  external → CSP `script-src 'self'` holds.
- **Deploy prep:** `package.json` build → `vite build` (output `dist/public`); `.node-version` **22**
  (Vite 7 needs ≥20.19 on Cloudflare). No env vars, no keys.

## ✅ Deployed & linked (2026-07-06)

- **LIVE at https://african-discoveries.pages.dev/** — git-connected Cloudflare Pages (build
  `pnpm build`, output `dist/public`, branch `main`). Verified serving: 200s on app/SW/manifest/icons/
  fonts/images, SPA routing, **CSP + security headers applied**, **zero external hosts** in served HTML.
- **Linked on The People's Home** — Curiosity & Knowledge pillar card flipped `status:'future'` →
  `status:'live'` (was already listed as a placeholder).

## Backlog / debts

- **Real-child play-test** — the standing World-A human gate (shared with Space Explorer). Not yet done.
- The recovered `.png` images are WebP bytes (fine for `<img>`, correct type served for the real PNG
  icons). Optional: rename to `.webp` for correctness.
- **isiZulu / multilingual** — English-first like all apps; deferred to the batched review.
- Unused shadcn/ui components and a few scaffold files (`template.json`, `components.json`, `ideas.md`,
  `COMPLETION_SUMMARY.md`, `IMPLEMENTATION.md`) remain — harmless, could be trimmed later.
