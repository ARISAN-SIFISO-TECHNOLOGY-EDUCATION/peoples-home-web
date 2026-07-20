# Structural and Experiential Gates

> **Status: 📝 DRAFT — deliberately NOT frozen alongside the Numeria documents.**
> Identified 2026-07-20, during the Numeria Guide Constitution.
>
> A classification of review gates across The People's Home. It names a **second kind of gate** that
> the ecosystem had been using informally without distinguishing it.

---

## ⚠️ Why this document is held to a higher standard

A product constitution says *"this is how Numeria works."* **A pattern document says "this is how The
People's Home works."** Those are very different claims, and the second is inherited by every future
contributor who never met the reasoning behind it.

Evidence standard scales with scope:

| Artefact | Scope | Validated by |
|---|---|---|
| **Product constitution** | one product | the product it governs |
| **Pattern document** | the ecosystem | **multiple independent products** |
| **Core governance / DNA** | permanent | **repeated observation across the ecosystem** |

This mirrors `@tph/core`'s extraction rule one layer up: *package what's proven, not what's imagined*
→ **govern what's repeatedly observed, not what's elegantly reasoned.** This document is therefore
subject to the same discipline it advocates — it is not frozen because it reads well, but because it
has been seen to explain reality somewhere it was not designed to fit.

### Ratification — the three-test rule

| Test | Product | Asks | Status |
|---|---|---|---|
| **1 · Originating** | Numeria (First Welcome Gate) | Does it describe something that **cannot** be adequately verified by architecture or implementation review alone? | ✅ Appears to hold |
| **2 · Historical** | Number Kingdom NK-1 | Did an experiential gate **already exist** before it had a name? | ✅ Appears to hold |
| **3 · Independent** | *a future, independently developed product* | Does applying it **clarify governance, or create unnecessary process?** | ⏳ **Insufficient independent evidence** |

Test 3 is the one that matters. If it merely adds ceremony to another product, the pattern is a
Numeria observation wearing an ecosystem's clothes.

### Test 3 — evidence (2026-07-20)

**Early Literacy — the pattern describes something already true, independently.**
[`../apps/early-literacy.md`](../apps/early-literacy.md) states, with no knowledge of this pattern:

> *"The only **true** 'done' gate left is a play-test with a real 3–7-year-old."*

— and explicitly separates it from engineering (*"a content effort, not engineering"*). Every
structural gate there is **already closed**: M1–M10 shipped, security review done, CSP locked,
governance review against DNA complete. What remains is the one gate an engineer cannot satisfy alone.
That is this pattern's exact claim, reached independently in a non-Numeria product.

**iKhaya — the pattern correctly does *not* apply.** No onboarding, welcome, or trust-establishment
surface appears in [`../platform/ikhaya.md`](../platform/ikhaya.md); it is a functional World-B
opportunity surface. Ordinary review is sufficient.

**Why this matters more than the positive result:** the pattern **discriminates**. It applies to
Early Literacy and declines to apply to iKhaya, on the boundary stated in Rule 3. A classification
that applied everywhere would be describing nothing.

**But this is supporting evidence, not independent evidence.** Early Literacy was already known to
exhibit the behaviour — the real-child play-test is listed below as a known instance — so it
corroborates the taxonomy rather than testing it.

### ⏳ Why this document is not waiting on a decision

**The blocker is not founder judgment. The blocker is that the evidence does not yet exist.**

> **Status: insufficient independent evidence for canonisation.** The pattern has explanatory power
> across existing educational products, but awaits validation by an **independently developed future
> product** — one not already known to exhibit the behaviour.

Asking the founder to rule on whether two-and-a-half examples are enough would make canonisation a
matter of judgment, which is precisely the standard this document rejects. **Reality decides, not
preference.** *Canonise what's observed, not what's reasoned.*

### What would settle it

This document now makes a **falsifiable prediction**, which is the point at which a pattern stops
arguing for itself:

> If a future learner-facing product is designed by someone who has never read this pattern, and its
> team independently concludes *"we need to observe a first interaction before we freeze this"* —
> **the pattern predicted reality** and may be canonised.
>
> If instead every such product is adequately served by ordinary structural review, **the pattern is
> a Numeria observation wearing an ecosystem's clothes** and should be narrowed to Numeria or
> discarded.

Either outcome is more informative than further reasoning.

---

## The distinction

Until now, every named gate in the ecosystem answered one question:

> **Is the system built correctly?**

Architecture review · governance review · accessibility review · stability · security · production
validation · the seven flagship promotion gates. All structural.

The Numeria Guide introduced a different question:

> **Does the system produce the intended human experience?**

These require **fundamentally different forms of evidence**, and conflating them is how an emotional
requirement quietly gets downgraded into a checklist item.

### The classifying question

> **Can this gate be satisfied through evidence available to an engineer working alone?**

- **Yes** → it is probably **structural**.
- **No** → ask *why not*. If the answer is *"because the success criterion is fundamentally about
  human experience,"* it is probably **experiential**.

This classifies the **nature of the evidence**, not the product — which is what keeps the taxonomy
from drifting into "important features get real-user validation."

### Known gate categories (current)

*Two categories are known today. This list is **not** asserted to be exhaustive — future work may
identify others.*

| | **Structural gates** | **Experiential gates** |
|---|---|---|
| **Question** | Is it built correctly? | Does it produce the intended human experience? |
| **Satisfied by** | Engineering | Interaction with real people |
| **Evidence** | Documentation, code, tests, review | **Observation** |
| **Examples** | Architecture · governance · accessibility · stability · security | First-run experience · emotional safety · onboarding · trust · delight · confidence |
| **Automatable** | Usually | **No — and it should not be attempted** |
| **Verb** | Testing | **Witnessing** |

---

## Why naming this matters

It pre-empts the question a future contributor will otherwise ask:

> *"How do we automate this?"*

**Some gates should not be automated.** An experiential gate that gets proxied into a metric has been
converted into a structural gate and no longer measures what it was created to measure.

It also protects against the reverse error — treating an experiential gate as merely *the hardest*
structural gate, and therefore as something to be engineered around when a deadline arrives.

---

## Rules

1. **An experiential gate is passed by observation of a real person.** Not a spec review, not a
   simulation, not a proxy metric.
2. **An experiential gate answers one question, not many.** It validates an intention, never artistic
   completeness. A gate that drifts into certifying polish will never be passed by anyone. Everything
   else belongs to ordinary iteration.
3. **Experiential gates are rare by design.** They attach to **front doors** — first encounters,
   onboarding, the moment trust is established — not to routine features. Broad application makes
   them a scheduling tax; narrow application keeps them meaningful.

   **The boundary:** if an interaction exists primarily to establish **trust, confidence, belonging,
   or emotional safety**, an experiential gate may genuinely apply. If it is primarily **functional**
   — navigation, settings, import/export, account-less setup — **ordinary review is sufficient.**
   Without this line the pattern expands into *"every feature needs real-user validation,"* which is
   too broad to survive contact with a deadline.
4. **An experiential gate may justify a documented exception to `Blueprint → Freeze → Build`,** since
   the experience cannot exist before it is built. Any such exception must be **narrow, named, and
   recorded** — see the Numeria Guide's two-stage ratification. *Narrow exceptions survive; broad
   exceptions become loopholes.*

---

## Known experiential gates

| Gate | Product | What it witnesses |
|---|---|---|
| **🚪 First Welcome Gate** | Numeria (Math Adventure RPG) | Does the learner's first encounter with the world express the constitution? *Did they leave feeling more capable than when they arrived?* |
| **10-point experience review** | Number Kingdom NK-1 | The emotional front door — *"NOT freezing on technical completion alone."* (The ecosystem's first experiential gate, before the category had a name.) |
| **Real-child play-test** | Every World-A app | Part of the definition of done; the long-standing informal instance of this category. Early Literacy calls it *"the only **true** 'done' gate left."* |

### Where it does *not* apply

| Surface | Why |
|---|---|
| iKhaya (World B) | Functional opportunity surface — no trust-establishment moment. Ordinary review. |
| Settings · import/export · navigation · the Passport | Functional. Correctness is verifiable by an engineer alone. |

---

## Related
- [`../apps/numeria-guide-constitution.md`](../apps/numeria-guide-constitution.md) §8 — the First Welcome Gate
- [`../apps/number-kingdom-roadmap.md`](../apps/number-kingdom-roadmap.md) NK-1 — the precedent
- [`../community-release.md`](../community-release.md) §4 — the seven flagship promotion gates (structural)
