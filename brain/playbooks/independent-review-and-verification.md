# Playbook: Independent Review & Verification

> **Track B's machine** (D-21) — the counterpart to the authoring playbook, and the process that closes
> the two ⏳ gates every authored record carries. Where
> [`authoring-educational-record.md`](./authoring-educational-record.md) takes a record to
> *authored + self-reviewed*, this takes it the rest of the way: to **Verified**, the only state in which
> a record may reach a child.
>
> ## 🔑 **Authored ≠ trustworthy.** (D-21 mantra)
> A record earns trust through **independent verification, not the author's self-confidence.** Everything
> here rests on one rule: **the reviewer is never the author** (FD-002 lineage — a self-review is evidence,
> not certification).

---

## What this machine does *not* do

It **does not supply the reviewers.** Recruiting a real historian and a real teacher is a **leadership /
founder task** (D-21 Track B, item 3) — this playbook makes that task *concrete* by defining exactly what
we ask of them, but it cannot do it. Naming this honestly is the point: the ceiling on "finish the
catalogue" is **human review capacity**, not authoring throughput.

It also does **not** cover the **real-child play-test** — that is a *separate experiential gate*
([`../patterns/experiential-gates.md`](../patterns/experiential-gates.md)) about whether a child can *use*
the app, not whether a record is *true*. Both are required before launch; they are different gates with
different reviewers. This playbook owns **content verification**; the play-test owns **usability**.

---

## The three certifications (all three must close)

A record is **Verified** only when an independent person has closed each of these. Until then it stays
`verified: false` — correct-by-construction, but not shippable.

### 1 · Historian / domain-expert review — *certifies accuracy*
- **Certifies:** every factual claim is supported; contested points are shown as contested; misconceptions
  are corrected accurately; no wording exceeds the evidence.
- **Receives:** the record, its source list, and — highlighted — the **misconception clarifications** and
  any claim the author flagged as uncertain in the editorial self-review.
- **Returns:** an accuracy sign-off, **or** per-claim corrections. A returned correction sends the claim
  back to authoring; it does not get "argued past."
- **For this domain especially:** a record whose whole purpose is resisting a distortion (Great Zimbabwe's
  colonial myth, Imhotep's romantic legend) *must* be checked by someone other than its author.

### 2 · Teacher / educator review — *certifies it teaches*
- **Certifies:** the record teaches its declared `ageBands` well — register, clarity, and that a learner
  reaches understanding without needing to leave the app (Canon 06 §1).
- **Receives:** the record and its declared age bands.
- **Returns:** a pedagogy sign-off, or notes on reading level, sequencing, and clarity.

### 3 · Source verification — *certifies the citations*
- **Certifies:** each `SourceRef` actually supports the claim it is attached to.
- **Action:** flip `verified: false → true` **against the real work**, and add the stable URL once
  confirmed. Any source that cannot be confirmed sends its claim back — **never** published on trust.
  *(This is the Phase 0 discipline; it also re-checks time-sensitive facts, e.g. IUCN conservation
  statuses, against a live source.)*

---

## The reviewer brief — hand this to a recruited reviewer

*Extract and give verbatim; it is written to be read by someone with zero project context.*

> **You are reviewing an educational record for The People's Home, a free offline learning institution for
> South African children. Your review is what lets us tell a child this record is true. We do not want
> agreement — we want you to find what is wrong.**
>
> **If you are a historian / subject expert**, please, for each section:
> 1. Is every factual statement supported by the cited source?
> 2. Is any wording *stronger than the evidence* (a certainty the sources don't support, a legend told as
>    fact, a gradual change written as an event)?
> 3. Are the "misconceptions" corrected *accurately* — not replaced with a new error?
> 4. Is anything contested presented as settled?
> Return: sign-off, or a list of specific corrections tied to the sentence and the source.
>
> **If you are a teacher / educator**, please:
> 1. Will a learner in the stated age range actually understand this?
> 2. Is the language right for those ages — not too advanced, not condescending?
> 3. Does it *teach the subject*, or merely describe it?
> Return: sign-off, or notes on reading level, order, and clarity.
>
> **You do not need to fix anything.** Finding the problem is the whole job.

---

## The verification ledger — how a record records its state

Every record carries its own status honestly, in its **editorial-review section** (as the three exemplars
do) and in the central tracker below. State is set **only by the person who closed the gate**, never by
the author on their behalf.

| State | Set by | Meaning |
|---|---|---|
| `authored` | Author | Written to Canon 06 |
| `self-reviewed` | Author | Author checked own overstatement (evidence, not certification) |
| `expert-verified` | Historian | Accuracy independently confirmed |
| `teacher-verified` | Teacher | Pedagogy independently confirmed |
| `sources-verified` | Verifier | Every `SourceRef` confirmed; URLs added |
| **`Verified`** | — | **All of the above closed. Only now may it reach a child.** |

---

## Verification tracker — the content library today

| Record | Archetype | Authored | Self-reviewed | Expert | Teacher | Sources |
|---|---|---|---|---|---|---|
| Imhotep | person | ✅ | ✅ | ⏳ | ⏳ | ⏳ |
| Great Zimbabwe | civilisation | ✅ | ✅ | ⏳ | ⏳ | ⏳ |
| The Dolos | innovation | ✅ | ✅ | ⏳ | ⏳ | ⏳ |

**Three records authored; zero Verified.** This is not a failure — it is the machine being honest about
where the backlog sits. Every ⏳ needs a human who does not yet exist in the process. *(Append rows as
records are authored; flip marks only when a real reviewer closes the gate.)*

---

## How this plugs into the launch

The Portfolio Launch Readiness Review (D-17) already names the human gates as the critical path — R2
(child play-tests), R3 (G5/G6 evidence), and the content verification this playbook owns. This machine
converts *one* of those — content verification — from a vague "needs review" into a defined, staffable
process with a ready-to-send brief. The others (play-tests, accessibility/educational evidence on the five
flagships, reviewer recruitment itself) remain **founder / leadership** tasks; this playbook is the
production system's contribution to Track B, not a substitute for those decisions.

---

*Author authors; reviewer certifies; founder recruits and releases. Three roles, deliberately not one.*
