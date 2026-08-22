# Session Record — 2026-08-17 · The People's Home: institutions pivot + deploy prep

> Durable record of what changed today and what was done. Factual log; decisions are the
> founder's. Nothing has been deployed or merged — see **Status** at the end.

---

## 1 · The shift (from the previous direction)

**Founder ruling (2026-08-17):** move The People's Home from *apps* to **systems / institutions**.
In the founder's words: *"apps are dying during this era of AI, so we better build
systems/institutions."*

- The People's Home has been **rebuilt separately** from the previous app portfolio — a new
  codebase, not an edit of the old one.
- This reframes the six pillars: each is now an **institution** with a named engine, not a
  standalone app.
- **Contrast with the last session (2026-07-26):** that session ended in a founder HALT —
  the Launch Experience Review scored the old portfolio **0/6 worthy as-is** ("this whole
  project is a mess — rethink UI + content"). Today's work is the constructive answer to that
  blocker: a single coherent, approved Home shell that treats the pillars as one connected
  house rather than a set of look-alike apps. The old-portfolio findings
  (`launch-experience-review-notes-2026-07-26.md`) still stand as history.

## 2 · What was chosen / approved

**New repo (approved, "chosen and approved version"):**
`github.com/ARISAN-SIFISO-TECHNOLOGY-EDUCATION/the-peoples-home`

- Manus-generated: React 19 + Vite 7 + Tailwind v4 + shadcn/ui + `wouter`.
- One real page: `client/src/pages/Home.tsx`. Design system **"The Porch Light"** — warm
  humanist editorial, **Porch Blue `#1F4D6B`**, DM Sans + Fraunces, "one home, many rooms".
- Honest scope: this is a strong **front-door shell**. The learning content/engines behind
  the rooms are **not built yet**.

**The six pillars → "Parallel Rivers" institutions:**

| Pillar | Institution | Experiences |
|---|---|---|
| Foundations | Parallel Rivers **Math** Engine | 2 (numeracy + literacy) |
| Curiosity & Knowledge | Parallel Rivers **Science** Engine | 1 |
| Creation & Technology | Parallel Rivers **Maker** Engine | 1 |
| Thinking & Reasoning | Parallel Rivers **Logic** Engine | 1 |
| Money & Financial Capability | Parallel Rivers **Finance** Engine | 1 |
| Entrepreneurship | Parallel Rivers **Venture** Engine | 1 |

## 3 · Hosting decision

- **Company** iKhaya AI → **Hostinger**, apex `ikhaya-ai.com` (unchanged; the company page).
- **Rule:** every system iKhaya AI builds gets **its own subdomain** of `ikhaya-ai.com`
  (Premium plan supports 3 more sites). One subdomain per system, repeatable.
- **The People's Home → `peopleshome.ikhaya-ai.com`** — founder chose `peopleshome` over
  `home` (ambiguous with the company) and `tph` (opaque) for clarity to rural + urban users.
- Added as a Hostinger **"Custom PHP/HTML"** static site (it's a static, offline-first PWA;
  no server process needed — the Express server was dropped for hosting).

## 4 · What was done (deploy prep) — branch `deploy/hostinger-peopleshome` (pushed, not merged)

Made the build deployable outside Manus, cheap for low-bandwidth users, and offline-complete:

- **Images baked in + optimized:** four hero/brand images moved from Manus's private storage
  (`/manus-storage/`, only resolves inside Manus) into `client/public/images/`, resized to
  display size, WebP for the three illustrations + 512² PNG logo. **21 MB → 0.64 MB.**
- **Fonts self-hosted:** DM Sans + Fraunces (latin + latin-ext, all weights) served from
  `/fonts/`; Google Fonts `@import` removed. **Last external network dependency gone** —
  fonts now render offline. +0.32 MB.
- **Service-worker bug fixed:** `APP_SHELL` had listed the dead `/manus-storage/` paths;
  `cache.addAll()` is atomic, so install would have failed → **no offline at all**. Fixed
  paths, precached images + fonts, cache bumped to v5.
- **Routing:** `.htaccess` — SPA fallback to `index.html`, WebP/manifest MIME types,
  no-cache for `sw.js`.
- **Build hygiene:** Manus dev/debug plugins gated out of production (`index.html`
  367 KB → 0.8 KB); orphan `__manus__/` removed.

**Deployable output:** `C:\tphrun\dist\public\` — **1.4 MB**, self-contained (no Manus, no
Google), works offline. **Local working clone: `C:\tphrun`** (short path — the deep temp path
breaks `pnpm install` with `ENAMETOOLONG` on Windows via the wouter patch).

## 5 · Tomorrow (2026-08-18) — founder's agenda

1. **Deploy** The People's Home to `peopleshome.ikhaya-ai.com` (Hostinger, Custom PHP/HTML;
   enable SSL; zip-upload `dist/public` into `public_html`).
2. **Add the Parallel Rivers Math Engine to Foundations** — wire the first real institution
   (already built) behind the Foundations room.
3. **Security discussion** — how to secure the systems now that they are / will be live.

## Status

- Branch `deploy/hostinger-peopleshome` **pushed** to GitHub; **PR not opened, not merged.**
- **Nothing deployed.** No site is live at `peopleshome.ikhaya-ai.com` yet.
- Company site `ikhaya-ai.com` unchanged.
- Founder stopped for the night; resumes fresh 2026-08-18.
