# Baselines

> Dated **reference snapshots** of The People's Home as a whole system — the live site
> structure, the flagship set, the release policy, the platform architecture.
>
> **Why:** so future work is measured against a *known* state instead of one reconstructed
> from scattered history. A reviewer should be able to read one baseline and know exactly
> what "before" looked like.
>
> **Protocol:** Append only. A baseline is **immutable once written** — it records what was
> true on its date. Never edit an old baseline to reflect new reality; cut a new one.

---

## What a baseline is *not*

- **Not the live registry.** Current facts live in [`../../ECOSYSTEM.md`](../../ECOSYSTEM.md) and
  [`../../ROADMAP.md`](../../ROADMAP.md). A baseline goes stale *by design*.
- **Not policy.** Governance lives in [`../community-release.md`](../community-release.md) and
  [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md). A baseline *cites* policy, it does not
  set it.
- **Not a changelog.** Per-event history is [`../history/HISTORY.md`](../history/HISTORY.md).

## When to cut a new baseline

At an institutional milestone — a public release, a major architectural shift, or a change to the
flagship set significant enough that "compare against the last baseline" stops being useful.
Cutting one is a **founder act**.

## Versioning

`YYYY.N` — calendar year, then the Nth baseline of that year. `2026.1` is the first.

## Index

- [`2026.1-community-release.md`](./2026.1-community-release.md) — 2026-07-10 · The Community
  Release. Six flagships, three tiers, the Stable Build Principle, the Math Adventure platform seam.
