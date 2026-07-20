# The Community Release Constitution

> The permanent operating model for how The People's Home presents itself to the community:
> which apps lead, how an app **earns** a flagship slot, how it may be **demoted**, and the
> cadence and review process behind it. Established **2026-07-10** (see
> [`decisions/DECISIONS.md`](./decisions/DECISIONS.md) → **D-14**, **D-15**).
>
> This is a **governance document**, not a live registry. Which apps are live *right now* is an
> **operational fact** → [`../ECOSYSTEM.md`](../ECOSYSTEM.md) / [`../ROADMAP.md`](../ROADMAP.md).
> When the two disagree about a current fact, the operational layer wins, then reconcile here.

---

## 1. Purpose

The **Community Release** is The People's Home's deliberate public debut: a *curated* front door,
not a full catalogue. Its job is to give a first-time visitor a **focused, high-quality first
impression** and to make the ecosystem legible as *"an expanding educational world"* rather than a
list of apps in varying states of completion.

This exists because breadth was working against us: 14 live cards is a *backlog on display*.
Curation is the **presentation-layer companion** to the build-layer discipline of **D-01**
(module-over-new-app / don't proliferate): *fewer things shown, not fewer things built.*

## 2. Flagship selection philosophy

- **One flagship per pillar.** Each of the six capability pillars is represented by exactly one
  **Available Today** app — its strongest current ambassador. Six flagships, one story per pillar.
- **The narrative matters.** The six should read as a journey:
  `Learn Mathematics → Discover Africa → Create Technology → Think Critically → Manage Money →
  Build a Business.`
- **Depth over breadth.** A pillar is better served by one polished flagship than several
  half-polished cards. Everything else stays **listed** (never hidden) as roadmap.
- **The founding six (2026-07-10):** Math Adventure RPG · African Discoveries · Tech Makers ·
  Truth Seekers · Mzansi Money · Micro Founders.

## 3. The three tiers

Every app on the site sits in exactly one tier. Tier = the app's `status` field in the `PILLARS`
data of [`../index.html`](../index.html); this is the **only** control and it is fully reversible.

| Tier | `status` | Badge | Meaning |
|---|---|---|---|
| 🌟 **Available Today** | `live` | **NOW** | Flagship. Clickable, playable now. |
| 🏗 **Currently Growing** | `growing` | **BUILDING** | Actively being built toward its best self. |
| 🌱 **Future Collection** | `future` | **NEXT** | On the roadmap; inspiring copy, not yet featured. |

*Note:* several **Future Collection** apps (e.g. ReadAfrica, Science Sprouts, Our World, Space
Explorer, The Golden Hand) are in fact **built and live** at their own URLs — they are
*de-emphasised on the showcase, not un-shipped*. Their URLs remain in the data so re-promotion is a
one-field flip.

## 4. Promotion criteria — how an app earns *Available Today*

An app may move `growing`/`future` → `live` **only** when **all** of these hold:

1. **Roadmap frozen** — its product roadmap is complete and founder-frozen.
2. **Architecture frozen** — no in-flight structural churn.
3. **Production build clean** — `tsc`/lint/build green, deployed and verified.
4. **Offline verified** — installable PWA, no runtime network calls (incognito-checked).
5. **Accessibility reviewed** — ≥44×44px targets, WCAG AA, works on low-end Android.
6. **Educational review complete** — the learning experience is sound for its ages.
7. **Founder approval** — the explicit, final gate.

Only then is the flagship slot earned. (This mirrors the app "definition of done" in
[`vision/01-product-rules.md`](./vision/01-product-rules.md), raised to a *flagship* bar.)

## 5. Demotion criteria

Demotion (`live` → `growing`/`future`) is a **founder decision**, always reversible, used when an
app no longer meets the flagship bar or is deliberately pulled back for rework. Precedent: **Early
Numeracy** was pulled to not-live for a UI rework (2026-07-06) while staying **listed** — the model
this Constitution generalises. Demotion never deletes the card or the app.

## 6. Release cadence

- The **live set changes deliberately**, not continuously — promotion/demotion are events, each with
  a dated note (operational docs + the app's `apps/*.md`), not silent edits.
- The **default posture is stability**: the community should experience a steady front door. Expand
  the flagship set only when a *Currently Growing* app genuinely clears §4 (e.g. the planned
  **Foundations Collection** once Number Kingdom + Early Literacy reach polish — see D-14).

## 7. Review process

1. A *Currently Growing* app's owner proposes promotion, evidencing §4 (build/offline/a11y/edu).
2. Founder review against the promotion criteria.
3. On approval: flip `status` in `../index.html`; reconcile `../ECOSYSTEM.md` / `../ROADMAP.md`;
   append a dated note to the app's `apps/*.md`, `CURRENT_STATE.md`, `PROJECT_TIMELINE.md` (per
   [`UPDATE_PROTOCOL.md`](./UPDATE_PROTOCOL.md)).
4. Incognito-verify the live card before considering it done.

## 8. Related

- [`baselines/2026.1-community-release.md`](./baselines/2026.1-community-release.md) — the **reference
  snapshot** of the state this Constitution first governed (2026-07-10). Compare against it.
- [`decisions/DECISIONS.md`](./decisions/DECISIONS.md) → D-14 (curation), D-15 (dual-edition).
- [`apps/math-adventure-release-policy.md`](./apps/math-adventure-release-policy.md) — the
  edition/channel/version/graduation model (the delivery companion to this presentation model).
- [`vision/01-product-rules.md`](./vision/01-product-rules.md) — the app definition-of-done.
- Operational live set: [`../ECOSYSTEM.md`](../ECOSYSTEM.md), [`../ROADMAP.md`](../ROADMAP.md).
