# Playbook: Release Packaging

> **The final production artifact.** One **Release Package** per app per launch, so that every reviewer
> decision and every founder approval works from the *same* checklist instead of a bespoke exercise. It
> **packages evidence; it does not close gates.** An app is *release-ready* when Sections 2–5 are evidenced
> and Section 7 is explicitly tracked; Section 6 (G7) is the founder's single decision.
>
> **What it deliberately is not:** the pre-ship DNA/technical checklist ([`review-checklist.md`](./review-checklist.md))
> — that is cited here (Quality Gates), not restated (D-13). This document is the *launch package* around it.

---

## Evidence standard (the same one used all session — D-17)

| Mark | Meaning |
|---|---|
| ✅ **Verified** | Checked this cycle — command run, file read, URL fetched |
| 📄 **Claimed** | Asserted elsewhere, not re-verified |
| ◑ **Partial** | Repository-verifiable portion done; observed / human portion open |
| ⏳ **Open** · ❓ **Unknown** | Outstanding · no evidence either way |

**Rule:** every mark in a Release Package names **where the evidence lives**. A bare ✅ is not evidence.

---

## The Release Package — per-app template

Copy this per app; fill every "evidence" cell.

### 1 · Application identity
| Field | Value |
|---|---|
| Name · Pillar | |
| Repository · visibility | |
| Branch · commit (release candidate) | |
| Live URL (if deployed) | |
| Distribution | Web/PWA · Play (only Math Adventure + Science Sprouts) |

### 2 · Constitutional gates — Community Release §4 *(cited, not restated — [`../community-release.md`](../community-release.md))*
| Gate | Status | Evidence location |
|---|---|---|
| G1 Roadmap frozen | | |
| G2 Architecture frozen | | |
| G3 Production build clean | | |
| G4 Offline verified | | |
| G5 Accessibility reviewed | | |
| G6 Educational review complete | | |
| G7 Founder approval | | *(Section 6)* |

### 3 · Quality gates *(repository-verifiable — the part production can close)*
| Check | Status | Evidence |
|---|---|---|
| TypeScript (`tsc --noEmit`) | | |
| Production build (`npm run build`) | | |
| Accessibility **baseline** (structural) | | Atelier apps → [`../patterns/atelier-accessibility-baseline.md`](../patterns/atelier-accessibility-baseline.md) |
| Automated tests | | *(state honestly — several flagships have none)* |
| Content validation / integrity | | *(e.g. `validate-content.mjs`, `smoke-content.mjs`)* |
| Pre-ship DNA checklist | | [`review-checklist.md`](./review-checklist.md) |

### 4 · Educational gates *(Canon 06 — for apps that make educational-record claims)*
| Check | Status | Evidence |
|---|---|---|
| Canon 06 compliance ([`../architecture/06-educational-record-standard.md`](../architecture/06-educational-record-standard.md)) | | |
| Independent **historian / domain** review | | [`independent-review-and-verification.md`](./independent-review-and-verification.md) |
| Independent **teacher** review | | *(as above)* |
| **Source verification** (`verified:false → true`) | | *(as above)* |
| Child play-testing | | *(experiential — Section 7)* |

### 5 · Distribution readiness
| Item | Status | Evidence |
|---|---|---|
| PWA manifest + icons (192/512) · installable | | |
| Offline service worker caches all assets | | |
| Privacy policy · terms (if published) | | |
| Store metadata · screenshots (Play apps only) | | |
| Deployed commit matches the release candidate | | |

### 6 · Founder approval (G7) — one decision, not a discussion
> **Decision:** ☐ Launch · ☐ Launch with named exceptions · ☐ Hold
> **Signed / dated:** ______
> **Gates accepted as *unevidenced* at launch (named explicitly):** ______
> *(Launching without full evidence is a legitimate founder choice; doing it **silently** is what corrodes
> the governance model — D-17 condition 4.)*

### 7 · Outstanding human gates — *only what no document can close*
List **only** the irreplaceable. Everything else must already be evidenced above. Per
[`../patterns/experiential-gates.md`](../patterns/experiential-gates.md), these are satisfied by observation
and judgement, never by an engineer or an AI working alone. **Authored ≠ trustworthy** (D-21).
- ☐ Independent historian / domain review · ☐ Independent teacher review
- ☐ **Child play-testing** (the standing World-A definition-of-done gate)
- ☐ Observed accessibility (screen-reader · rendered contrast · real-device zoom)
- ☐ Real-device performance validation
- ☐ Founder G7 approval

---

## Portfolio snapshot — the six flagships (2026-07-26)

Consolidated from this session's evidence (D-17 review · G5/G6 sweep · Atelier baseline · verification
tracker). Marks are the *best current evidence*, not a launch verdict.

| App | tsc | Build | Tests | A11y baseline | Educational (Canon 06) | G7 |
|---|---|---|---|---|---|---|
| **Math Adventure RPG** | 📄 | 📄 | 📄 376 | 📄 axe tool | n/a (not a records app) | ⏳ |
| **African Discoveries** | 📄 | 📄 | 📄 170 | ◑ Phase 6 (repo) | ◑ standard adopted; content-model + historian/teacher/source ⏳ | ⏳ |
| **Tech Makers** | ✅ | 📄 | ❌ none | ◑ own-code modest | educator review ⏳ | ⏳ |
| **Truth Seekers** | ✅ | ✅ | ❌ none | ✅ **applied** | educator review ⏳ | ⏳ |
| **Mzansi Money** | ✅ | ✅ | ❌ none | ✅ **applied** | educator review ⏳ | ⏳ |
| **Micro Founders** | ✅ | ✅ | ❌ none | ✅ **applied** | educator review ⏳ | ⏳ |

**What this makes legible:** the repository-verifiable columns are largely green or closeable; the two
right-hand realities — **educational/independent review** and **G7** — are ⏳ for the whole launch face, and
neither is a production task.

### The consolidated Outstanding Human Gates (portfolio)
The complete list of what remains, none of it document-closeable:
1. **Child play-tests** — every World-A app (R2; the single highest-leverage action, per D-17 §9).
2. **Independent educator review** — the true G6, every flagship.
3. **Independent historian + source verification** — African Discoveries content and the three Canon 06
   exemplars (Imhotep · Great Zimbabwe · Dolos), all `verified:false`.
4. **Observed accessibility** — screen-reader / contrast / real device, every app (the baseline is structural).
5. **Real-device performance** — especially African Discoveries (audit never tested a low-end device).
6. **Founder G7 approval** — all six; and the **African Discoveries 9–17 vs fund-3–8 scope decision**.

---

## Where this leaves the programme

With this checklist, **the production side of the launch is complete under the publication hold.** Every
artifact a document *can* produce — the standard, the schema, the playbooks, the validation records, the
readiness review, the verification pipeline, the accessibility baseline, and now the release package — exists.

What remains is Section 7: **independent experts, real children, and founder decisions.** Those were never
production's to close, and the strongest governance choice of this programme was refusing to fake them. The
release package's job is to keep leadership's attention exactly there — on the irreplaceable — and nowhere
else.
