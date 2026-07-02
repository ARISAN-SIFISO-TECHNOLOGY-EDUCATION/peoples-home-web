# THE PEOPLE'S HOME — Roadmap & Status

> What's live, what's next, and the sequencing logic. **Source of truth.**
> Last updated: 2026-06-26.

See also: [`BLUEPRINT.md`](./BLUEPRINT.md) · [`ECOSYSTEM.md`](./ECOSYSTEM.md) · [`DECISIONS.md`](./DECISIONS.md).

---

## Strategy in one line
**Web-first.** Ship each learning app as an offline, installable **Cloudflare Pages PWA**, then
surface it on this site. (Superseded the Google-Play "release machine" — see
[`DECISIONS.md`](./DECISIONS.md) → "Web-first pivot".) Learning apps are **offline · no-data ·
no-account · #FreeForever · ages-not-grades · age-ceiling-17 · SA-first.**

---

## Status board (World A — learning apps)

| App | Pillar | Status |
|---|---|---|
| Math Adventure RPG | Foundations | **LIVE** (web PWA + Android). Numeracy 3–17. |
| ReadAfrica | Foundations | **LIVE** (web PWA). Literacy 3–17. Hosts the TPH Core SDK (embedded). |
| Science Sprouts | Curiosity | **LIVE** (web PWA). Science **3–17** ✅ — teen **Science Academy** tier added 2026-06-25 (data-driven exam-prep on the ported exam-studio engine; 5-school arc 13 Explorers → 17 Thinkers, 15 topics / 45 levels), so the **age-ceiling rule is satisfied**. **Play: ROLLING OUT TO PRODUCTION (2026-06-21)**. SS is the **last app on Google Play ever**; Play track now closed. |
| Tech Makers | Creation | **LIVE** (web PWA). Maker arc 3–17. |
| SIFISO — The Golden Hand | Creation | **LIVE** (web PWA). A **five-app-in-one system** — a journey: Golden Learn (Python) → Golden AI (AI literacy) → Golden Quiz (mastery) → Golden Startup (*1M Startups*) → Golden Commons (*Each One, Teach One*). 100% offline (self-hosted Pyodide/Monaco). |
| **Truth Seekers** | Reasoning | **LIVE** (web PWA, 13–17). Five muscles: Fact Finders · Logic Builders (fallacies) · Data Detectives (stats) · System Builders (bias slider) · Truth Makers (evidence board), 24 SA scenarios. **Phase 2 polish (2026-06-24): now fully reasoning-native** — the Atelier engine scaffold (STACK/POUR/ROLL/MAKE) was purged and case content ~doubled. Early ages 3–12 deferred until TPH matures. |
| Everyday Foundations | Foundations | **LIVE** (web PWA) — https://everyday-foundations.pages.dev/ . The adult **second front door** (NOT remedial — confidence-building). 5 areas (Reading · Numbers · Digital Skills · Everyday Life · Languages), voice-first, progress-as-abilities, Household Mode. full shell + **Everyday Life · Digital Skills · Numbers · Reading** authored deep (24 lessons; only Languages "Coming soon" — deferred to the isiZulu review batch). Satisfies the Foundations adult on-ramp. |
| Our World | Curiosity | **LIVE** (web PWA) — https://our-world-b0t.pages.dev/ . The Curiosity pillar's signature companion to Science Sprouts: a **belonging journey** (Place · People · Planet), not a geography quiz. Six Journeys (South Africa **deep** — 7 hand-verified discoveries; Africa · The World · Nature · Cultures · Big Trips "Coming soon"); 🏡 My Home opener + 📘 My Passport (first-person stamps, never %); voice-first; Household Mode. All-ages, EF chassis. |
| Mzansi Money | Money | **LIVE** (web PWA, 13–17) — https://mzansi-money.pages.dev/ . Money-wisdom journey "My Money, sorted": Earn → Budget → Save → Borrow → Protect, Grow & Plan, on the Micro Founders chassis. Money Situations picker + Budget Board + Credit Calculator + My Money Plan. Money wisdom, never advice; hands off to iKhaya for jobs/funding. |
| Micro Founders | Empowerment | **LIVE** (web PWA, 13–17). Full 5-stage Venture Journey ([`MICRO_FOUNDERS.md`](./MICRO_FOUNDERS.md)) playable: Spot · Cost · Sell · Build · Pitch, + 3 bespoke activities (price board · pitch builder · venture canvas). "My Venture" through-line, Atelier chassis. |
| Early Numeracy | Foundations | **BUILT, not deployed.** Number-sense 3–7. Phase 1 shell (2026-06-30). Youngest-learner on-ramp below Math Adventure. |
| Early Literacy | Foundations | **BUILT, not deployed.** Emergent literacy 3–7 ("Village"). Built externally (Gemini); Phases 1–4 (Listening → Sound → Letters → First Words) + navigation framework. Integrated into the Brain 2026-07-02. Consumes engines via Event Bus; adds WordEngine + ReadingJourneyEngine. ⚠️ deploy + governance fixes pending — see [`brain/apps/early-literacy.md`](./brain/apps/early-literacy.md). |
| Golden Hand — Web track | Creation | Planned (a Web/HTML-CSS-JS step inside The Golden Hand; AI literacy already ships as **Golden AI**). |
| Digital Creator Academy | Creation | Parked (future, undecided). |

## Status board (World B — opportunity infrastructure = iKhaya)
| Surface | Status |
|---|---|
| iKhaya core (jobs/social loop) | Prototype ~4/10 (Lovable). 2026 = one-suburb closed beta goal; 2027 = People's Home flagship. |
| Opportunity Hub (6 navigators + job/funding surfaces) | Lives inside iKhaya (bundled static data). |
| Community & Mentor Services | Inside iKhaya. |

---

## What's next (near-term sequence)
1. ~~**Truth Seekers v1 (teens 13–17)**~~ — ✅ DONE. Live PWA; Phase 2 made it fully reasoning-native
   (engine scaffold purged) and ~doubled the case content (2026-06-24).
2. ~~**Mzansi Money (Pillar 5, teens 13–17)**~~ — ✅ DONE. Live PWA (mzansi-money.pages.dev), 5-stage
   Money Journey on the Micro Founders chassis (2026-06-24).
3. ~~**Science Sprouts → age 17**~~ — ✅ DONE (2026-06-25). Teen Science Academy tier live in the
   science-sprouts PWA; age-ceiling rule now satisfied across all Curiosity apps.
4. ~~**Everyday Foundations (Pillar 1, adult on-ramp)**~~ — ✅ DONE (2026-06-26). Live PWA
   (everyday-foundations.pages.dev): the adult second front door, 5-area shell + Everyday Life authored
   deep, voice-first, Household Mode; **Digital Skills · Numbers · Reading** added (now 4 of 5 areas live, 24 lessons).
   *Remaining: Languages — deferred to the batched isiZulu/multilingual review (it's inherently multilingual).*
5. ~~**Our World** (Curiosity)~~ — ✅ DONE (2026-06-27). Live PWA (our-world-b0t.pages.dev): the
   belonging-journey app (Place · People · Planet) — six Journeys, South Africa authored deep (7
   discoveries), 🏡 My Home opener + 📘 My Passport, voice-first, Household Mode. **All World-A "current"
   apps per the BLUEPRINT are now shipped** (one live app in every pillar). Deepen passes (other 5
   Journeys, age-band depths, bespoke activities, multilingual) are the post-2026 backlog.
6. **TPH Core SDK** — extract from ReadAfrica into a shared package; adopt across apps (platform track).
   **Now the lead item** alongside the deepen passes.
7. **iKhaya** — steady background track toward a one-suburb beta; the funding-model decision must be
   resolved before its 2027 launch.

## Definition of done (a learning app)
Live PWA (offline-verified) + on this site (card flipped to live, incognito-checked) + unique PWA
manifest `id` + **0 grade strings** + isiZulu present (DRAFT) + no runtime network calls.

---

## Milestones
- **2026-06-21 — Google Play track CLOSED.** Science Sprouts (the final Play release) is rolling
  out to production; Math Adventure + SS are maintenance-only on Play. All future apps are
  web-first PWA only.

## Standing backlog / debts
- **isiZulu native-speaker review** — all apps ship English-first; zu is **DRAFT** until a batched
  December review.
- ~~**Foundations adult on-ramp**~~ — ✅ built & live as **Everyday Foundations** (2026-06-26). Deepen
  pass: 4 of 5 areas live (Everyday Life · Digital Skills · Numbers · Reading); only Languages remains,
  deferred to the multilingual review batch.
- **"Expert Approved" (Play)** — Math Adventure's badge was rejected (text volume for young ages +
  disruptive sounds); fix carries over to the PWA.
- **Keystore off-machine backup** — outstanding, high priority (see `DECISIONS.md`).
