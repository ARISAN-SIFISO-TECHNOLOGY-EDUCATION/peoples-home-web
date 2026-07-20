# 05 · Platform Editions & Profiles — the multi-shell model

> **One canonical product, multiple platform shells.** A reusable architecture pattern for any TPH
> app that must ship to more than one target (Google Play, web/PWA, and later desktop / Chromebook /
> classroom) from a **single codebase** — without a fork and without endangering a shipped release.
> Established **2026-07-10**; first implemented in Math Adventure RPG (see
> [`../apps/math-adventure-release-policy.md`](../apps/math-adventure-release-policy.md), D-15).

---

## The idea

Educational content is **one product**; only the **experience layer** changes per target. So keep
one codebase and separate *what runs everywhere* from *what a given shell adds*:

```
shared educational core  (curriculum · game logic · progress · save · TPH Core)
        │
   platform seam         (profiles → PLATFORM detection → feature flags → adapters)
        │
   ┌────┴──────┬───────────┬─────────────┐
 mobile       web        desktop        …          ← shells (editions)
 (Play LTS)  (Community)  (future)
```

## The three seam primitives

1. **Profiles** — a single explicit `PROFILE` (`play-store | community | development | demo`)
   chosen at build time, superseding scattered per-target flags (e.g. bare `WEB_BUILD`). The profile
   fixes base path, PWA on/off, and feature-flag defaults. One knob, not many checks.
2. **`PLATFORM` detection** — a single source of truth (`{ isWeb, isMobile, isDesktop }`) instead of
   raw `Capacitor.isNativePlatform()` calls sprinkled through the code.
3. **Feature flags** — named capabilities (e.g. `storyTheatre`, `livingWorld`, `animations`) gated
   *by profile*, so a shell's extras are additive and never leak into a frozen edition.

## The two disciplines that make it safe

- **Stable Build Principle** — one shell is designated the frozen **LTS** edition (Play). No
  architectural or other-shell work may change its gameplay/saves/progression/content/UX without
  explicit founder approval. Architecture evolves *behind* the release.
- **Seam-first, no big-bang** — introduce the seam (`platform/`) and the innovation shell's feature
  area (`web/`) **first, moving no existing code**; extract shared code into `core/` **incrementally**
  (one subsystem at a time, by stability, freeze between). *"No file moves without a reason."*
  Same clean-boundaries-first discipline as the TPH Core / Passport extraction
  ([`03-tph-core-and-passport.md`](./03-tph-core-and-passport.md)).

## Why it fits TPH

It reconciles two standing decisions: **D-03/D-11** (web-first; Play is not our home) with the
reality that a Play app already exists and has users — Play stays, but only as a frozen LTS shell,
while the web edition becomes where the product evolves. It generalises to every future dual-target
app and gives the ecosystem a path to desktop/Chromebook/classroom shells over the *same* educational
engine.

## Reference implementation & related

- [`../apps/math-adventure-release-policy.md`](../apps/math-adventure-release-policy.md) — editions,
  release channels, version semantics, feature-graduation pipeline (the delivery model).
- [`../community-release.md`](../community-release.md) — the presentation model (which shell/edition
  is *featured* to the community).
- [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) → D-15 (this pattern), D-03/D-11 (web-first).
