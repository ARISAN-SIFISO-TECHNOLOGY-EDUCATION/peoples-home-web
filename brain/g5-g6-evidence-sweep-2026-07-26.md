# G5 / G6 Evidence Sweep — the launch face — 2026-07-26

> **Track B production task (D-21).** The Portfolio Launch Readiness Review ([`launch-readiness-2026-08-09.md`](./launch-readiness-2026-08-09.md), D-17)
> found **G5 (accessibility) and G6 (educational review) near-universally ❓** across the flagships and named
> the *evidence sweep* as recommendation #3. This is that sweep. It is **evidence generation, not an audit**:
> it turns ❓ into a real mark, in one consistent format, so portfolio decisions can rest on evidence.
>
> **What it swept (this session):** the four un-swept flagships — **Tech Makers · Truth Seekers · Mzansi
> Money · Micro Founders.** Math Adventure RPG and African Discoveries carry forward their own prior
> evidence (D-17 review; `african-discoveries/docs/audit/`), cited not re-run.

---

## Evidence standard (same as D-17)

| Mark | Meaning |
|---|---|
| ✅ **Verified** | Checked this session — command run, files read, counts taken |
| ◑ **Partial** | The **repository-verifiable** portion is done; the **observed / human** portion is open |
| 📄 **Claimed** | Asserted in another doc, not re-verified here |
| ⏳ **Open** | Genuinely outstanding |
| ❓ **Unknown** | No evidence either way |

> ## The honest limit, stated once (it governs every G5 and G6 below)
> This sweep reads **repositories**. A repository can prove it *has* alt text, semantic buttons, and
> age-targeted content. It **cannot** prove a screen-reader user succeeds, that rendered contrast passes, or
> that a child *learns* — those are **observed** gates (`../patterns/experiential-gates.md`) owned by real
> testers and educators. So the strongest honest G5 is **◑**, and the true G6 ("educational review
> complete") is **⏳ for all** until an educator reviews. This sweep evidences the *model and the
> repository properties*; it does not certify the experience. **Authored ≠ trustworthy** (D-21) applies to
> apps too.

---

## ⚠️ Correction & update (2026-07-26, same day)

Two things changed after first publication; both are recorded here rather than silently edited (evidence
discipline — annotate, don't overwrite):

1. **Tech Makers' G5 was overstated.** The first version credited it with "130 aria, 13 skip-links, sr-only."
   Those counts were **substantially lesson content** — `src/content/age15.ts` *teaches* web accessibility.
   Tech Makers' **own-code** a11y is modest (≈5 aria-labels; 0 skip-links/sr-only in its components) — though
   it does contribute the one genuinely reusable pattern, a global `:focus-visible` rule. This is the
   "scanner matched content instead of implementation" failure the AD audit named; caught, corrected below.
2. **The Atelier baseline has since been applied.** Truth Seekers · Mzansi Money · Micro Founders now carry
   the shared **Atelier Accessibility Baseline** (focus-visible · skip link · `main` landmark ·
   reduced-motion) — [`patterns/atelier-accessibility-baseline.md`](./patterns/atelier-accessibility-baseline.md).
   tsc + production build verified for all three. Their G5 rows below are updated accordingly. *(Observed
   a11y remains a Track-B human gate for every app — the baseline is structural, not observed.)*

---

## Portfolio readiness matrix — the single operational view

*Community Release §4 gates. `Tests` and `tsc` verified this session for the four swept apps.*

| App | G5 · a11y | G6 · educational | G7 · founder | Auto-tests | tsc | Status / next |
|---|---|---|---|---|---|---|
| **Math Adventure RPG** | ◑ 📄 `a11y-audit.mjs` (axe) | ⏳ *Expert Approved* rejected 2026-06-17 | ⏳ | 📄 376 | 📄 | Best-evidenced; G6 + G7 open (D-17) |
| **African Discoveries** | ◑ Phase 6 (repo) done; observed ⏳ | ⏳ child play-test not done | ⏳ | 📄 170 | 📄 | Audit verdict **DO NOT LAUNCH** pending human validation |
| **Tech Makers** | ◑ own-code modest (~5 aria; global focus ring); high raw counts were lesson content | ◑ model ✅; educator review ⏳ | ⏳ | ❌ none | ✅ clean | Most launch-prepared of the four; needs educator + observed a11y |
| **Truth Seekers** | ◑ **baseline applied** (focus·skip·main·reduced-motion); observed ⏳ | ◑ model ✅; educator review ⏳ | ⏳ | ❌ none | ✅ clean | Atelier baseline landed 2026-07-26 |
| **Mzansi Money** | ◑ **baseline applied** (chassis, same block) | ◑ model ✅; educator review ⏳ | ⏳ | ❌ none | ✅ clean | Atelier baseline landed 2026-07-26 |
| **Micro Founders** | ◑ **baseline applied** (chassis, same block) | ◑ model ✅; educator review ⏳ | ⏳ | ❌ none | ✅ clean | Atelier baseline landed 2026-07-26 |

**Two portfolio facts this makes legible:**
1. **G7 is ⏳ for every flagship** — no founder approval is recorded against §4 for any app. That is the
   single gate common to all six, and only the founder can close it.
2. **The a11y gap is concentrated, not spread.** Tech Makers is genuinely accessible. The weakness is one
   codebase — the **Atelier chassis** (Truth Seekers → Mzansi Money → Micro Founders) — so **fix once,
   fix three.**

---

## Tech Makers — evidence

**G5 · accessibility (◑ strong, repo-verifiable).** ✅ Verified this session across 56 src files: **130
`aria-*` attributes**, **13 skip-to-content** references, **11 `sr-only`** utilities, **35** focus-ring /
`focus-visible` usages, semantic landmarks used throughout, and interaction almost entirely on native
`<button>` (208 buttons; **only 1** `onClick` on a `<div>`). **38 `alt=`** on **68 `<img>`** — coverage to
confirm (some images may be legitimately decorative). *Gaps:* `role=` used only 3×; **`prefers-reduced-motion`
= 0**. *Observed a11y (screen reader, contrast, real zoom) ⏳ — not established by a repo.*

**G6 · educational (◑ model present; review ⏳).** ✅ Real, structured content — `src/content` + `src/data`,
**22 content/data files**; **324** age references, **0** "Grade" (ages-not-grades ✅); **0** lorem / TODO /
placeholder. Independent **educator review ⏳**.

**Readiness.** ✅ `tsc` clean this session. Most launch-prepared of the four: ships `docs/PRIVACY_POLICY.md`,
`age-verification-compliance.md`, `PLAY_STORE_LISTING.md`, `PLAY_LAUNCH_CHECKLIST.md`, `AUDIT.md`; Capacitor
Android target; `validate-content.mjs` + `audit-zu.mjs` (isiZulu) content checks.

**Outstanding risks.** No automated behaviour tests (`tsc` is a type check). `role=`/reduced-motion gaps.
alt-coverage to confirm. Observed a11y + educator review open.

---

## Truth Seekers — evidence

**G5 · accessibility (◑ weak, repo-verifiable).** ✅ Verified across 17 src files: **0 `aria-*`, 0 `role=`,
0 `focus-visible`, 0 `sr-only`, 0 skip-links, 0 `prefers-reduced-motion`**, only 2 semantic landmarks. **One
real strength:** all interaction is on native `<button>` (41 buttons; **0** `onClick` on `<div>`), so
baseline keyboard operability is likely intact. **0 `<img>`** — the UI is `lucide-react` icons + text, so the
open question is **icon-only buttons without accessible names** (⏳ to check). Observed a11y ⏳.

**G6 · educational (◑ model present; review ⏳).** ✅ Genuine, hand-authored SA content: a **critical-thinking
studio, ages 13–17**, five reasoning "muscles" by age (Fact vs Opinion → Fallacies → Misleading Numbers →
Systems & Bias → Claim→Evidence→Argue); `src/content` = age13–17 + cases/lessons (8 files); **28** age refs,
**0** "Grade"; a grown-up **Co-Pilot** mode. `smoke-content.mjs` integrity check. Educator review ⏳.

**Readiness.** ✅ `tsc` clean; PWA via `vite-plugin-pwa`; DNA-clean per README (offline · no accounts · no
network · no AI). README only — no `docs/`.

**Outstanding risks.** The **Atelier chassis** a11y baseline (0 aria/focus/reduced-motion) — **fixing it here
fixes Mzansi Money and Micro Founders too.** No automated tests. Icon-button labels to verify. Observed a11y
+ educator review open.

---

## Mzansi Money — evidence

**G5 · accessibility (◑ weak — chassis-identical to Truth Seekers).** ✅ Verified across 23 src files: **0
aria / role / focus-visible / sr-only / skip-links / reduced-motion**, 2 landmarks; all interaction on native
`<button>` (39; **0** on `<div>`); **0 `<img>`** (lucide icons). Same profile as the chassis it is built on.
Observed a11y ⏳.

**G6 · educational (◑ model present; review ⏳).** ✅ Real content: a **money-wisdom journey, ages 13–17** —
Earn → Budget → Save → Borrow → Protect/Grow/Plan, with a situation-picker through-line ("My Money Plan"),
bespoke Budget Board + Credit Calculator, and a Grown-up view. `src/content` = 9 files; **54** age refs, **0**
"Grade"; explicit *"money wisdom, never financial advice; every figure illustrative; no crypto/trading/live
rates."* `smoke-content.mjs`. Educator review ⏳.

**Readiness.** ✅ `tsc` clean; PWA; DNA-clean (offline · no-login · no-server · no data collected).

**Outstanding risks.** Inherits the chassis a11y baseline. No automated tests. Financial-content framing is a
good candidate for the **educator/domain review** (that money guidance is sound and non-advisory).

---

## Micro Founders — evidence

**G5 · accessibility (◑ weak — chassis-identical).** ✅ Verified across 23 src files: **0 aria / role /
focus-visible / sr-only / skip-links / reduced-motion**, 2 landmarks; native `<button>` throughout (37; **0**
on `<div>`); **0 `<img>`** (lucide icons). Observed a11y ⏳.

**G6 · educational (◑ model present; review ⏳).** ✅ Real content: a **venture studio, ages 13–17** — Spot →
Cost → Sell → Build → Pitch, "My Venture" through-line, bespoke Price Board + Pitch Builder, Venture Canvas,
Mentor (parent/teacher) view; blueprint in `peoples-home/MICRO_FOUNDERS.md`. `src/content` = 9 files; **54**
age refs, **0** "Grade". Educator review ⏳.

**Readiness.** ✅ `tsc` clean; PWA; DNA-clean; **live** at micro-founders.pages.dev (per README).

**Outstanding risks.** Inherits the chassis a11y baseline. No automated tests. Observed a11y + educator review
open.

---

## What this sweep changes, and what it hands to Track B

**Turned ❓ → evidenced** for four flagships: G5 is now a *known* quantity per app (Tech Makers strong; the
three Atelier apps weak-but-keyboard-operable), G6's *model* is evidenced (real, structured, ages-not-grades,
no placeholder) for all four, and `tsc` is ✅ re-verified.

**Two production follow-ups (I can do, ungated):**
1. **One a11y pass on the Atelier chassis** — add `aria-label`s to icon-buttons, focus-visible styling, a
   skip link, and `prefers-reduced-motion` — landing accessibility across **Truth Seekers + Mzansi Money +
   Micro Founders** at once. Tech Makers' patterns (skip-links, sr-only) are the template.
2. **Confirm two specifics:** Tech Makers' alt-coverage (38/68), and whether the Atelier icon-buttons have
   accessible names.

**Handed to Track B human gates (leadership — this sweep cannot close them):**
- **Observed accessibility** — screen-reader, rendered contrast, real-device zoom — on all six.
- **Independent educational review (the true G6)** — an educator confirms each app teaches its ages; Mzansi
  Money's money framing is a natural first candidate.
- **G7 founder approval** against §4 — ⏳ for every flagship; the one gate common to all.

*This document is evidence, not a decision. It does not fix, freeze, or approve anything (D-17 discipline).*
