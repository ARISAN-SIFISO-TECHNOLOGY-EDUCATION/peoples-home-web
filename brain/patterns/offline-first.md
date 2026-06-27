# Pattern: Offline-First

> **Core DNA of every World-A app.** This is not an optimisation or a feature —
> it is the foundational constraint that defines what The People's Home is for.

---

## What it is

Every World-A learning app must work completely with zero network connectivity.
The core learning loop — open app, navigate, learn, make progress — must function
when the device has never been online or when connectivity is permanently unavailable.

---

## Why we use it

The People's Home is built for every South African, including those in townships,
rural areas, and households where mobile data is expensive or intermittent. An app
that requires an internet connection to function is an app that excludes the people
who need it most.

**The constraint is also a design clarity tool.** It forces every feature to be
self-contained. You cannot lean on a server to do work. The app must carry everything.

---

## How it is implemented

### Delivery model

All World-A apps deploy as **Cloudflare Pages PWAs** (Progressive Web Apps):
- `index.html` + assets served from Cloudflare's global CDN
- Service worker caches all assets on first visit
- After first load: fully offline
- No server-side rendering; no API calls in the learning loop

### Build stack (standard)

```
React + Vite → static build → Cloudflare Pages
```

Optional Capacitor wrapper for Google Play (Math Adventure + Science Sprouts only;
no new Play submissions after 2026-06-21).

### What "offline" means in practice

- All content (text, audio, images) must be bundled or service-worker-cached
- No analytics pings that block the UI
- No CDN-hosted fonts or assets — bundle everything
- No external API calls in critical paths (AI features, if added, degrade gracefully)
- Progress state lives in `localStorage` or IndexedDB — never on a server

### What is allowed

- One-time asset download on first online visit (e.g., heavy audio packs as optional downloads)
- The People's Home Passport export/import (user-initiated, not automatic)
- In future: background sync when online (for Passport to iKhaya) — but the app must
  still work fully without it

---

## Where it is used

| App | Notes |
|---|---|
| Math Adventure RPG | Offline from day 1. Also Android via Capacitor. |
| ReadAfrica | Hosts TPH Core SDK; fully offline. |
| Science Sprouts | Web PWA + Capacitor (Play). Last app to ever use Capacitor. |
| Tech Makers | Web PWA only. Full maker arc offline. |
| SIFISO — The Golden Hand | Offline Python via Pyodide (WebAssembly). Heaviest bundle. |
| Truth Seekers | Offline. 24 SA scenarios fully bundled. |
| Micro Founders | Offline. Venture Journey + My Venture persistence in localStorage. |
| Mzansi Money | Offline. Budget Board + Credit Calculator all local. |
| Everyday Foundations | Offline + Voice-first. Adult on-ramp with no data cost. |
| Our World | Offline + Voice-first. Household Mode. Our World Journey authored deep. |

---

## Rules and constraints

1. **Never add a required server call** in the learning loop. Advisory AI features are
   fine if they degrade gracefully (skip if offline); core navigation and content must not.

2. **Never lazy-load content from an external CDN** at runtime. Bundle it or don't include it.

3. **Service worker must be registered** on every app. Without it, "offline" is just
   "works if you never close the tab."

4. **Test offline before shipping.** In Chrome DevTools → Network → Offline: every core
   screen must load and function.

5. **World B (iKhaya) is explicitly exempt.** iKhaya requires a server and is not offline-first.
   The World A / World B DNA split exists precisely to hold this tension.

---

## Evolution

**Pre-2026:** Math Adventure RPG established the pattern informally (Capacitor/offline Android).

**2026-06-12 — Web-first pivot:** The pattern became the explicit deployment standard.
All new apps ship as Cloudflare Pages PWAs. Google Play is wind-down mode.
See [`../vision/02-delivery-model.md`](../vision/02-delivery-model.md).

**2026-06-21 — Formalised in BLUEPRINT v2:** World A DNA defined as "offline, free,
no login." The constraint became architecture, not just intent.
