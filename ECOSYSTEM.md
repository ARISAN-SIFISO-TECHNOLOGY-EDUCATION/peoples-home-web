# THE PEOPLE'S HOME — Ecosystem Index

> The map of everything: every app, its repo, live URL, stack, and deploy config.
> **Source of truth.** When something changes (new app, new URL, build tweak), update it *here*.
> Last updated: 2026-06-21.

See also: [`BLUEPRINT.md`](./BLUEPRINT.md) (the capability architecture) ·
[`ROADMAP.md`](./ROADMAP.md) (what ships next) · [`DECISIONS.md`](./DECISIONS.md) (the *why*).

---

## Org & accounts
- **GitHub org:** `ARISAN-SIFISO-TECHNOLOGY-EDUCATION` (most repos). A few legacy repos sit under
  the personal account `SifisoScS`.
- **Hosting:** Cloudflare Pages — each app is a Pages project, auto-deploys from `main` on push.
- **Umbrella org:** ARISAN SIFISO Holdings · built by iKhaya AI · supported by The People's Home
  Foundation (NPC).

---

## Apps — World A (offline learning · Cloudflare PWAs)

| App | Pillar | GitHub repo | Live URL | Stack | Build (cmd · output · node) |
|---|---|---|---|---|---|
| **Math Adventure RPG** | Foundations | `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/math-adventure-rpg` | https://math-adventure-rpg.pages.dev/ | React 19 · TS · Vite · Tailwind v4 · Capacitor 8 | `npm run build` · `dist` · 20 (web build flag) |
| **ReadAfrica** | Foundations | `SifisoScS/read-africa` *(private — verify)* | https://read-africa.pages.dev/ | Vite 6 · React 19 · TS · Tailwind v4 | `npm run build` · `dist` · 20 |
| **Science Sprouts** | Curiosity | `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/science-sprouts` | https://science-sprouts-65b.pages.dev/ | React 19 · TS · Vite · Tailwind · Capacitor | `npm run build` · `dist` · 20 |
| **Tech Makers** | Creation | `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/tech-makers` | https://tech-makers.pages.dev/ | Vite 8 · React 19 · TS 6 · Tailwind v4 · Capacitor 8 | `npm run build` · `dist` · 20 · **lockfile gitignored** |
| **SIFISO — Learn Python** | Creation | `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/sifiso-learn-python` | https://sifiso-learn-python.pages.dev/ | CRA (react-scripts 5) · React 19 · Monaco · Pyodide · Tailwind v3 | **`CI=false npm run build`** · `build` · 20 · **lockfile gitignored** |
| **Truth Seekers** | Reasoning | *(not created — next build)* | *(pending)* | Vite · React · TS (scaffold from exam-studio) | *(tbd)* |

**Local checkouts:** `C:\Users\sifis\Next-Level-Projects\{math-adventure-rpg, tech-makers,
sifiso-learn-python, peoples-home}` · `C:\Users\sifis\mobile-projects\science-sprouts`.
ReadAfrica has no permanent local checkout (was a temp audit clone).

### Per-app deploy gotchas (hard-won)
- **Tech Makers & SIFISO:** `package-lock.json` is **gitignored** so Cloudflare uses lenient
  `npm install` instead of `npm ci` (Vite 8 `@emnapi` / CRA dep drift both break `npm ci`).
- **SIFISO:** must build with **`CI=false`** or CRA fails on ESLint warnings; output dir is
  **`build`** (CRA), not `dist`.
- **SIFISO offline:** self-hosts Pyodide (`public/pyodide/`, ~12 MB) + Monaco locally — runs Python
  with no connection.
- **Cloudflare URL trap:** if the bare project name is taken, Cloudflare suffixes it (Science
  Sprouts → `science-sprouts-65b`). Always capture the **actual** `.pages.dev` URL from the dashboard.
- **PWA manifest:** every app needs a **unique manifest `id`** (e.g. `/tech-makers/`, `/sifiso/`)
  or sibling apps installed from the same origin collide.

---

## The umbrella site

| | |
|---|---|
| **Repo** | `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/peoples-home-web` |
| **Local** | `C:\Users\sifis\Next-Level-Projects\peoples-home` |
| **Live** | https://peoples-home-web.pages.dev/ |
| **Stack** | Static HTML + inline CSS, **no build step** (Cloudflare preset None, empty build cmd, output `/`) |
| **Pages** | `index.html` (homepage, 6 pillars) · `partners.html` · `404.html` · this doc set |

---

## World B — Opportunity Infrastructure (different DNA)
| Project | What | Repo / stack |
|---|---|---|
| **iKhaya** | The opportunity layer — jobs/social network, the 6 navigators, mentors/community. Server-backed, accounts, PII, POPIA. 2027 People's Home flagship. | Lovable prototype (~4/10), own backend/stack |
| **iKhaya Learn** | AI-tutored web/coding portal (ages 13–17), freemium, Gemini "Sizwe" | `SifisoScS/ikhaya-learn-reloaded` · React + Express + Gemini |

---

## Critical assets NOT in any repo (back these up off-machine!)
> See [`DECISIONS.md`](./DECISIONS.md) → "Critical-information risk". These are single points of failure.
- **Android signing keystores** (`.jks` + `keystore.properties`) — gitignored, **local-only,
  irreplaceable**. Losing one = can never update that app on Play again.
- **Cloudflare / GitHub / Play Console account access.**
- **The strategy brain** — currently in Claude's local memory + the plan file (being migrated into
  this doc set so it stops being machine-local).
