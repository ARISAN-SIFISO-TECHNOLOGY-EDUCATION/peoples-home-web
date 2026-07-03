# Space Explorer

> 🔭 **Curiosity & Knowledge** · ages **3–17** · **✅ LIVE** at
> **https://ikhaya-space-explorer.pages.dev/** — installable offline PWA · linked on The People's Home ·
> brought in-house 2026-07-03

The **third Curiosity & Knowledge app** (after Science Sprouts and Our World). Built externally in
**Google AI Studio (Gemini)**, then brought fully in-house this session — the same path as
[[tph-early-literacy-status]]. Repo: `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/Space-Explorer` (PRIVATE,
branch **`main`**), local `C:\Users\sifis\Next-Level-Projects\space-explorer`.

---

## What it is

A cinematic "spaceport" a child pilots solo — no reading gate, no fail state. Five tabs: **Starport
Home**, **Exploration Map** (regions unlock with progress: Earth → Moon → Solar System → Milky Way →
Deep Space → Future Missions), **Discovery Book / Journal**, **Nova** (companion), **Captain's Log /
Profile**. Progress = **curiosity points** → ranks (Space Cadet → Deep Space Admiral). All state is a
single local profile (`localStorage: tph_space_explorer_profile`). React 19 · Vite 6 · Tailwind v4 ·
lucide-react. The app ships its own design brain in-repo: `brain/apps/space-explorer/01..07` (product
vision, UX, design system, world bible, component library, impl guide, engineering constitution).

## In-house conversion (2026-07-03)

Same playbook as Early Literacy. **No app logic/UI changed.**

- **AI dropped** (commit `cd8e9ce`): removed `@google/genai` + `express` + `dotenv` + `motion` (all
  unused in `src/`), cleared the Gemini capability in `metadata.json`, deleted the AI-only `.env.example`.
- **True offline + no tracking:** removed a **live Google Fonts `@import`** from `index.css` (the app
  literally displays "fully operational offline" — now honoured). Fonts fall back to system stacks;
  self-hosting Inter/Space Grotesk/JetBrains Mono for pixel fidelity is a backlog item. **Zero external
  requests** confirmed by sweep.
- **Offline PWA:** `vite-plugin-pwa` (Workbox precache 14 entries, autoUpdate) + real branded icons
  (dependency-free zlib generator, space theme) + code-split (react/icons/vendor).
- **Deploy prep:** `package.json` name `react-example` → `space-explorer`; `tailwindcss` +
  `vite-plugin-pwa` → `dependencies` (Cloudflare prod-install gotcha); **added `@types/react` +
  `@types/react-dom`** (tsc was hollow — now real, 0 errors); `_redirects`, `wrangler.toml`, real
  `index.html`. **New README** replacing the AI-Studio boilerplate.
- **Security `public/_headers`:** CSP (`script-src 'self'` — build has no inline scripts; `style-src
  'unsafe-inline'` for Tailwind; `worker-src 'self' blob:`) + X-Frame-Options DENY, nosniff,
  no-referrer, Permissions-Policy. `npm audit` = 0 vulns. ErrorBoundary already present (`CoreErrorBoundary`).

## Bug sweep (bug-identifier → bug-fixer, commit `2dad860`)

Same High-severity class as the Early Literacy fix:
- **Unguarded `localStorage.setItem`** in `saveProfile` → Safari Private Mode / quota throws → crash.
  Now try/catch (works in-memory).
- **No default-merge on profile load** → a profile from an older build (missing `createdPlanets` /
  `favoriteIds` / `unlockedRegions`) left arrays undefined; callers read them unguarded
  (`favoriteIds.includes`, `[...createdPlanets]`) → `TypeError`. Now `{...DEFAULT_PROFILE, ...parsed}`.

Verified: `tsc --noEmit` 0 errors; `vite build` clean; `_headers` in `dist/`.

## ✅ Deployed & linked (2026-07-03)

- **LIVE at https://ikhaya-space-explorer.pages.dev/** (the bare `space-explorer.pages.dev` was taken
  by an unrelated "GravityDemo", so the Cloudflare project uses the `ikhaya-space-explorer` subdomain).
  Verified our hardened build is serving (matching bundle hash + CSP headers).
- **Linked on The People's Home** (`peoples-home-web` `06c9e05`): Curiosity pillar entry flipped
  `future` → `live`. Verified present on the site.
- **Play-test:** build/type-verified only; observe a real child before calling it done.

## Related

- [[tph-app-ecosystem]] · [[tph-early-literacy-status]] (the in-house playbook this followed) ·
  [[skills-library]] (bug-identifier/bug-fixer)
- App's own design brain: `space-explorer/brain/apps/space-explorer/01..07`
