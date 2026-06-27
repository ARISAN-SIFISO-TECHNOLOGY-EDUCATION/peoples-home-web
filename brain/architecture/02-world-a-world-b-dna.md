# Canon 02 — The World A / World B DNA Split

> **The single most important architectural idea in the whole project.** If you internalise one
> thing, make it this. It decides where every feature lives, what it's allowed to do, and how it's
> funded.

---

## The split

There are **two engineering worlds, and they never mix.**

| | **World A — Offline Learning** | **World B — Opportunity Infrastructure** |
|---|---|---|
| Examples | Math Adventure, ReadAfrica, Truth Seekers | Jobs, mentors, funding, community |
| Login | none | accounts / profiles |
| Server | none | yes |
| Data | no tracking, on-device | relationships, PII, POPIA, moderation |
| Internet | not required | required |
| Cost | ~zero marginal (static hosting) | running backend cost |
| Status | **our proven strength** | a different engineering problem (= **iKhaya**) |

- **World A** = the learning apps. Offline, no login, no server, no tracking, **#FreeForever**.
  Static PWAs on Cloudflare Pages. This is the proven, repeatable competence.
- **World B** = everything that needs accounts, profiles, relationships, notifications, POPIA,
  and moderation. **It all lives inside one platform: iKhaya.** Never as standalone offline apps.

> **Why they must not mix:** the moment a learning app needs a login or a server, it inherits
> World B's cost, privacy risk, and POPIA obligations — and breaks the free/offline/no-data promise
> that *is* the product. Keeping the worlds separate keeps the learning side pure and cheap, and
> contains all the hard infrastructure/trust problems in one place.

---

## "The bridge" — how the worlds connect

Two pillars **span both worlds**: **Money (6)** and **Empowerment (5)**.

```
   WORLD A (offline app)            "the bridge"            WORLD B (iKhaya)
   teaches the capability    ───────── hands off ─────────▶  connects to real opportunity
   free, forever                                              (jobs, funding, mentors)
```

- **Mzansi Money** teaches financial literacy offline → hands off to iKhaya's **Opportunity Hub**
  (the 6 navigators: University · TVET · Bursary · Career · Learnership · Internship, + Side Hustle
  Hub · Tender Starter · Funding Finder · Freelancer Toolkit).
- **Micro Founders** teaches venture-building offline → hands off to iKhaya's **Community & Mentor
  Services** (mentors, communities, cooperatives, civic action, impact tracking).

> The offline app teaches the capability **for free, forever**; iKhaya is where a *ready* learner
> **connects to real opportunity**. That clean seam is the whole *"education → pathway"* thesis.

---

## World B is one platform, not many apps

Everything server-backed lives **inside iKhaya**:
- **Opportunity Hub** — navigators + job/funding/hustle surfaces.
- **Community & Mentor Services** — mentors, communities, cooperatives, civic action, impact.

The six navigators are **in-app sections** of iKhaya, *not* six separate apps. (Same
module-over-new-app discipline as World A — see [`01-capability-architecture.md`](./01-capability-architecture.md).)

---

## The funding consequence (#FreeForever's one fork)

World A is ~free to run (static hosting). **World B carries a real backend cost.** That makes iKhaya
**the one place "free forever" needs a sustainability answer** — the *#FreeForever funding fork*.
It must be resolved **before iKhaya's 2027 flagship launch**. Candidate answers explored: Azure /
Microsoft-for-Startups credits, freemium on the opportunity side, Foundation/grant support.

See [`../platform/ikhaya.md`](../platform/ikhaya.md) and [`03-product-rules.md`](./03-product-rules.md).

---

## Related
- [`01-capability-architecture.md`](./01-capability-architecture.md) — where this split sits in the whole.
- [`../platform/ikhaya.md`](../platform/ikhaya.md) — World B, in depth.
- [`03-product-rules.md`](./03-product-rules.md) — the rules World A must never break.
