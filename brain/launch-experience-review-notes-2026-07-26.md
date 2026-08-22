# Launch Experience Review — Founder's Notes (verbatim)

> **Evidence record. Founder's own words — do not rewrite, do not soften.** Captured 2026-07-26,
> 17:14. Source: the founder walked all six flagships and filled the web notebook; `6/6 reviewed`.
> The notebook's `↓ Notes (.md)` export failed silently (sandboxed-iframe downloads are blocked),
> so the founder pasted the rendered notebook. This file is the durable copy — the web notebook's
> data lives only in one browser's localStorage.
>
> **What was walked:** African Discoveries · Truth Seekers · Mzansi Money · Micro Founders on their
> **local dev servers** (current unpushed branches); Tech Makers · Math Adventure RPG on their
> **live** builds (no unpushed app changes).
>
> The synthesis at the bottom is **mine**, kept separate from the founder's words above it (D-002 /
> evidence-decision-record: findings are not rewritten to match an outcome).

---

## 1 · African Discoveries — verdict: **Not yet**
- **First impression:** "Impression is great"
- **Navigation:** "Navigation confusing because the users feel like there's more to learn about the subject whereas there's little"
- **Reading / activity:** "It's good - but the thing is when the cards are such big, users expect a lot whereas there's little information. People of today are about information, and when there's little info, they turn to other apps or websites, and that's where the competition is. The one with a lot of information wins."
- **Trust signals:** "No errors, clear language - design is promising something big, but there's little information, and the cards should stop promising - cards are big with little info."
- **Friction:** "There's little information in African Discoveries"
- **Why (verdict):** "More information must be provided to my learners and the people of South Africa - Not satisfied at all."

## 2 · Tech Makers — verdict: **Not yet**
- **First impression:** "Promising - not bad"
- **Navigation:** "Yes, navigation is well"
- **Reading / activity:** "Repeated content in the whole 'Discover' card for ages 3-5, and in 'Build' for ages 6-12, and also in the 'Create' for ages 13-17... This is not worth publishing."
- **Trust signals:** "Nothing broken - the problem is the repeated content all over the app"
- **Friction:** "Not worth publishing"
- **Why (verdict):** "More information must be provided to my learners and the people of South Africa - Not satisfied at all."

## 3 · Truth Seekers — verdict: **Not yet**
- **First impression:** "Promising"
- **Navigation:** "Navigation will always confuse if what's found inside confuse... when clicking as a parent you don't find why this feature was added or was it added for the sake of being there."
- **Reading / activity:** "I find a very little knowledge than what I was expecting. It felt like a quiz in disguise. This is built to provide information that is enough then questions later"
- **Trust signals:** "Nothing broken, language is clear - but the information is very little"
- **Friction:** "More information must be provided to my learners and the people of South Africa - Not satisfied at all."
- **Why (verdict):** "More information must be provided to my learners and the people of South Africa - Not satisfied at all."

## 4 · Mzansi Money — verdict: **Not yet**
- All fields: **"Same as Truth Seekers"** (first-impression field reads "Same as Truth Seekers & Mzansi Money" — self-reference; intent is Truth Seekers).
- **Why (verdict):** "More information must be provided to my learners and the people of South Africa - Not satisfied at all."

## 5 · Micro Founders — verdict: **Not yet**
- All fields: **"Same as Truth Seekers & Mzansi Money"**.
- **Why (verdict):** "More information must be provided to my learners and the people of South Africa - Not satisfied at all."

## 6 · Math Adventure RPG — verdict: **worthy, pending the planned animation upgrade — do not touch else**
- Every field: "This app needs nothing more than animation as explained in our conversation - In other words, it is to take this app to another level. Nothing more to be touched unless we do animation upgrade."
- *(Ties to the MA animation blueprint — MA-0…MA-5. Not a content-depth concern.)*

---

## Portfolio coherence — "one Home, not six strangers"
- **One Home or six strangers:** "Making the home doesn't mean the apps must be the same, like rooms are not the same. The main bedroom will never be the same as lounge room. So, this must be changed, about three apps are the same. Boring."
- **Ties / jars:** "They must not share the same interface"
- **Most worthy:** "As stated in each and every app review"
- **Least worthy:** "As stated in each and every app review"
- **What would make a parent trust the collection:** "Nothing right now"

---

## Synthesis (mine — separate from the verbatim above)

**Verdict count: 0 of 6 worthy as-is. 5 "Not yet"; Math Adventure held pending its planned animation upgrade.**
This is, in effect, a founder **G7 = HOLD** across the whole launch face. The 2026-08-09 readiness
picture is materially changed by it.

Three findings, ranked:

### F1 — The portfolio is under-informed *(dominant; hits 4 of 6)*
Every content app got the same verdict: **the design promises depth the content doesn't deliver.**
Founder's thesis, in his words: big cards "promising something big" over "little information";
*"the one with a lot of information wins"*; Truth Seekers *"felt like a quiz in disguise… provide
information that is enough then questions later."* This is a **content problem, not an engineering
one** — and it validates the entire premise of **Track A** (Canon 06 record authoring). The apps are
well-built shells waiting for substantial content.
→ **Pile: mostly Experiential/Direction (founder) + Track A production.** "How much, what depth" is
the founder's call; authoring to that bar is production.

### F2 — Three apps are clones *(reverses a live strategy)*
Truth Seekers · Mzansi Money · Micro Founders are *"the same. Boring… They must not share the same
interface."* The house/rooms metaphor: one Home does **not** mean identical rooms.
**This directly reverses the Atelier shared-shell strategy** ("fix once, fix three"), and the
Atelier **accessibility baseline** completed earlier this session made these three *more* identical.
The a11y improvements themselves (focus rings, skip links, reduced-motion) remain valid; the premise
that a **shared visual shell is a virtue** is now rejected by the founder for these three apps.
→ **Pile: Direction (founder decision) → then production re-differentiates.** Must not be silently
actioned — it unwinds prior architecture.

### F3 — Tech Makers repeats content across age bands *(confirmed defect)*
Verified in-code: the same four engines (Stack · Pour · Roll · Stick) are reused across every age
band with only relabeled names/intros (`src/content/age10.ts`: *"the SAME four interactive engines
as Age 3–9"*). By design as progressive complexity — but experientially it reads as one app repeated
three times. Founder: *"not worth publishing."*
→ **Pile: Objective defect (production) — but the fix is content differentiation per band, which is
substantial, not cosmetic.**

### What this does NOT change
- **Math Adventure RPG** — explicitly fine; only the planned animation upgrade (MA blueprint). Leave it.
- The engineering/accessibility repository work stands; the finding is about **content and identity**,
  not build health.

### The decision this tees up (founder's, not production's)
The review has surfaced that the launch blocker is **content depth + app differentiation**, not
play-tests or engineering. Before production re-engages, the founder decides scope:
1. Is "more information" a **launch-blocking** rewrite of every content app, or a post-launch growth
   commitment — and what does that do to **2026-08-09**?
2. Confirm the **de-cloning** of the three Atelier apps (reverses the shared-shell strategy).
3. Tech Makers: differentiate the three age bands' content.

Recording only. No app rewritten, nothing pushed, no scope decided here.
