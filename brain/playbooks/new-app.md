# Playbook: New World-A Learning App

> Use this when building a new offline learning app for The People's Home.
> Based on the actual process used to build all 10 World-A apps in June 2026.
>
> **Before you start:** Read `brain/PROJECT_DNA.md`. Every decision you make must
> be consistent with the twelve principles. Check the pillar map to confirm there
> is a genuine gap this app fills.

---

## Pre-build decisions (do this first, before writing any code)

### 1. Identify the pillar and the gap

Open `brain/architecture/01-capability-architecture.md` and identify which capability
pillar this app serves. Ask:
- Is this pillar already covered? If yes, is this truly a different capability, or
  should the existing app be deepened instead?
- What specific capability does the learner leave with? (Not "what content does it teach?")

### 2. Identify the audience precisely

- What age range? (Express as ages, not grades — see DNA principle 5)
- Is this for children, teens, adults, or all ages?
- Is voice-first required? (Low literacy audience → yes. See `brain/patterns/voice-first.md`)

### 3. Choose the learning structure

Two proven patterns:

**Journey Progression** (best for: sequential growth, one persistent artifact)
→ Micro Founders, Mzansi Money, SIFISO, Our World
→ See `brain/patterns/journey-progression.md`

**Atelier Chassis** (best for: parallel skills, scenario-response activities)
→ Truth Seekers
→ See `brain/patterns/atelier-chassis.md`

If neither fits: define the new structure explicitly before building.

### 4. Name and URL slug

- Name: meaningful to the learner ("Math Adventure RPG", not "Math App v2")
- URL slug: `<name>.pages.dev` — check availability on Cloudflare Pages first
- GitHub repo name: same as URL slug (e.g., `micro-founders`)
- isiZulu name: consider from the start (harder to add later)

### 5. Check platform features needed

- People's Home Passport? (Yes for most apps — see `brain/architecture/03-tph-core-and-passport.md`)
- Household Mode? (Yes for all-ages and adult apps)
- Google Play? **No.** Web-first only. See `brain/vision/02-delivery-model.md`.
  Exception: only if already granted Play production access (Math Adventure + Science Sprouts).

---

## Build process

### Step 1 — Scaffold

```bash
npm create vite@latest <app-slug> -- --template react-ts
cd <app-slug>
npm install
npm install tailwindcss @tailwindcss/vite
```

Add Tailwind to `vite.config.ts`:
```typescript
import tailwindcss from '@tailwindcss/vite'
export default defineConfig({
  plugins: [react(), tailwindcss()],
})
```

### Step 2 — PWA setup (critical for offline)

```bash
npm install -D vite-plugin-pwa
```

In `vite.config.ts`:
```typescript
import { VitePWA } from 'vite-plugin-pwa'

VitePWA({
  registerType: 'autoUpdate',
  workbox: {
    globPatterns: ['**/*.{js,css,html,ico,png,svg,mp3,webm}'],
    maximumFileSizeToCacheInBytes: 5 * 1024 * 1024, // 5MB
  },
  manifest: {
    name: '<App Full Name>',
    short_name: '<Short Name>',
    description: '<One sentence>',
    theme_color: '<brand colour>',
    background_color: '#ffffff',
    display: 'standalone',
    start_url: '/',
    icons: [
      { src: 'icons/icon-192.png', sizes: '192x192', type: 'image/png' },
      { src: 'icons/icon-512.png', sizes: '512x512', type: 'image/png' },
    ],
  },
})
```

**Gotcha:** `maximumFileSizeToCacheInBytes` defaults to 2MB. SIFISO needs 5MB+ for
Pyodide. Set this explicitly for any app with heavy assets.

### Step 3 — Core structure

```
src/
├── components/     # shared UI components
├── pages/          # one file per screen/stage
├── data/           # content files (bundled at build time, not fetched at runtime)
├── utils/          # progress.ts, passport.ts, narration.ts, storage.ts
├── hooks/          # useProgress(), usePassport(), useNarration()
├── types.ts        # all shared TypeScript types
├── App.tsx         # top-level router
└── main.tsx        # entry point
```

### Step 4 — Progress and Passport

Install or copy the TPH Core SDK patterns:

```typescript
// utils/storage.ts — localStorage with namespacing
const KEY = 'tph-<app-id>'

export function getProgress(): AppProgress {
  const raw = localStorage.getItem(KEY)
  return raw ? JSON.parse(raw) : getDefaultProgress()
}

export function saveProgress(progress: AppProgress): void {
  localStorage.setItem(KEY, JSON.stringify(progress))
}
```

**Gotcha:** Always namespace with `tph-<app-id>`. Apps sharing a device should
never overwrite each other's progress.

### Step 5 — Content bundling

All content must be bundled — no runtime fetches in the learning loop:

```typescript
// data/content.ts
export const STAGES: Stage[] = [
  { id: 'stage-1', title: 'Spot it', ... },
  // ...
]
```

For audio: include `.mp3` or `.webm` files in `/public/audio/` and reference them
as static paths. Workbox will cache them.

### Step 6 — Voice-first (if required)

```typescript
// utils/narration.ts
export function speak(text: string, lang = 'en-ZA'): void {
  if (!window.speechSynthesis) return
  const utterance = new SpeechSynthesisUtterance(text)
  utterance.lang = lang
  utterance.rate = 0.9 // slightly slower for clarity
  speechSynthesis.speak(utterance)
}
```

**Gotcha:** Browsers block autoplay before a user gesture. Wrap the first call
in a `useEffect` that only fires after a `userInteracted` state is set to `true`.

### Step 7 — Offline test before deploying

In Chrome DevTools:
1. Application → Service Workers → confirm registration
2. Network → Offline → reload
3. Verify every core screen loads and functions

If any screen breaks offline: fix before deploying. Not after.

---

## Deploy process

See [`cloudflare-pages.md`](./cloudflare-pages.md) for the complete deploy steps.

---

## Post-ship: update the brain

After the first live deployment:

1. **Create `brain/apps/<app-slug>.md`**
   Use an existing app file (e.g., `brain/apps/micro-founders.md`) as a template.
   Sections: overview, origin, pedagogy, structure, features, audience, status, evolution.

2. **Update `brain/CURRENT_STATE.md`**
   Add the app to the World-A table with its status.

3. **Update `brain/PROJECT_TIMELINE.md`**
   Add the ship date entry.

4. **Update `kilimanjaro/src/knowledge/platform.ts`**
   Add the app entry with correct URL, age range, highlights, audience.
   Add the app detail card to `APP_RESPONSES` in `brain.ts`.
   Add to `buildAppListSections()`.

5. **Update `brain/SESSION_HANDOFF.md`**
   Record what was built and what is next.

---

## Common gotchas (from building 10 apps)

| Gotcha | Fix |
|---|---|
| Service worker not updating in dev | Use Vite's dev server without SW in development; test SW in production build only |
| Audio blocked on iOS | Require a user tap before any audio plays; store `audioUnlocked` in sessionStorage |
| `maximumFileSizeToCacheInBytes` too small | Set to 5MB+ for apps with audio or Pyodide |
| localStorage namespace collision | Always prefix with `tph-<app-slug>-` |
| "Grade N" strings in content | Use ages ("Ages 8–10"). Grep for "Grade" before shipping. |
| Vite import of large JSON bundles | Use `import data from './data.json' assert { type: 'json' }` or dynamic import |
| Cloudflare Pages build fails | Check the build command is `npm run build` and output dir is `dist` |
| isiZulu text without review | Mark as DRAFT; do not ship as if reviewed |
