# Session Record — 2026-08-22 · The People's Home goes live, and the first institution opens

> Durable record of what was done and what was found. Factual log; decisions are the
> founder's. Continues [`session-2026-08-17-institutions-pivot-and-deploy-prep.md`](./session-2026-08-17-institutions-pivot-and-deploy-prep.md),
> whose agenda items 1 and 2 are now closed.

---

## 1 · Status at the top

**Both are live, on one Hostinger origin, and both work offline — verified on a real device.**

```
https://peopleshome.ikhaya-ai.com/          The People's Home  (front-door shell)
        └── Foundations  ──────►            /math/   Parallel Rivers Math Engine
```

| | Repo | Commit | State |
|---|---|---|---|
| The People's Home | `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/the-peoples-home` | `cbd45b0` | live, `main` clean |
| Parallel Rivers Math Engine | `SifisoScS/parallel-rivers-math-engine` | `b6adac5` | live, `main` clean |

`deploy/hostinger-peopleshome` was merged to `main` and the branch deleted.

**Correction to a standing assumption.** The engine deploys via **`.htaccess`**, not
Cloudflare `_headers`. The `.pages.dev` pattern throughout [`../ECOSYSTEM.md`](../ECOSYSTEM.md)
and [`../ROADMAP.md`](../ROADMAP.md) describes the **previous** app portfolio. The
2026-08-17 ruling moved The People's Home to Hostinger; host config is Apache from now on.

---

## 2 · What was done

**The People's Home deployed.** `dist/public/` (1.4 MB) dragged into `public_html`.
The subdomain and SSL had existed since 2026-08-17 but `public_html` was never filled — the
URL had been returning 200 with the **Hostinger parking page**, which is easy to misread as
"live". It is now the real shell.

**The Math Engine rebuilt for a subfolder and deployed** to `public_html/math/`.

**The Foundations room wired** to open onto `/math/`. A pillar now carries an optional
`url`; pillars without one keep the existing select-and-read behaviour, so the five unbuilt
rooms stay honest cards rather than becoming dead links. Entering a room no longer marks it
"explored" — progress belongs to the engine, which can observe whether a child learned
something. The house cannot, and should not claim otherwise.

**Both repos documented.** `the-peoples-home` had no README and no deployment notes at all;
it now has both. The engine gained `docs/deployment.md`, referenced from its `AI_CONTEXT.md`.

---

## 3 · Four defects found — and why they matter beyond today

None of these announced itself. In every case the app built cleanly, looked perfect, and
failed silently. They are recorded because **three of the four will recur on every engine
added to the house.**

### 3.1 The offline promise was broken in *both* apps — the same way

A service worker precaches its `APP_SHELL` / `PRECACHE` list. But the JS and CSS that *are*
the app are requested by `index.html` **before the worker has activated and claimed the
page**. They bypass it entirely and are never cached by it.

- The People's Home: `APP_SHELL` contained **zero** references to `/assets/`, and there was
  no `Cache-Control` on them either. Install the app, go offline, and you would get the shell
  HTML with no styles and no JavaScript. `offline.webp` was precached; the app that would
  render it was not.
- Parallel Rivers: same shape, for `_next/static/chunks` — 1.2 MB of a 1.3 MB artifact.

Fixed in both by serving the content-hashed asset paths with an immutable year, so the
**browser HTTP cache** carries them. Safe because both Vite and Next hash filenames: the name
changes when the bytes change.

> **The guarantee now lives in `.htaccess`, not in the apps.** That is honest and it works on
> this host, but it means Law 5 depends on host configuration. The durable fix — precaching
> the hashed chunks in the worker — is **not done** in either app.

**Check this on every new engine.** It is a defect class, not a one-off.

### 3.2 A room at `/math` is outside a worker scoped to `/math/`

The engine's service worker is scoped to `/math/`. A page at **`/math`** — no trailing slash
— is outside that scope, so it is never controlled and offline dies while the app looks
healthy. The framework generated exactly that un-slashed link.

The symptom is worth remembering: `navigator.serviceWorker.ready` has **no timeout**, so the
test suite *stalled indefinitely* rather than failing. A hung run with no output was the only
signal.

Fixed with trailing slashes everywhere. **Links from the house into any room must keep the
trailing slash** — offline, there is no redirect to be had.

### 3.3 The house's SPA catch-all reaches into the rooms

The root `.htaccess` ends in `RewriteRule . /index.html [L]`. A subdirectory only escapes a
parent's rewrite rules **by declaring its own**. Without that, every missing path under
`/math/` served The People's Home's shell **with a 200** — wrong app, no error.

Any room added to `public_html/` needs its own `.htaccess` for this reason alone.

### 3.4 Framework base paths do not cover everything

`basePath` prefixed the framework's own asset URLs and its `<Link>` components, but **not**
page-metadata URLs (manifest, icons) and not hand-written anchors. Those kept pointing at the
domain root — i.e. at the house — and PWA installability broke.

---

## 4 · An incident worth recording

**Dragging files into `public_html` deleted the sibling `math/` folder outright.** The Math
Engine had been verified working; after a routine two-file upload to the root, every path
under `/math/` began returning The People's Home's shell. The folder was simply gone. It was
recreated and re-uploaded; no data was at risk, since the artifact is a build output.

**After any root-level upload, re-check that every room folder still exists.**

Two host-specific traps made this slower to diagnose than it should have been, and both will
mislead again:

1. **A 403 on `.htaccess` does not prove the file exists.** Apache denies any path beginning
   `.ht` whether or not it is there. Prove `.htaccess` is live by checking a header it sets,
   never by the 403. This was mis-read once during the session before being caught.
2. **A missing path returns 200 with the house's shell**, because of the catch-all — so
   "wrong app" and "file absent" look identical. Discriminate by `Content-Type`: `text/html`
   on a request for a `.js` or `.png` means it fell through. Control against a path that
   certainly does not exist.

Hostinger fronts the site with a CDN (`hcdn`); add a cache-busting query when probing.

**Zip-and-extract does not work on this host.** Files are dragged. Re-confirmed.

---

## 5 · Evidence

- Parallel Rivers: **65 E2E checks across 9 suites**, green against the export served at
  `/math`, including every offline assertion.
- Production verified by request: routing and redirects, `Cache-Control` on hashed assets,
  service-worker headers, manifest MIME, gzip, and a real 404 rather than a fall-through.
- Offline verified **on a phone, twice** — once for the house, once for the engine reached
  through the Foundations room.

Full reproducible detail lives with each codebase, not here:
`the-peoples-home/DEPLOYMENT.md` and `parallel-rivers-math-engine/docs/deployment.md`.

---

## 6 · What this does and does not change

**Does not change the launch-readiness finding.** [`launch-readiness-2026-08-09.md`](./launch-readiness-2026-08-09.md)
concluded the gap is **evidential, not technical** — *"Nothing is broken. What is missing is
proof."* Today's work is engineering. It moves no educational evidence. **G6 remains unmet:
no app has been observed with a real child.** Two live URLs are not two pieces of evidence.

**Does close** the 2026-08-17 agenda items 1 (deploy TPH) and 2 (wire the Math Engine behind
Foundations). Item 3, the security discussion, is still open — and now has concrete input:
neither app sets a Content-Security-Policy.

---

## 7 · Open

- **The publication hold.** [`CURRENT_STATE.md`](./CURRENT_STATE.md) carries
  *"do not `git push` until after 2026-08-09"*, and this repo is **19 commits ahead of
  `origin/main`**. That date has passed. Whether to release is the founder's call; nothing
  has been pushed.
- **No CSP on either app.** Parallel Rivers needs Next-specific work — the policy used by the
  Vite apps would break it on load, because Next's bootstrap uses inline script.
- **Neither service worker precaches its own hashed assets** (§3.1).
- **Five of six rooms have no engine.** The house is still a front-door shell.
- **The real-child play-test remains the critical path**, exactly as it was before today.
