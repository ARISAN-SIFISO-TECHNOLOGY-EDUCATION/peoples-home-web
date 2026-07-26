# Playbook: Authoring an Educational Record

> The repeatable editorial workflow that turns **Canon 06** from a standard into a process.
> Run this for **every** record before it may enter review — and again, at the review stages,
> before it may be declared complete.
>
> - **Standard (the bar):** [`../architecture/06-educational-record-standard.md`](../architecture/06-educational-record-standard.md) — *when* a record is complete.
> - **Schema (the shape):** [`../architecture/educational-record-schema.md`](../architecture/educational-record-schema.md) — *how* it is structured.
> - **Exemplar (the gold standard):** [`../architecture/exemplar-imhotep.md`](../architecture/exemplar-imhotep.md) — what "complete" reads like.
>
> This is the *how*. It does not restate the standard; it operationalises it (D-13: one owner per rule).
>
> ## 🔑 Operational mantra (D-21): **Authored ≠ trustworthy.**
> A record earns trust through **independent verification**, never through the author's self-confidence.
> Authoring and author self-review are *evidence*; certification is a separate act by a *different person*
> (see [`independent-review-and-verification.md`](./independent-review-and-verification.md)). Applies to
> every record, forever. *(Available for elevation to a PROJECT_DNA principle — a founder act.)*

---

## The pipeline — a record moves through seven stages

```text
  Research  →  Author  →  Self-review  →  Historian review  →  Teacher review  →  Verified  →  Published
  (gather)     (write)    (author)         (independent #1)      (independent #2)    (sources)    (ship)
```

**The stages are not interchangeable, and no stage may stand in for another.** This is the whole
lesson of the Imhotep exemplar: the author self-review found four real overstatements — genuine value —
but a self-review is **evidence, not certification**. An author cannot independently verify their own
work. The two independent reviews (historian, teacher) and source verification are separate gates that
only a *different person* can close.

| Stage | Who | Produces | The state it sets |
|---|---|---|---|
| 1. Research | Author | Real sources gathered, claims noted with citations | — |
| 2. Author | Author | The record, written to the schema | **Authored** ✅ |
| 3. Self-review | Author | Corrections where wording exceeded evidence | **Self-reviewed** ✅ (not certified) |
| 4. Historian review | Independent domain reviewer | Accuracy sign-off, or corrections | **Independently reviewed** ⏳ until done |
| 5. Teacher review | Independent educator | Age-fit + pedagogy sign-off | **Pedagogically reviewed** ⏳ until done |
| 6. Verified | Reviewer with source access | Every `SourceRef.verified` flipped true against the real work | **Sources verified** ⏳ until done |
| 7. Published | Founder | The record goes live | **Complete** — only now |

> A record may sit at **Self-reviewed ✅** for a long time. That is honest and expected. It is *not*
> "complete" — Canon 06 §2 is certified by a reviewer, never inferred from the author's confidence.

---

## Gate A — before a record may enter review (Stages 1–3)

The author checks every item. A record that fails any of these is **not ready for review** — it goes
back to authoring, not forward.

### A1 · Foundation teaches (Canon 06 §2.1, §3 Band 1)
- [ ] The Foundation **is the lesson**, not a summary of a lesson that lives elsewhere.
- [ ] Introduction is written for a learner with **no prior knowledge**.
- [ ] The account tells the actual history or science *properly* — not a description of the subject.
- [ ] Significance is **concrete** (what specifically, not "was important").
- [ ] **Misconceptions are addressed** where any real one exists — stated plainly, then corrected with
      evidence. *(Not optional when a common misconception exists: an institution corrects, it does not
      only assert.)*

### A2 · Context is complete (Canon 06 §2.2, §3 Band 2)
- [ ] The learner understands the **world the subject sits in** — era, place, society — not just its name.
- [ ] The **fields it touches** are named.

### A3 · Connections are educational, not decorative (Canon 06 §2.3, §3 Band 3)
- [ ] Connections are **named and meaningful** ("studied under", "built", "influenced") — an author's
      curated links, **not** the raw output of the app's relatedness mechanism.
- [ ] Temporal placement is set where the subject admits it (signed year: negative = BCE).

### A4 · Exploration lets the learner and a checker go further (Canon 06 §2.4, §3 Band 4)
- [ ] Further reading / museums / references are present and real.
- [ ] Glossary defines the terms **the account itself introduced**, at the intended reading level.

### A5 · Every factual claim is sourced (Canon 06 §5 — non-negotiable)
- [ ] Every claim in Bands 1–3 is a `Claim` with **≥ 1 real source** (publication + title at minimum).
- [ ] **No citation was invented** to satisfy the contract. If a claim cannot be sourced, the claim is
      cut or softened — never propped up with a fabricated reference. *(This is the Phase 0 discipline:
      African Discoveries once shipped a fabricated scholar assembled from plausible unsourced text.)*
- [ ] Every source starts at **`verified: false`** and stays there until Stage 6.

### A6 · Language matches the audience (Canon 03 ages-not-grades)
- [ ] Register fits the declared `ageBands` — ages, never grades.

### A7 · Presence is not completeness (Canon 06 §4 — the negative requirement)
- [ ] The author has **not** treated "has a description + image + achievements + related links" as done.
      Those are inputs. Completeness is certified against §2, never inferred from filled-in fields.

---

## Gate B — the self-review (Stage 3), passage by passage

This is the discipline the Imhotep exemplar proved is worth its cost. For **each passage**, ask two
questions and act:

- [ ] **Is this claim supported by the cited work?** If the source does not actually establish it →
      re-source or cut.
- [ ] **Is the wording stronger than the evidence?** This is where records fail quietly. Watch for:
  - superlatives the source does not support ("*earliest in the world*" → "*earliest we have evidence of*")
  - a settled tone over a contested fact (say "*the evidence suggests*" when it does)
  - collapsing gradual change into an event ("*became*" over centuries, not "*was*")
  - borrowed certainty — a later legend stated as contemporary fact
- [ ] Record the corrections made. The self-review's **output is the edits**, and its honest label is
      *"self-reviewed by the author — independent review still pending."*

> **Gotcha (Imhotep):** the four corrections here were all the author's own overstatements — an
> "earliest stone monument in the world" that should have been "earliest great monument built of cut
> stone", a priesthood conflated with pedestal titles, a deification flattened into an event, a
> "more than a century" that was "roughly a century." Expect to find these in your *own* prose. Finding
> them is the point; not finding any usually means the review was not done properly.

---

## Gate C — the review stages (Stages 4–6): only a different person closes these

- [ ] **Historian / domain review** — an independent reader with subject knowledge confirms accuracy, or
      returns corrections. Closes the accuracy gate; the author cannot.
- [ ] **Teacher review** — an independent educator confirms the record teaches its ages well.
- [ ] **Source verification** — a reviewer with access to the cited works flips each
      `SourceRef.verified` to `true` *against the real source*, and adds the stable URL. Any claim whose
      source cannot be verified goes back — it is not published on trust.

**Until all three are closed, the record is `verified: false` and not complete.** Publishing (Stage 7)
is a founder act.

---

## The four verification boundaries — always state where a record actually is

Carry these honestly on every in-progress record (the exemplar's model). They prevent "looks finished"
from being read as "is verified":

| Boundary | Who can close it | Imhotep exemplar today |
|---|---|---|
| **Authored** | Author | ✅ |
| **Self-reviewed** | Author (evidence, not certification) | ✅ |
| **Independently reviewed** | Historian + teacher (a *different* person) | ⏳ |
| **Sources verified** | Reviewer with source access | ⏳ |

---

## What this playbook deliberately does **not** do

- It does **not** lower the bar to speed up a library. Canon 06 §6: the standard leads; the model — and
  the schedule — follow. A half-verified record is not a fast complete one; it is an incomplete one.
- It does **not** let AI-generated prose count as a record. AI drafting is a research aid at Stage 1–2;
  it does not close any gate and it is never the published content on its own.
- It does **not** define the learner's journey *across* records. One record's depth only (Canon 06 §3, §7).

---

## Notes on cadence (added 2026-07-26)

Authoring a library to this standard is **per-record scholarship**, not a batch operation. The realistic
unit of progress is *one genuinely-sourced record moved to Self-reviewed*, then queued for the two
independent reviews. "Finish the library" is a program measured in reviewed records, not a single
sitting — and the fastest way to betray it is to fill the queue with unsourced prose that looks complete.
Depth over completion, one record at a time. *(Append new cadence notes below as we learn.)*
