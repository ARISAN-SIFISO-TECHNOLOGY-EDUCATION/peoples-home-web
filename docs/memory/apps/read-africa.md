# ReadAfrica

> 🧮 **Foundations** · ages **3–17** · **LIVE** (web PWA) ·
> repo `…/read-africa` · https://read-africa.pages.dev/
> The **literacy** half of Foundations — and the current **home of the TPH Core SDK**.

---

## What it is
A literacy app for ages 3–17 — the reading counterpart to Math Adventure's numeracy. Offline,
free, ages-not-grades.

## Why it exists
Literacy is the other half of the **Foundations** floor. With Math Adventure (numeracy) and
ReadAfrica (literacy), a child has both basic-participation capabilities covered, free and offline.

## Original vision
A reading/literacy learning app on the same offline, no-data, SA-first principles as Math Adventure.

## Design iterations / how the thinking evolved
- **It became the platform's seed.** ReadAfrica is where the **TPH Core SDK** was first built and
  embedded — the shared identity/progress/rewards/lore/offline-engine services. That makes ReadAfrica
  quietly the most architecturally important app after Math Adventure: it's the cradle of the platform.

## Architectural decisions (& rejected alternatives)
- **TPH Core embedded here first.** Rather than design the shared platform in the abstract, it was
  grown *inside a real app* (ReadAfrica) and is now slated for **extraction** into a shared package.
  *Rejected:* building a platform package up front with no consumer (it would have been speculative).
- Standard house stack: Vite 6 · React 19 · TS · Tailwind v4.

## Current state
Live web PWA, literacy 3–17. **Hosts the TPH Core SDK (embedded).** No permanent local checkout —
it was cloned temporarily for audit; the canonical copy is the GitHub repo.

## Future direction
The lead platform work — **extract TPH Core from ReadAfrica into a shared package** and adopt it
across apps — runs *through* ReadAfrica. It's the reference for what "shared services" means in
practice. See [`../platform/tph-core.md`](../platform/tph-core.md).

## Related
- [`../platform/tph-core.md`](../platform/tph-core.md) (the SDK it hosts) ·
  [`../canon/05-tph-core-and-passport.md`](../canon/05-tph-core-and-passport.md) ·
  [`math-adventure-rpg.md`](./math-adventure-rpg.md) (its Foundations sibling).
