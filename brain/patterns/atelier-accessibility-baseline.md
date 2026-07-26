# Pattern: Atelier Accessibility Baseline

> The minimum accessibility contract shared by the three apps that inherit the **Atelier shell**:
> **Truth Seekers · Mzansi Money · Micro Founders.** Established 2026-07-26 from the G5/G6 evidence sweep,
> which found all three shared a near-identical accessibility gap *because they share a shell lineage*.
>
> **Governance rule (founder, 2026-07-26):**
> > **Accessibility improvements are made in the Atelier chassis first, then in individual Atelier apps.**
> One canonical educational standard, one schema, one verification pipeline — and now **one accessibility
> baseline.** It stops accessibility from fragmenting across the portfolio.

---

## What "the chassis" means here (precise, to avoid overclaiming)

[`atelier-chassis.md`](./atelier-chassis.md) records the *engine-level* history: Truth Seekers became
"reasoning-native" and Micro Founders rejected the **generic reasoning engine**. That is still true. **This
pattern is about a different, real thing:** the three apps share a **visual shell lineage** — the Atelier
device-chrome, an identical `index.css`, and an identical `App.tsx` shell (`<header>` → `<main class="flex-1
…">` → `<footer>`, a decorative grain layer, the cream palette). Verified 2026-07-26: their `index.css`
files were **byte-identical** and their shells structurally identical.

There is **no shared npm package** — they are three separate repos. So "fix once, fix three" is enforced by
**convention, not import**: the baseline blocks are kept identical across the three, and a change to the
baseline is a change to all three. The CSS block carries a header comment pointing back to this file.

---

## The baseline contract

| # | Requirement | Status (2026-07-26) | Where |
|---|---|---|---|
| 1 | **Visible keyboard focus** (`:focus-visible` ring) | ✅ done | `index.css` (ported verbatim from **Tech Makers** — the reference for this one pattern) |
| 2 | **Skip link** to main content, first focusable element | ✅ done | `.skip-link` in `index.css` + `<a href="#main-content">` first child in `App.tsx` |
| 3 | **`<main id="main-content">`** focusable landmark to skip to | ✅ done | `App.tsx` (`tabIndex={-1}`) |
| 4 | **Respect `prefers-reduced-motion`** | ✅ done | `@media (prefers-reduced-motion: reduce)` in `index.css` |
| 5 | **Landmark structure** (`header`/`main`/`footer`) | ✅ already present | pre-existing in all three shells |
| 6 | **Accessible names for icon-only buttons** (`aria-label`) | ◑ n/a → verify | sweep found **~0** icon-only buttons (apps use text+icon buttons); no action needed beyond a confirming pass |
| 7 | **Keyboard navigation unchanged after the pass** | ✅ additive only | all changes are additive (a link, an id, CSS); no handler or tab-order change. tsc + production build pass for all three |

**And then stop.** This is a *baseline*, not an open-ended accessibility programme (founder instruction). It
removes the one common structural gap the evidence sweep found. Deeper, per-app work (e.g. `aria-pressed` on
the mode toggles, dialog/menu semantics if any are added later) is deliberately **out of scope** here.

---

## The honest limit (what this baseline does NOT establish)

Everything above is **repository-verifiable**. None of it proves the *observed* experience:

- that the focus ring has sufficient **rendered contrast** on every surface (the ring is `#f97316`; contrast
  against each app's cream/indigo/green surfaces is **⏳ unverified by observation**);
- that a **screen-reader** user succeeds end to end;
- that **reduced-motion** visibly calms the real animations on a device.

These are **observed accessibility** — a **Track B human gate** (`experiential-gates.md`), owned by a real
tester, not a repo. **Authored ≠ trustworthy** (D-21) applies to accessibility too: the baseline makes the
apps *structurally* accessible; a human still has to confirm they *are* accessible.

---

## Provenance note — a correction this pass forced

The G5/G6 sweep first credited Tech Makers with "130 aria-attributes, 13 skip-links." On inspection those
counts were **substantially lesson content** — `tech-makers/src/content/age15.ts` literally *teaches* web
accessibility ("Skip to main content" is a lesson). Tech Makers' **own-code** a11y is modest (≈5 aria-labels;
0 skip-links/sr-only in its components) — but it does contribute the **one genuinely reusable pattern**, the
global `:focus-visible` rule, which is what was ported here. The sweep has been corrected
([`../g5-g6-evidence-sweep-2026-07-26.md`](../g5-g6-evidence-sweep-2026-07-26.md)). This is the exact
"scanner matched content instead of implementation" failure the African Discoveries audit named — caught and
corrected, not buried.

---

## Rule for the next contributor

1. **Change the baseline in all three, together, or not at all.** Keep the `index.css` block and the
   `App.tsx` skip-link/`main` identical. Divergence is the failure this pattern exists to prevent.
2. **Reference, don't fork.** If a fourth app joins the Atelier shell, it inherits this baseline verbatim.
3. **Observed a11y is a separate gate.** Do not mark these apps "accessible" on the strength of this pattern;
   that word is earned only after the human review in `experiential-gates.md`.
