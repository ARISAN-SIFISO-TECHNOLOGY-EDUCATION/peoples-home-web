# iKhaya Learn

> **World B · server-backed learning portal** (different DNA from the offline apps) · ages 13–17 ·
> repo `SifisoScS/ikhaya-learn-reloaded` · stack React + Express + Gemini.
> Context: [`../canon/02-world-a-world-b-dna.md`](../canon/02-world-a-world-b-dna.md).

---

## What it is
An **AI-tutored web/coding portal** for ages 13–17 — a freemium ("iKhaya Plus") learning product
with an AI tutor named **"Sizwe"** (Gemini-backed). React + Express server + Gemini.

## Why it exists
It fills the 13–17 web/coding-tutoring space and is a server-backed, AI-native learning experience —
something the offline apps deliberately are *not*. Ages-not-grades is honoured.

## Why it's World B, not a learning app (the key classification)
Despite being "learning," iKhaya Learn is **World B by DNA**:
- **server-backed** (Express),
- **data leaves the device** (Gemini calls, accounts),
- **has a paid tier** (freemium).

That's the opposite of the World-A promise (offline · no-data · #FreeForever). So it lives on the
**opportunity/server side** with iKhaya — *not* among the offline learning apps. It's a clean example
of *why the DNA split is about engineering reality, not subject matter*: a "learning" product can
still be World B.

## Design iterations / how the thinking evolved
- **Surfaced on the People's Home by linking, not bundling.** Because it's server-backed and lives on
  its own URL, the way to bring it into the Home is to **deploy it and link a card**, not to fold its
  code into the offline ecosystem.
- It overlaps conceptually with **iKhaya** (the opportunity layer) as the AI/server half of the
  People's Home — both carry the server/PII/paid DNA.

## Architectural decisions (& rejected alternatives)
- **Kept on the server side.** *Rejected:* treating it as a World-A offline app (it can't be — it
  needs a server and sends data off-device).
- **Freemium model** ("iKhaya Plus") — consistent with World B carrying cost, unlike the
  #FreeForever offline apps.

## Current state
Exists as a server-backed portal (`SifisoScS/ikhaya-learn-reloaded`). Relationship to the main
iKhaya platform is the broader World-B story.

## Future direction
Surface on the People's Home by deploying to a URL and linking a card. Its server/AI DNA aligns it
with iKhaya's 2027 arc and the #FreeForever funding fork.

## Related
- [`ikhaya.md`](./ikhaya.md) (the opportunity layer it shares DNA with) ·
  [`../canon/02-world-a-world-b-dna.md`](../canon/02-world-a-world-b-dna.md) (the classification that
  puts it here, not among the learning apps).
