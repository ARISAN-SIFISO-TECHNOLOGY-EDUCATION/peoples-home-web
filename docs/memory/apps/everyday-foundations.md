# Everyday Foundations

> 🧮 **Foundations** (adult on-ramp) · **all ages, adult-first** · **LIVE** (web PWA) ·
> repo `…/everyday-foundations` (private) · https://everyday-foundations.pages.dev/
> The **"second front door"** to the Home — for adults and those who missed schooling.

---

## What it is
The adult/never-schooled on-ramp to Foundations. Five areas: **Reading · Numbers · Digital Skills ·
Everyday Life · Languages.** Voice-first, progress shown as **real-life abilities** (not %), with a
**Household Mode**. Explicitly **NOT remedial — confidence-building.**

## Why it exists
The BLUEPRINT's Foundations pillar targets *"Children · Youth · Adults who missed schooling · Elders."*
Math Adventure and ReadAfrica serve children well, but an adult needs a different doorway — one that
respects their adulthood and connects to **real life** (IDs, SASSA, municipal forms, using a phone),
not a child's game. Everyday Foundations is that door.

## Original vision
An adult on-ramp covering Everyday English, Everyday Maths, Digital Basics, Citizen Essentials, and
the languages of SA — voice-first, dignity-first.

## Design iterations / how the thinking evolved
- **"Second front door," not a remedial track.** The framing decision matters: it's *confidence-
  building*, entered by choice, not a deficit label. This shapes tone, naming, and the "progress as
  abilities" design (an adult sees *"I can fill in a form"*, never *"42%"*).
- **Voice-first + Household Mode.** Built for shared phones and low-literacy entry — you can *hear*
  your way through, and a household can share one device. This pattern was carried forward into
  **Our World**.
- **Shipped 4 of 5 areas deep.** Everyday Life · Digital Skills · Numbers · Reading authored deep
  (24 lessons); **Languages** is "Coming soon," **deferred to the batched isiZulu/multilingual
  review** (it's inherently multilingual, so it waits for the native-speaker pass).

## Architectural decisions (& rejected alternatives)
- **Reuse the Mzansi Money chassis** (Atelier lineage). *Rejected:* a bespoke adult UI.
- **Progress as real-life abilities, never percentages.** *Rejected:* scores/grades (would shame an
  adult learner — and violates ages-not-grades' spirit).

## Current state
Live web PWA; full shell + 4 of 5 areas deep (24 lessons); only Languages "Coming soon." Satisfies
the Foundations adult on-ramp.

## Future direction
Author **Languages** during the multilingual review; deepen the other areas; a strong future
consumer of TPH Core (Household Mode ≈ multi-profile identity) and the Passport.

## Related
- [`our-world.md`](./our-world.md) (shares voice-first + Household Mode) ·
  [`math-adventure-rpg.md`](./math-adventure-rpg.md) · [`read-africa.md`](./read-africa.md)
  (the children's Foundations apps it complements) ·
  [`../canon/00-vision-and-philosophy.md`](../canon/00-vision-and-philosophy.md) (dignity by design).
