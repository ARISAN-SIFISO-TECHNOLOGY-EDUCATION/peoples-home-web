# Playbook: Cloudflare Pages Deployment

> The standard deploy path for every World-A learning app.
> Offline PWAs. Global CDN. Free tier. No server.
>
> All 10 World-A apps use this pattern as of 2026-06-27.

---

## Standard setup (new project)

### 1. GitHub repo first

Create the repo in the `ARISAN-SIFISO-TECHNOLOGY-EDUCATION` org (private).
Push the initial code to `main`.

### 2. Connect to Cloudflare Pages

1. Login to Cloudflare Dashboard → **Workers & Pages** → **Create application**
2. Select **Pages** → **Connect to Git**
3. Choose the GitHub org: `ARISAN-SIFISO-TECHNOLOGY-EDUCATION`
4. Select the repo
5. Configure build:

| Setting | Value |
|---|---|
| Framework preset | None (or Vite) |
| Build command | `npm run build` |
| Build output directory | `dist` |
| Root directory | `/` (leave blank) |
| Node.js version | 18 or 20 |

6. Click **Save and Deploy**

**Gotcha:** If the build fails with a Node version error, set `NODE_VERSION=20` in
Cloudflare Pages → Settings → Environment Variables.

### 3. Custom name

After first deploy:
- Pages → your-project → Custom domains → No custom domain needed
- The project name becomes `<project-name>.pages.dev`
- Choose the name carefully — this is the permanent URL

### 4. Autodeploy

By default, every push to `main` triggers a new deploy. This is correct behaviour.
Preview deploys are created for other branches — useful for testing.

---

## Updating an existing app

```bash
# Make changes locally
git add .
git commit -m "feat: ..."
git push origin main
```

Cloudflare picks it up automatically. Check the deploy status at:
`https://dash.cloudflare.com/ → Workers & Pages → <project>`

A deploy typically takes 1–3 minutes.

**To check it's live:** open the `.pages.dev` URL in an incognito window (to bypass cache).

---

## Verifying offline works after deploy

1. Open the app URL in Chrome
2. Wait for the service worker to install (check DevTools → Application → Service Workers)
3. DevTools → Network → check "Offline"
4. Hard refresh (Ctrl+Shift+R)
5. All core screens must load

If something is broken offline, check:
- The failing asset is listed in the workbox `globPatterns`
- The asset is in the `dist/` folder (not fetched at runtime)
- `maximumFileSizeToCacheInBytes` is high enough for large assets

---

## Environment variables

Cloudflare Pages supports env vars at: Pages → Settings → Environment variables

World-A apps should need zero env vars (they are static, offline PWAs).
If you find yourself adding an API key to a World-A app, that is a DNA violation —
the app is no longer truly offline-first.

---

## Rollback

If a deploy is broken:
1. Pages → Deployments → find the last good deploy
2. Click the three-dot menu → **Rollback to this deployment**
3. Instant rollback — no rebuild needed

---

## URL patterns in this project

| App | URL |
|---|---|
| Math Adventure RPG | math-adventure-rpg.pages.dev |
| ReadAfrica | read-africa.pages.dev |
| Everyday Foundations | everyday-foundations.pages.dev |
| Science Sprouts | science-sprouts-65b.pages.dev |
| Our World | our-world-b0t.pages.dev |
| Tech Makers | tech-makers.pages.dev |
| SIFISO — The Golden Hand | sifiso-learn-python.pages.dev |
| Truth Seekers | truth-seekers.pages.dev |
| Micro Founders | micro-founders.pages.dev |
| Mzansi Money | mzansi-money.pages.dev |
| People's Home website | peoples-home-web.pages.dev |

**Note on naming:** Some slugs have suffixes (`-65b`, `-b0t`, `sifiso-learn-python`)
because the preferred name was taken. Choose project names early and carefully.

---

## Gotchas

| Gotcha | Fix |
|---|---|
| Vite build outputs to `dist/` by default | Cloudflare Pages output dir should be `dist` |
| Large files (Pyodide, audio) hit cache limits | Set `maximumFileSizeToCacheInBytes` in workbox config |
| Service worker cached old version | Hard refresh in incognito; or clear site data in DevTools |
| Deploy shows "Build failed" | Check the Cloudflare build logs; usually a missing dependency or wrong Node version |
| `pages.dev` URL shows old content | Force refresh; CDN propagation usually takes < 1 min |
| 404 on page refresh (SPA routing) | Add a `public/_redirects` file: `/* /index.html 200` |
