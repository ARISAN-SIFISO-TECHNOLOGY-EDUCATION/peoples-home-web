# Math Adventure RPG — Release Policy

> How the one Math Adventure RPG codebase ships as **two editions** without the web innovation lab
> ever endangering the Google Play release. Established **2026-07-10** (see
> [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) → **D-15**). Reusable as a template for
> every future TPH app that has both a store presence and a web edition.
>
> Live build facts (URLs, versionCodes, build flags) are **operational** →
> [`../../ECOSYSTEM.md`](../../ECOSYSTEM.md). This doc is the *policy*.

---

## One product, two editions

`math-adventure-rpg` is a **single codebase** producing both channels via Capacitor. It is **not**
forked. Only the **experience layer** differs by edition; the educational content is one product.

### Google Play — the Stable / LTS edition
- **Purpose:** a stable, dependable educational release.
- **Allowed:** bug fixes · compliance/policy updates · accessibility · security.
- **Not allowed:** experimental UI · beta systems · unvalidated features.
- Think of it as an **LTS** release: it changes slowly and only for good reasons.

### Web — the Community Edition
- **Purpose:** the innovation platform where new experiences are developed and validated.
- **Allowed:** Living World · Story Theatre · advanced animation · large-screen / keyboard & mouse ·
  community features · experimental UX.
- Successful innovations **graduate** into a future Play release **after validation** (see §
  *Feature graduation* below).

## The Stable Build Principle

> The Play build is an LTS release. **No architectural or web work may change its gameplay, saves,
> progression, content, or UX without explicit founder approval.** Architecture evolves *behind* the
> release, not through it.

This is the non-negotiable safety rule of the two-edition model. (Open: whether to elevate it to a
DNA Principle #19 — a founder act, not yet taken.)

## Mechanism — build profiles, seam-first

One repo, gated by an explicit **profile** rather than a bare `WEB_BUILD` flag:

| `PROFILE` | Base | PWA | Experimental flags | Maps to channel |
|---|---|---|---|---|
| `play-store` (default) | `./` | off | all off (core only) | **Stable (Play)** |
| `community` | `/` | on | on | **Community Edition (Web)** |
| `development` | `/` | on | on | Development / Founder Preview |
| `demo` | `/` | on | curated | Public showcase / Founder Preview |

- **Backward-compatible:** absent/`play-store` reproduces today's Android behaviour byte-for-byte;
  `WEB_BUILD=1` continues to map to the web/community profile so nothing currently building breaks.
- **Seam-first adoption:** introduce `src/platform/` (profiles → `PLATFORM` detection → feature
  flags → adapters) and a `src/web/` feature area **first, moving no existing code**; extract shared
  code into `src/core/` **incrementally later** — one subsystem at a time, by stability
  (utils/types → engines → gameplay → UI last), freeze between. *"No file moves without a reason."*

## Release channels (reusable across TPH)

```
Development → Founder Preview → Community Edition → Stable (Google Play) → Expert-Approved Target
```

- `development`/`demo` profiles serve Development & Founder Preview.
- `community` profile → Community Edition (Cloudflare Pages).
- `play-store` profile → Stable.
- **Expert-Approved** is the quality target a Stable release aims to satisfy.

## Version semantics

Distinguish the editions explicitly so "feature X is on the web but not on Play" is never confusing:

- **Stable (Play):** released semver + Android `versionCode`, e.g. `v1.5.2` — channel **Stable**.
- **Community (Web):** a preview line, e.g. `v2.0-preview` — channel **Innovation**.

## Feature graduation

A Community-Edition feature becomes part of a Stable release only after passing every gate:

```
Community Feature → Founder Review → Child Testing → Accessibility Review →
Performance Review → Promotion Proposal → Play Store Candidate
```

No feature enters a Stable (Play) build until it clears this pipeline **and** the founder approves —
this is what keeps the Community Edition a *structured innovation pipeline*, not a place for
one-off experiments to leak into the LTS release.

## Related

- [`math-adventure-rpg.md`](./math-adventure-rpg.md) — the app memory.
- [`../community-release.md`](../community-release.md) — the presentation model (this is the
  delivery model; the two are companions).
- [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) → D-15, and D-03/D-11 (web-first; Play is
  not our home).
- The repo's own `CLAUDE.md` is the authoritative engineering guide.
