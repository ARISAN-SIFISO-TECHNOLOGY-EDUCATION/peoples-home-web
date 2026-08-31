# Reconciliation — the pre-pivot roadmap against the institutions model (2026-08-31)

> Factual log. **Decisions are the founder's.** This walks every open item from the *old*
> app-portfolio roadmap and marks where it stands after the **2026-08-17 institutions pivot**
> ("apps are dying in the AI era — build systems/institutions"). Sources: this brain's
> `DECISIONS.md` (D-01…D-22), `ROADMAP.md`, `CURRENT_STATE.md`, `project_state` memory,
> and the two post-pivot session records (2026-08-17, 2026-08-22).
>
> ⚠️ **Honesty caveat that governs the whole document:** the founder has **not** issued an
> explicit ruling retiring the old app portfolio. The pivot said the new People's Home was
> *"rebuilt separately from the previous app portfolio"* — it did **not** say "delete the old
> apps," and all ~12 old apps are still LIVE on `*.pages.dev`. So every **🔁 SUPERSEDED** mark
> below is **provisional** — it reflects that the pivot created a new forward line, not that the
> old thing was formally killed. **The fate of the old portfolio is the central open decision
> (§3).** Nothing here retires anything on its own.

**Legend:** ✅ DONE/CLOSED · 🟢 STILL-LIVE (survives the pivot) · 🔁 SUPERSEDED (provisional — see caveat) · ❓ NEEDS-DECISION · 🆕 NEW (created by the pivot)

---

## 1 · What the pivot forked

Before 2026-08-17 there was **one line**: ~12 offline React+Vite PWAs on Cloudflare Pages
(`*.pages.dev`), curated to six flagships (D-14), heading for a **portfolio launch on 2026-08-09**
(D-17). The pivot started a **new line**, built *separately*:

- **New front-door:** `the-peoples-home` — the "Porch Light" house, on **Hostinger** at
  `peopleshome.ikhaya-ai.com` (not Cloudflare).
- **New engine:** `parallel-rivers-math-engine` — a **brand-new Next.js build** (65 E2E tests),
  live at `/math/` behind the Foundations room. **It is not the old Math Adventure RPG.**
- **Five of six rooms have no engine yet.** The house is still mostly a front-door shell.

So the two lines are genuinely distinct codebases and hosts. The reconciliation below is really
about which *old* line items carry across the fork, which are replaced by the new line, and which
were never about World A at all (iKhaya / DNA) and are therefore untouched.

---

## 2 · Item-by-item

### Survives the pivot — 🟢 STILL-LIVE
- 🟢 **G6 / R2 — no app ever observed with a real child.** Re-affirmed as *the critical path* in
  **both** post-pivot session records. Engineering two live URLs "moves no educational evidence."
  Un-superseded, top priority. *(Open question folded in below: play-test **what** now — the new
  house + Math Engine, or the old apps? See §3.)*
- 🟢 **World A / World B DNA split (D-02)** and **#FreeForever + "wire AI, don't activate it"
  (D-05, D-12).** Foundational; D-22 explicitly lists them as *not changed*.
- 🟢 **iKhaya (World B) — one-suburb beta (2026 H2) + flagship launch (2027).** World B is
  orthogonal to the World-A pivot. The **#FreeForever funding fork** still gates the 2027 launch.
  *(This is the "2027 project" — still standing.)*
- 🟢 **Security on the live systems.** Now active: the 2026-08-22 record flags **no CSP on either
  app**; Next needs its own policy. This is the founder's stated current agenda item.
- 🟢 **The offline defect class.** Neither service worker precaches its own content-hashed
  JS/CSS; offline currently depends on `.htaccess` `Cache-Control`. "Check on every new engine."
  Live technical debt that recurs per engine.

### Replaced by the new line — 🔁 SUPERSEDED (provisional)
- 🔁 **The 2026-08-09 Portfolio Launch (D-17)** as an *event*. It was "present the initial
  collection of flagship experiences together." The pivot replaced "launch the portfolio" with
  "build the house + engines." **Its core condition — the real-child play-test — survives on its
  own (see STILL-LIVE).** The date is moot.
- 🔁 **Community Release site curation (D-14).** Curated the *old* `index.html` to six flagships.
  The live site is now the house at `peopleshome.ikhaya-ai.com`.
- 🔁 **Web-first / Cloudflare Pages as the delivery mechanism (D-03).** Superseded as *hosting* by
  Hostinger + "rooms in one origin" (**D-22**). The offline / #FreeForever / no-account **DNA
  survives**; only the `.pages.dev` mechanism is replaced.
- 🔁 **Numeria / Math Adventure RPG two editions / story system (D-15, D-16; `numeria_blueprint`
  memory).** These were the *old* Math app's roadmap (MA-0…MA-5, Stable/Community editions). The
  new Foundations experience is the *new* Parallel Rivers Math Engine. ❓ **but see §3** — does
  Numeria's content feed the new engine, or is it parked?
- 🔁 **Number Kingdom / Early Numeracy (NK-4 freeze, NK-5).** The *old* Foundations app. Same
  question as Numeria — parked, or does its content feed the Math Engine? ❓ §3.
- 🔁 **Deepen passes** (Our World's other journeys, Everyday Foundations "Languages") and **TPH
  Core SDK → `@tph/core` extraction (D-09).** All were *old multi-app-portfolio* platform work.
  Superseded unless the old apps live on. ❓ §3.
- 🔁 **isiZulu native-speaker review (~Dec 2026).** Was a batched pass over the old apps. Carries
  forward only for whatever survives §3 (and the new engines will need their own).

### Already resolved — ✅ DONE/CLOSED
- ✅ **Kilimanjaro (WhatsApp AI agent).** Founder ruling 2026-08-31: **removed from TPH, frozen,
  re-home to iKhaya.** Off-model for offline/no-runtime-AI TPH; skeleton reusable, `src/knowledge/`
  rebuilt for iKhaya. Teardown done (Claude key deleted, Railway service deleted); optional last
  tidy = revoke the Meta token. Repo `github.com/KilimanjaroCode/kilimanjaro` intact. This closes
  the old `project_state` item 2 ("set `ADMIN_PHONE_NUMBER`").
- ✅ **R1 — Android keystore off-machine backup.** Closed 2026-07-23, integrity-verified.
- ✅ **"Truth Seekers has no GitHub remote."** Was a false claim; corrected 2026-07-21. Not a task.

### Created by the pivot — 🆕 NEW forward work
- 🆕 **Build the five remaining engines:** Science · Maker · Logic · Finance · Venture. Five of
  six rooms are empty; the house is a shell until they exist.
- 🆕 **Per-engine hosting discipline (D-22):** each room needs its own `.htaccess`; every link into
  a room keeps its trailing slash; re-check room folders survive after any root upload.
- 🆕 **CSP on the house and each engine** (the security item, now concrete).

---

## 3 · The central open decision — ❓ the fate of the old app portfolio

Everything marked 🔁 hangs on one ruling only the founder can make:

> **Are the ~12 live `*.pages.dev` apps retired, kept live-but-frozen, or does their content
> migrate into the new Parallel Rivers engines?**

Three coherent positions:
- **(A) Retire them.** The pivot means what it says; the old apps are sunset. Clean, but discards
  a large body of authored, working content (Numeria, Number Kingdom, all six flagships, Canon 06
  educational records).
- **(B) Keep them live, freeze them, build forward with engines.** The old apps stay reachable at
  their URLs but get no new work; all effort goes to the house + engines. Lowest-risk; costs
  nothing to leave PWAs parked.
- **(C) Migrate content into engines.** The engines are new *shells*; the old apps' authored
  learning content (and Canon 06 records) becomes the material an engine teaches. Highest-value
  reuse, most work. This is the only path where Numeria / Number Kingdom / isiZulu / `@tph/core`
  stop being 🔁 and become inputs to 🆕.

**Not decided here.** This is the ruling that turns the whole 🔁 column from "provisional" into
settled. Recommend it be taken explicitly and recorded as a D-record, because every old-portfolio
item's status derives from it.

---

## 4 · Other open decisions

- ❓ **The #FreeForever funding fork (D-05, D-22 open list).** Still the one place free-forever needs
  an answer; gates iKhaya's 2027 flagship. Unchanged by the pivot.
- ❓ **Publication of `peoples-home-web`.** The publication hold ("no push until after 2026-08-09")
  expired. On **2026-08-31**, a push of the decouple docs (`d85b8dc`) carried **21 previously-held
  commits** to the **public** origin — including the hold-record itself and the candid launch-review
  files (`launch-experience-review-notes-2026-07-26.md`, `launch-readiness-2026-08-09.md`). Within
  the letter of the hold (date passed), but not a conscious release decision. **Founder to decide:**
  accept the disclosure, or make the repo **private** (recommended — it holds the whole Brain).
- ❓ **Security constitution for live systems.** CSP absent on both live apps; a per-engine security
  baseline is unwritten. (Founder's current agenda item; ties to `SECURITY_CONSTITUTION.md`.)
- ❓ **Standing pre-pivot opens still unresolved** (D-22 list): Digital Creator Academy (parked);
  the Golden Hand framing; whether the Stable Build Principle becomes DNA Principle #19 — all now
  **contingent on §3** (they only matter if the old apps live on).

---

## 5 · The current forward roadmap (post-pivot), if §3 = keep-and-build-forward

1. **Real-child play-test** of the live house + Math Engine — still the critical path (G6).
2. **Security baseline** — CSP on the house and the Math Engine; write the per-engine security rule.
3. **Build the next engine** (Science/Maker/Logic/Finance/Venture — founder picks order).
4. **Close the offline defect class** — precache hashed assets in each service worker (don't leave
   Law 5 depending on `.htaccess` alone).
5. **iKhaya (World B)** — background track toward the one-suburb beta; resolve the funding fork
   before the 2027 launch.
6. **Rule §3** (portfolio fate) — the decision that re-prioritises everything above.

---

## 6 · What this reconciliation is not

It does not retire, delete, or freeze anything — it records where each item stands and surfaces the
decisions. All 🔁 marks await the §3 ruling. Written as a local Brain record; **not pushed**, pending
the founder's call on §4's publication question.
