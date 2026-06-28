# History Archive — incidents, pivots, renames, retired ideas

> The things that went wrong, changed name, or were abandoned — and what was learned. Kept so
> the same lessons aren't re-learned the hard way. **Append-only.** Newest at the top within
> each section.

---

## Origins — how The People's Home came to exist

**The first app:** Sifiso built **Math Adventure RPG** and published it to Google Play Store.
That was the beginning — a learning app, built and shipped.

**The moment:** While building the second app — **Science Sprouts** — two things became clear:

1. **Google Play has laws I don't like.** The Play Store is not a neutral delivery channel.
   It has policies, approval power, distribution control, and the ability to delist at any time.
   The apps were inside someone else's walls, subject to someone else's rules. That contradicts the
   whole point: *technology should empower society, not gatekeep it.* Google was gatekeeping.

2. **The vision was bigger than "my apps."** It wasn't enough to build individual apps and publish
   them. There needed to be **a home** — for the apps, and for the people. A place where people
   could learn, build, and achieve. Not inside an app store. Inside something built for them.

**The decision:** Science Sprouts became the last app published to Google Play, ever.
The People's Home was born — not as a technical platform decision, but as a values decision.
The builder chose to build *outside* someone else's walls.

**The founding purpose (verbatim):**
> *"I wanted to build a home for my apps and the people — where they'll learn, build, and achieve."*

**Why this matters to record:** Every architectural decision downstream — PWA-first, #FreeForever,
offline-first, no accounts, no tracking, private by default — flows from this founding moment.
The People's Home is not a collection of apps that happened to share a website. It is a home
that was deliberately built because the alternatives were controlled by someone else.

---

## Incidents (hard-won lessons)

### Keystore rotation (~2026-06-09) — *done, but it left a standing debt*
Math Adventure's Play **upload key** was rotated to `upload-new.jks` (alias `upload`); the old
key was replaced, `keystore.properties` switched, and v2.0/code5 was signed with the new key.
- **Lesson:** Android signing keystores are **local-only, gitignored, and irreplaceable**. Lose
  one and you can never update that app on Play again.
- **Standing action (OUTSTANDING, high priority):** keep an **encrypted off-machine backup** of
  every `.jks` + `keystore.properties` (password-manager vault / encrypted cloud). Never in git,
  but it must exist in more than one place. See root [`DECISIONS.md`](../decisions/DECISIONS.md) → "Critical-information risk."

### "Expert Approved" badge rejected (Math Adventure, 2026-06-17)
Google Play declined the "Expert Approved" badge. Cited: **too much text for young ages** and
**disruptive / distracting sounds**.
- **Lesson:** for the youngest ages, less text and calmer audio. The fix **carries over to the PWA**,
  not just the Play build — it's a product lesson, not a store technicality.

### Science Sprouts shipped silent
An earlier Science Sprouts build shipped with **broken audio** because it used the naive
`speak()` call instead of Math Adventure's robust narration engine.
- **Lesson → house rule:** always use Math Adventure's `useNarration` (wait for `voiceschanged`,
  pin an installed voice, isiZulu→English speech fallback). **Device-audio is a release gate.**
  See [`canon/04-delivery-model.md`](./vision/02-delivery-model.md).

### The strategy brain was nearly unbacked (identified 2026-06-21)
The most critical, least-protected asset wasn't code — it was the **reasoning** behind the
ecosystem, which lived only in machine-local AI memory + a single plan file. One wiped machine
would have erased the *why* of the whole project.
- **Resolution:** migrate it into versioned docs. This memory system (2026-06-27) is that resolution.

---

## Renames

### "SIFISO — Learn Python" → "SIFISO — The Golden Hand" (2026-06-23)
The app was never just a Python course; it's a **five-app-in-one journey** (Golden Learn → Golden
AI → Golden Quiz → Golden Startup → Golden Commons) — effectively the original People's Home
prototype. The in-app title already said "The Golden Hand"; the rename propagated the real name
across the ecosystem (cards, docs, manifest, README).
- **Kept deliberately:** the repo slug `sifiso-learn-python` and the `.pages.dev` URL — renaming
  them would break the Cloudflare connection and the live link. **Display name only.**

---

## Pivots (direction changes)

### Web-first pivot (2026-06-12)
Stopped prioritising Google Play; went web-first via offline Cloudflare Pages PWAs.
*Full reasoning:* [`canon/04-delivery-model.md`](./vision/02-delivery-model.md) and
[`DECISIONS.md`](./decisions/DECISIONS.md).

### Capability architecture (2026-06-21)
~40 imagined apps → a capability *system* (≈10 deep apps + iKhaya + TPH Core).
*Full reasoning:* [`architecture/01-capability-architecture.md`](./architecture/01-capability-architecture.md).

### Google Play track closed (2026-06-21)
Science Sprouts is the **last app on Play, ever**; the release machine is retired after it.

---

## Retired / parked ideas

| Idea | Status | Why |
|---|---|---|
| **~40 independent apps** (v1 blueprint) | **Retired** (2026-06-21) | Collapsed into the capability system. A backlog of 40 products was unbuildable by a solo developer and conceptually wrong — most were *modules*, not apps. |
| **Digital Creator Academy** (video/audio/graphics) | **Parked** (undecided) | A genuine capability, but media tooling is heavy and off-stack. Revisit later. |
| **App Builder Lab / Open Source Builder** as standalone apps | **Folded** | Candidate *capstone modules* inside Tech Makers / The Golden Hand, not separate apps (module-over-new-app discipline). |
| **Google Play as primary channel** | **Retired** (2026-06-12 / 06-21) | Slow review, morale cost; web-first PWAs reach the SA audience better. |
| The six "navigators" as **separate apps** | **Folded into iKhaya** | They need accounts/server (World B); they live as in-app sections of the Opportunity Hub. |

---

## Unknowns worth filling later
- Precise origin dates for Math Adventure and The Golden Hand prototype (`Unknown`).
- The full pre-2026 history of the iKhaya jobs-network prototype.
- The detailed contents of the original ~40-app v1 blueprint (only its *shape* is recorded).
