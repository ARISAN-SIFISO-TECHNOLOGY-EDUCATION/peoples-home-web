# Deploying The People's Home

This is a **static site** (plain HTML/CSS, no build). Any static host works. Below are the three
best options for a South-African / low-connectivity audience, in recommended order.

---

## ⭐ Option 1 — Cloudflare Pages (recommended)

**Why:** free, **unlimited bandwidth**, and one of the fastest global CDNs with strong African
edge presence (Johannesburg, Cape Town, Durban) — so the site loads fast on local networks.
Free custom domain + automatic HTTPS.

1. Push this folder to a GitHub repo (see "Put it on GitHub" below).
2. Go to **dash.cloudflare.com → Workers & Pages → Create → Pages → Connect to Git**.
3. Pick the repo. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/`
4. Deploy. You get `your-project.pages.dev` instantly; add a custom domain under **Custom domains**.

*No GitHub? Use **Direct Upload**: Create → Pages → Upload assets → drag this folder in.*

---

## Option 2 — GitHub Pages (simplest if you already use the ARISAN-SIFISO org)

**Why:** zero extra accounts — you already have GitHub. Free, HTTPS, custom domain supported.

1. Push this folder to a repo (e.g. `ARISAN-SIFISO-TECHNOLOGY-EDUCATION/peoples-home-web`).
2. Repo **Settings → Pages → Source: Deploy from a branch → `main` / root (`/`)**.
3. Site goes live at `https://<org>.github.io/<repo>/`. Add a custom domain in the same panel
   (and a `CNAME` file is created for you).

---

## Option 3 — Netlify

**Why:** the easiest drag-and-drop, generous free tier, instant deploys, form handling if you
later add a "Partner with us" form.

- **Fastest:** go to **app.netlify.com/drop** and drag this folder onto the page. Live in seconds.
- **Git-connected:** New site → import from Git → build command empty, publish directory `/`.

---

## Put it on GitHub (shared first step for Options 1 & 2)

From this folder:

```bash
git init
git add -A
git commit -m "The People's Home website"
git branch -M main
git remote add origin https://github.com/<your-org>/peoples-home-web.git
git push -u origin main
```

*(`git init` + the first commit are already done in this folder — start from `git remote add`.)*

---

## Custom domain

Whichever host you choose, point a domain like **peopleshome.org.za** / **thepeopleshome.africa**
at it (each host's dashboard gives you the exact DNS records). Until then the free
`*.pages.dev` / `*.github.io` / `*.netlify.app` subdomain works fine for sharing.

## Recommendation

**Cloudflare Pages** for the live public site (best reach + unlimited bandwidth for SA traffic),
with the repo mirrored to your **ARISAN-SIFISO GitHub org** so GitHub Pages is a ready fallback.
