# The Educational Record Schema — DRAFT

**Status:** 📝 **DRAFT — proposed, not adopted.** · **Opened:** 2026-07-24 · **Owner (on adoption):** World A
**Represents:** [`06-educational-record-standard.md`](./06-educational-record-standard.md) (Canon 06).
**Proving ground:** African Discoveries (evidence, not owner).

> Canon 06 defined *what a complete educational record is.* This is the **structure that represents it** —
> the "grown model" Canon 06 §6 obliges, so that any interface (app, website, AI assistant, voice, print)
> can present the same record differently while staying grounded in one educational meaning.
>
> It is a **canonical** schema, not an African Discoveries type. Applications implement it; they do not
> own it. On adoption it becomes the Educational Record schema for World A.

---

## 1. Design principles (these govern every field below)

1. **Canonical, not minimal.** Optimise for *educational completeness*, not for today's implementation.
   The first implementation may leave fields empty; it may **not** omit a concept from the schema because
   the first app does not support it yet. (Same philosophy that produced Canon 06.)
2. **Educational meaning, not presentation.** The schema names *Historical Context · Misconceptions ·
   Connections · Glossary* — never *tab · accordion · panel · sidebar*. It does not know whether a record
   is shown on one screen, ten screens, in a chat, by voice, in VR, or on paper. (Follows from the
   Institutional Platform Strategy: the platform owns the record; interfaces present it.)
3. **Depth, not journey.** It answers *"what is this educational record?"* — never *"what happens after
   reading it?"* No `nextRecord`, `unlockLevel`, `sequence`, `prerequisite`. Progression is a different
   model, deliberately not this one (Canon 06 §3, §7).
4. **Every claim is sourced, at claim granularity.** Canon 06 §5 says every claim traces to evidence. A
   record-level `sources[]` cannot express *"which source supports this paragraph?"* or *"which source
   backs this misconception correction?"* So **evidence attaches to the smallest meaningful claim** — the
   atom in §3. A claim without a source is not representable as complete.

## 2. The justification test (what may enter the schema)

A field exists **only** if it is justified by one of three sources. Anything else stays out until
evidence demands it — this is what keeps the schema from becoming speculative architecture.

| # | Justification |
|---|---|
| **C** | **Canon 06** — required to represent educational completeness |
| **R** | **A real educational record** (Imhotep, Great Zimbabwe, Maathai, Nyokong — §5) |
| **A** | **A constitutional rule already adopted** (Canon 03 ages-not-grades; the C4 signed-year lesson; Phase 0 sourcing) |

Every type in §3/§4 carries its justification. A field with none does not belong.

---

## 3. The atom — a sourced claim

Educational content and its evidence are **inseparable** (Canon 06 §5). The unit the whole schema is
built from:

```ts
// [A: Phase 0]  A citation. Publication + title at minimum; a stable URL only once
// independently confirmed — never fabricated (the Phase 0 discipline).
interface SourceRef {
  citation: string;        // "Publication — 'Title'"
  url?: string;            // present only when verified
  verified: boolean;       // false until independently checked
}

// [C: §5]  The smallest meaningful educational claim, bound to its evidence.
// INVARIANT (validator-enforced, cf. African Discoveries data.test.ts): sources.length >= 1.
// A claim with no source is an assertion, not a claim — and is not "complete".
interface Claim {
  statement: string;       // one coherent educational statement (sentence or paragraph)
  sources: SourceRef[];    // >= 1, always
}
```

Prose in Bands 1–3 is `Claim[]`, not `string`. That single decision is what makes *"every claim is
sourced"* a structural property rather than a hope.

---

## 4. The record

```ts
interface EducationalRecord {
  // ── Identity ──────────────────────────────────────────────────────────────
  id: string;              // [R] stable identifier
  kind: string;            // [R] the APP's subject taxonomy (hero/animal/place/…). The canonical
                           //     schema does not fix the subject types — that is an app decision.
  title: string;           // [R]
  subtitle?: string;       // [R] e.g. a hero's role, a species' common framing

  // ── BAND 1 · Foundation — the lesson itself [C: §3 Band 1] ─────────────────
  foundation: {
    introduction: Claim[];         // who/what, for a first encounter
    account: Claim[];              // the actual history or science — the substance today's records lack
    significance: Claim[];         // achievements / why it matters
    misconceptions: Misconception[]; // [C] required: an institution corrects misunderstanding
    facts?: Claim[];               // optional, only if they teach
  };

  // ── BAND 2 · Context — the subject's world [C: §3 Band 2] ──────────────────
  context: {
    world: Claim[];                // era, place, society
    fields: string[];              // domains it touches (each may resolve to a Connection)
  };

  // ── BAND 3 · Connections — knowledge as a network [C: §3 Band 3] ───────────
  // CURATED and named by an author — not the raw output of an app's relatedness mechanism.
  connections: Connection[];
  placement?: TemporalPlacement;   // where it sits in time, if the subject admits it

  // ── BAND 4 · Exploration — outward, last [C: §3 Band 4] ────────────────────
  exploration: {
    furtherReading: SourceRef[];   // books, museums, references
    glossary: GlossaryTerm[];      // terms the account introduced
    // NOTE: primary sources are NOT a separate list here — they live on every Claim (§3),
    // which is the whole point. "Where this comes from" is assembled from the record's claims.
  };

  // ── Cross-cutting ──────────────────────────────────────────────────────────
  ageBands: AgeBand[];     // [A: Canon 03] which ages this record's content serves (ages, never grades)
  media: MediaRef[];       // [R] illustrations — referenced by MEANING (alt/caption), not layout
}

interface Misconception {              // [C: §3 Band 1]
  misconception: string;               // the common wrong belief, stated plainly
  clarification: Claim;                // the evidenced correction — a Claim, so it is sourced
}

interface Connection {                 // [C: §3 Band 3]
  targetId: string;                    // another EducationalRecord
  relationship: string;                // NAMED and meaningful: "built", "studied under", "influenced"
  note?: Claim;                        // why they connect (sourced if it asserts anything)
}

interface TemporalPlacement {          // [A: African Discoveries C4 — the signed-year lesson]
  year: number;                        // signed: NEGATIVE = BCE, positive = CE. Never rendered raw.
  eraLabel?: string;                   // "Old Kingdom", "Medieval", …
}

interface GlossaryTerm { term: string; definition: string; }   // [C: §3 Band 4]

interface MediaRef {                   // [R] + [A: audit H1 accessibility]
  assetId: string;
  alt: string;                         // meaning, never "" for meaningful media
  caption?: string;
  // NO width/height/position/tab/panel — presentation belongs to the interface (principle 2)
}

type AgeBand = "3-5" | "6-8" | "9-12" | "13-17";   // [A: Canon 03]
```

---

## 5. Validation against real records (evidence, per your constraint)

The schema is ready only if it can faithfully hold real content. Traced against the four test cases:

| Record | Foundation.account | Misconception | Context.world | Connections | Placement |
|---|---|---|---|---|---|
| **Imhotep** | Step Pyramid architect; physician; later deified | *"only legendary"* → real official under Djoser | Old Kingdom Egypt, Djoser's reign | Djoser · Egyptian architecture · early medicine | `-2650`-ish, "Old Kingdom" |
| **Great Zimbabwe** | dry-stone city; Shona builders; trade hub | *"built by Europeans"* → Shona ancestors (archaeology) | medieval southern Africa, gold/ivory trade | Shona peoples · Indian Ocean trade | ~`1100`–`1450` CE |
| **Wangari Maathai** | PhD (vet anatomy); Green Belt Movement; Nobel Peace Prize | *miscategorised "leader"* → scientist by training | 20th-C Kenya, environmental movement | reforestation · civic activism | `1940`–`2011` |
| **Tebello Nyokong** | chemist; photodynamic cancer therapy; Rhodes University | *modern African science is "absent"* → living, working scientist | contemporary South Africa | medicine · chemistry | b. `1951` |

All four represent cleanly. **One finding this surfaced:** Great Zimbabwe is a *place/civilisation*, which the
app's current `kind` taxonomy (heroes/animals/innovations/timeline) has no clean slot for. That is an
**application** limitation, not a schema one — the canonical schema leaves `kind` to the app (§4), and this
is exactly the kind of gap the proving-ground exercise is meant to expose.

---

## 6. Deliberately excluded (and why)

Recorded so a future contributor does not "helpfully" add them:

- **Journey / progression:** `nextRecord`, `previousRecord`, `unlockLevel`, `sequence`, `prerequisite`.
  Principle 3 — a different model. (The current app's `unlocked: boolean` is a progress flag; it does
  **not** belong on the record.)
- **Presentation:** any tab/accordion/panel/screen/layout field. Principle 2.
- **Speculative:** versioning, i18n structure, multi-tenant, analytics hooks. None passes §2's test yet.

## 7. Open questions (flagged, not decided)

1. **Reading-level / register.** The app hand-writes a child-friendly `narration` distinct from the
   `description`. Is an age-appropriate *register* educational meaning (belongs in the schema, perhaps as
   per-`ageBand` `Claim` variants) or presentation (belongs in the interface)? Genuinely unresolved, and
   entangled with the **scope decision** (9–17 vs fund-3–8). Left out until that is made.
2. **Exact claim granularity** — sentence, paragraph, or "assertion"? §3 fixes the *direction* (claim-level);
   the precise unit is a design call best made against a fully-authored record.
3. **`kind` taxonomy** — owned by each app, or eventually a World A vocabulary? Deferred; the schema works
   either way today.

## 8. Relationship

- **Owned by** [`06-educational-record-standard.md`](./06-educational-record-standard.md) (Canon 06) —
  this schema represents that standard and has no authority of its own.
- **Unblocks** African Discoveries' content-model gate (Canon 06 §7.2; the app's `docs/editorial-standard.md`
  reference) — *without* touching the scope or journey gates.
- **Realises** the Institutional Platform Strategy's core: one educational record, many interfaces.

*Author proposes; the founder rules. Until adopted, no app implements this, and the current flat types stand.*
