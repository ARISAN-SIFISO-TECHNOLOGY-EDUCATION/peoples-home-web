# Canon 06 — The Educational Record Standard

> **Adopted 2026-07-24 (World A canon).** Founder ruling → [`../decisions/DECISIONS.md`](../decisions/DECISIONS.md) **D-20**.
> **Owner:** World A. **First implementation:** African Discoveries.
>
> Subject-agnostic by construction. The worked examples are from African Discoveries because it is the
> first implementation, but the principle, definition, and requirements hold for **any** World A
> educational record — Imhotep or photosynthesis, the Kingdom of Mali or fractions, Python or astronomy.

> ## No educational record may claim completeness unless it satisfies this standard.

This is the question it answers: **not "what should a record contain?" but "when may an educational
record be declared complete?"** It applies to **World A learning apps** and complements the
non-negotiables in [`../vision/01-product-rules.md`](../vision/01-product-rules.md) (Canon 03).

---

## 1. Educational Principle

> **The objective of an educational record is understanding, not completion.**
>
> A record is complete when it enables a learner to achieve meaningful understanding of the subject
> **without needing to leave the application for essential knowledge.**
>
> Reading time, word count, and screen count are not quality measures. **Educational completeness is.**

This principle is the lens through which every requirement below is read. The People's Home is an
education institution, not a feed: it optimises for **understanding, not completion**. If genuine
understanding of a subject takes fifteen minutes, fifteen minutes is correct. This is the World A
statement of *"technology should empower, not gatekeep"* applied to content itself.

---

## 2. Definition of Completeness

A record **may not be declared complete** unless it satisfies **all** of the following. These are the
objective acceptance criteria a reviewer evaluates:

1. **It explains the subject accurately** — plainly enough for a first encounter, correct enough to
   withstand scrutiny.
2. **It provides sufficient historical or scientific context** — the learner understands the world the
   subject sits in, not only its name.
3. **It connects the subject to wider knowledge** — the record is a node in a network, not an isolated
   card. *(In African Discoveries this is "wider African knowledge"; each app scopes the network to its
   domain.)*
4. **It enables further exploration through verified references** — the learner can go deeper, and a
   parent or teacher can check the claims.

These four map one-to-one onto the four bands in §3: the bands are *how* an author satisfies them, this
list is *what* a reviewer certifies. A record that reads well but fails any one is **not complete** — it
is in progress.

---

## 3. The Four Bands — editorial requirements

**Requirements for authors, not screens for users.** They describe the content a record must *contain*
to be complete; how it is presented to a learner is a separate UI concern. Depth of **understanding**,
not length. This standard owns the **depth** axis of a single record only — the learner's *journey
across* records is a separate concern, deliberately not defined here (§6).

### Band 1 — Foundation · *the lesson itself*
The substance — not a summary of a lesson elsewhere; this **is** the lesson. Satisfies criterion 1.
- **Introduction** — who/what, for a learner with no prior knowledge.
- **The account** — the actual history or science, told properly.
- **Achievements / significance** — concretely.
- **Why it matters** — then, and now.
- **Misconceptions & clarifications** — an education institution corrects misunderstanding, it does not
  only assert facts. State the common misconception and the evidenced correction. *(Imhotep: "only a
  legendary figure" → contemporary inscriptions identify a real official under Djoser. Great Zimbabwe:
  "built by Europeans" → archaeology overwhelmingly attributes it to ancestors of the Shona people.)*
  Each clarification is a sourced claim like any other (§5).
- *Interesting facts* — optional, only if they teach.

### Band 2 — Context · *the subject's world*
Widen from subject to surroundings. Satisfies criterion 2.
- **The world around it** — era, place, society.
- **The fields it touches** — the domains it reaches into.

### Band 3 — Connections · *knowledge as a network*
Satisfies criterion 3. An app's relatedness mechanism provides the *candidates*; this band is the
**curated, meaningful** version an author affirms — named links, not just automatic facet matches.
- **Connections to other records** — specific and named.
- **Placement in time** (where the subject admits it).

### Band 4 — Exploration · *outward, last*
Satisfies criterion 4 — after the learner has learned, not instead of it.
- **Sources** (§5, non-negotiable) · **Further reading / museums / references** · **Glossary** ·
  *teacher / parent resources (optional)*.

---

## 4. Negative Requirements

A record is **not** complete merely because it has:

- a description · achievements · an image · related links · AI-generated prose · a large word count.

**Those are inputs, not evidence of educational completeness.** A record can carry every one and satisfy
none of §2. This clause exists so the institution cannot drift back into *"looks complete"* — the exact
failure a real audit found, where a fabricated record with a description, an image and an achievements
list passed for finished. Completeness is certified against §2, never inferred from the presence of
fields.

---

## 5. The non-negotiable: every factual claim is sourced

- **Every claim in Bands 1–3 traces to a real, checkable source in Band 4** — publication + title at
  minimum, a stable URL once confirmed. An author may not invent a citation to satisfy the contract.
- **Depth never comes at truth's expense.** A shorter, fully-sourced account beats a longer,
  half-verified one. "Complete" means *educationally complete **and** true*, never *long*.

This carries the discipline of African Discoveries' content audit (its Phase 0), which exists because
that app once presented a fabricated "African" Mongol scholar assembled from plausible but unsourced
text. Truth is the floor; **sufficiency** is this standard's bar.

---

## 6. Governance rule — the standard leads, the model follows

> **The Educational Record Standard defines the required content model. The content model must evolve to
> satisfy the standard; the standard must not be weakened to accommodate existing implementation
> constraints.**

An app whose data model cannot yet hold Bands 1–2, misconceptions, a glossary or further-reading must
**grow the model**, not narrow the standard. The bar does not come down to meet the code.

> **The grown model:** [`educational-record-schema.md`](./educational-record-schema.md) (DRAFT) is the
> canonical structure that represents this standard — sourcing at claim granularity, depth not journey,
> meaning not presentation. It implements §5's rule structurally rather than by convention.

---

## 7. Implementation is gated per app (adoption is not)

Adopting this standard fixes *what a complete educational record is*, across World A. It commits no app
to authoring content immediately. Each World A app resolves these before authoring records against it:

1. **Scope** — the depth bar applies to *every* record an app claims complete. How many records, and for
   which age bands, is a per-app funding decision (e.g. African Discoveries' open 9–17 vs fund-3–8 call).
   Gates **rollout**, not adoption.
2. **The content-model change** in §6.
3. **The journey axis** — this standard owns record *depth*; the learner's *path across* records is a
   separate, unresolved decision (e.g. the dead `LEARNING_JOURNEY` scaffold and any Discover→…→Teach
   journey). One vocabulary, implemented or removed — never a new one invented per app.

---

## 8. Related

- [`../vision/01-product-rules.md`](../vision/01-product-rules.md) (Canon 03) — the World A
  non-negotiables this extends; that document owns *ages-not-grades, #FreeForever, offline*; this one
  owns *content completeness*.
- [`../vision/00-vision-and-philosophy.md`](../vision/00-vision-and-philosophy.md) (Canon 00) — the
  philosophy this makes into a content rule.
- [`01-capability-architecture.md`](./01-capability-architecture.md) (Canon 01) — capabilities are *what
  a learner becomes*; a complete record is how a single subject contributes to that.
- **First implementation:** African Discoveries — `docs/editorial-standard.md` in that repo is a
  delegated implementation reference; **this document is the canonical owner.** Future implementers
  (Space Explorer, Early Numeracy, and every later World A app) inherit this rather than reinventing
  "complete."
- **Gold-standard exemplar:** [`exemplar-imhotep.md`](./exemplar-imhotep.md) — the first record authored
  to this standard in full. What "complete" reads like, in practice, not in the abstract.
