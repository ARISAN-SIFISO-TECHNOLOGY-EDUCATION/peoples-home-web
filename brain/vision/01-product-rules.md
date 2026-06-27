# Canon 03 — Product Rules (the non-negotiables)

> Break one of these and you have broken the project. They are the philosophy
> ([`00-vision-and-philosophy.md`](./00-vision-and-philosophy.md)) made into engineering constraints.
> They apply to **World A learning apps** unless noted.

---

## 1. Ages, never grades
- Present **everything by AGE**. CAPS/IGCSE/Cambridge alignment is **internal only** — grade
  labels must **never render in UI**. (Smoke-test intent: zero `Grade|GR[0-9]` strings in output.)
- **Why:** grades gatekeep and shame; age is universal, dignified, and works for learners who
  missed schooling. Part of "technology should empower, not gatekeep."

## 2. Every learning app's age ceiling reaches 17 *(added 2026-06-21)*
- No learning app stops at 12. Each pillar reaches **age 17** (ages-not-grades).
- **Why:** a child must be able to keep growing inside the Home, not get ejected at 12.
- **Forced action:** Science Sprouts (was 3–12) extended to 13–17 via a teen "Academy" tier (done 2026-06-25).

## 3. #FreeForever
- No ads, no IAP, no paywalls, no accounts — on learning apps. **Forever.**
- **The one exception:** iKhaya's backend cost (World B). That's the *#FreeForever funding fork*,
  to be resolved before iKhaya's 2027 launch. See [`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md).

## 4. Offline · no-data
- Learning apps require **no internet** and collect **no data** ("No data collected"). No runtime
  network calls.
- Anything needing network/PII is **World B (iKhaya)**, not a learning app.
- **Why:** sovereign learning — connectivity and surveillance must not gatekeep; the learner owns
  their progress on-device (and can carry it via the [Passport](../platform/peoples-home-passport.md)).

## 5. SA-first
- Local contexts, names, Rand, languages throughout. Built for South Africa first, honestly.
- **isiZulu** ships as **DRAFT** until a native-speaker review (batched, ~December 2026). Apps ship
  English-first; zu present but flagged draft.

---

## Cross-cutting craft rules (learned the hard way)

| Rule | Why | Source |
|---|---|---|
| **Use Math Adventure's `useNarration`** (wait for `voiceschanged`, pin an installed voice, isiZulu→English fallback). Never the naive `speak()`. | Science Sprouts shipped silent using `speak()`. **Device-audio is a release gate.** | [`../HISTORY.md`](../history/HISTORY.md) |
| **Less text + calmer sound for young ages.** | Math Adventure's "Expert Approved" badge was rejected for text volume + disruptive sounds (2026-06-17). | [`../HISTORY.md`](../history/HISTORY.md) |
| **Unique PWA manifest `id` per app** (e.g. `/our-world/`). | Sibling apps installed from the same origin collide / launch each other without it. | [`04-delivery-model.md`](./04-delivery-model.md) |
| **Module-over-new-app.** | Stops the blueprint drifting back to 40 products. | [`01-capability-architecture.md`](./01-capability-architecture.md) |

---

## Definition of done (a learning app)

A World-A app is "done" when:
- Live PWA, **offline-verified** (no runtime network calls), and
- on the People's Home site (card flipped to live, incognito-checked), and
- has a **unique PWA manifest `id`**, and
- **0 grade strings**, and
- isiZulu present (DRAFT acceptable), and
- audio works on-device.

See the operational [`../../ROADMAP.md`](../../ROADMAP.md) for the running checklist.

---

## Related
- [`00-vision-and-philosophy.md`](./00-vision-and-philosophy.md) — the *why* behind every rule here.
- [`02-world-a-world-b-dna.md`](./02-world-a-world-b-dna.md) — which rules apply where.
