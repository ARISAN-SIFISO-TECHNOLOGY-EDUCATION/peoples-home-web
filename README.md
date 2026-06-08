# The People's Home — website

The public site for **The People's Home**, a Sovereign Learning System by **iKhaya AI** (an
ARISAN SIFISO Holdings initiative). A complete learning journey from childhood to opportunity.

> *Technology should empower society — not gatekeep it.*

## Pages

| File | Purpose |
|------|---------|
| `index.html` | **Public homepage** — mission first: hero, the six capability pillars, "The Missing Piece" (why Opportunity Hub is essential), shared connectors, the complete-vision blueprint, mission. Company names appear only in the footer/blueprint. |
| `partners.html` | **Institutional Architecture (v3)** — the partner/investor view: ARISAN SIFISO Holdings and its four divisions (Media Group · iKhaya AI · The People's Home · The Foundation NPC), the learning system expanded, and Foundation programmes. |
| `404.html` | Fallback page. |

## Stack

Pure static HTML + inline CSS — **no build step, no dependencies**. Fonts load from Google Fonts
(Fraunces + Hanken Grotesk); everything else is self-contained, including the hand-built SVG
"sunrise over the home" hero. Works offline once the fonts are cached.

## Run locally

Just open `index.html` in a browser. Or serve the folder:

```bash
npx serve .        # or: python -m http.server 8000
```

## Deploy

This is a static site — drop the folder on any static host. See `DEPLOY.md` for the
recommended options (Cloudflare Pages / GitHub Pages / Netlify).

## The six pillars

🧮 Foundations · 🌱 Curiosity & Knowledge · 🔧 Creation & Technology ·
🧠 Thinking & Reasoning · 💰 Money & Opportunity · 🚀 Real-World Empowerment

Carried end-to-end by shared rails: Identity · Progress · Rewards · Lore · Offline Engine · Parent Dashboard.

---

Built by **iKhaya AI** · An **ARISAN SIFISO Holdings** Initiative · Supported by **The People's Home Foundation** (NPC)
