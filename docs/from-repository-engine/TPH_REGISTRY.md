# TPH Registry — The People's Home Repos

> Engine-side tracking for all People's Home repositories.
> This is the engine's view of TPH state — the canonical source is the
> peoples-home repo's `brain/CURRENT_STATE.md`.
>
> **Registry type:** External (not engine-generated — manually maintained)
> **Last updated:** 2026-07-02

---

## Status key

| Symbol | Meaning |
|---|---|
| ✅ LIVE | Deployed, accessible, working |
| 🔄 ACTIVE | In active development |
| 🔒 PRIVATE | Private repo, not public |
| ⏳ PENDING | Not yet started |

---

## World-A Learning Apps (10 repos)

| # | Name | Status | GitHub org | Cloudflare URL | Notes |
|---|---|---|---|---|---|
| 1 | math-adventure-rpg | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | math-adventure-rpg.pages.dev | Also on Google Play (`com.sifiso.mathadventurerpg`). Hosts TPH Core SDK work. |
| 2 | read-africa | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | read-africa.pages.dev | Hosts embedded TPH Core SDK. |
| 3 | everyday-foundations | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | everyday-foundations.pages.dev | Adult on-ramp. Voice-first. Household Mode. |
| 4 | science-sprouts | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | science-sprouts-65b.pages.dev | Also on Google Play (rolling out). Teen Science Academy tier. Last Play app, ever. |
| 5 | our-world | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | our-world-b0t.pages.dev | Shipped 2026-06-27. Belonging journey (Place·People·Planet). Voice-first. Household Mode. |
| 6 | tech-makers | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | tech-makers.pages.dev | Coding + maker arc. Block coding → web dev → robotics. |
| 7 | the-golden-hand (sifiso-learn-python) | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | sifiso-learn-python.pages.dev | URL slug: `sifiso-learn-python` (original name preserved). 5 journeys in one. Offline Python via Pyodide. |
| 8 | truth-seekers | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | truth-seekers.pages.dev | Phase 2: fully reasoning-native. 5 muscles, 24 SA scenarios. |
| 9 | micro-founders | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | micro-founders.pages.dev | 5-stage Venture Journey. My Venture through-line. |
| 10 | mzansi-money | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | mzansi-money.pages.dev | 5-stage Money Journey. Budget Board, Credit Calculator. |

---

## World-A — Foundations on-ramps (ages 3–7)

| # | Name | Status | GitHub org | Cloudflare URL | Notes |
|---|---|---|---|---|---|
| — | early-numeracy | 🔧 BUILT 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | — (not deployed) | Number-sense 3–7. Phase 1 shell (2026-06-30). PWA-ready. |
| — | early-literacy | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | early-literacy.pages.dev | Emergent literacy 3–7 ("Village"). Built externally (Gemini). Foundations slot #4. Phases 1–4 + nav framework. **AI dropped for #FreeForever, deployed as installable offline PWA, senior audit + Phase-1 fixes, repo moved to org — 2026-07-02.** ⚠️ remaster backlog Phases 2–5 + "TPH Core" naming collision (app-local engine set ≠ canonical TPH Core SDK). Canonical memory: `peoples-home/brain/apps/early-literacy.md`. |

---

## Platform and Infrastructure (World B / shared)

| Name | Status | Description |
|---|---|---|
| peoples-home-web | ✅ LIVE 🔒 | The People's Home website (peoples-home-web.pages.dev) |
| peoples-home (root hub) | ✅ ACTIVE 🔒 | Memory/docs hub — `brain/` is here |
| iKhaya | 🔄 PROTOTYPE 🔒 | Opportunity platform (World B). ~4/10. Lovable prototype. Target: 2027 launch. |
| iKhaya Learn | 🔄 CONCEPT 🔒 | AI-tutored learning portal 13–17 (World B; different DNA from World A). |

---

## World-B Platform (iKhaya)

| Name | Status | GitHub org | URL | Notes |
|---|---|---|---|---|
| ikhaya | ✅ LIVE 🔒 | ARISAN-SIFISO-TECHNOLOGY-EDUCATION | ikhaya.pages.dev | Opportunity Hub Phase 4–6. 25 SA opportunities, discovery engine, eligibility engine, offline PWA. Phases 7–10 pending. |

## Supporting tools

| Name | Status | Location | Description |
|---|---|---|---|
| kilimanjaro | ✅ LIVE 🔒 | Railway | WhatsApp AI agent. "The People's Guide." |

---

## Engine tracking notes

- **Registration:** TPH repos are external to the engine's `generated-repos/` system.
  They are tracked here for cross-reference but not managed by `processRepo`.
- **Quality gates:** TPH apps don't go through engine health scoring; they have their
  own Cloudflare Pages deploy pipeline.
- **Batch operations:** Never run engine batch commands against TPH repos.
- **Registry distinction:** This file is `TPH_REGISTRY.md` — not `registry.json`.
  Engine's `registry.json` only tracks engine-generated repos.

---

## Known risks (engine perspective)

| Risk | Priority | Notes |
|---|---|---|
| Keystore backup | 🔴 HIGH | `upload-new.jks` for Math Adventure + Science Sprouts is local-only. Unrecoverable if lost. |
| iKhaya #FreeForever funding fork | 🟡 MEDIUM | Must resolve before 2027. World A stays free; iKhaya needs revenue without compromising the mission. |
| isiZulu review | 🟢 LOW | Deferred ~December 2026. All apps ship English-first, isiZulu as draft. |
