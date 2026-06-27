# Pattern: Voice-First Narration

> The app reads content aloud to the learner. This is not an accessibility feature
> — it is the primary interface for the intended audience.

---

## What it is

Voice-first means the app narrates its own content using Text-To-Speech (TTS) as
the default mode. The learner does not need to read to learn. Text on screen is
secondary — a visual echo of what is being spoken.

This is distinct from:
- **Voice input** — the learner speaking commands to the app (not implemented)
- **Accessibility subtitles** — captions added for accessibility (different use case)
- **Background music** — decorative audio (not narration)

---

## Why we use it

### Problem: literacy as a barrier

Two of the six pillar audiences are explicitly low-literacy:
1. **Everyday Foundations** — adults who missed formal schooling; may not be able to read
2. **Our World** — all-ages belonging journey; the youngest tier (ages 3–5) cannot read

An app that requires reading to navigate is an app that gatekeeps its own content.

### Problem: mobile data cost for audio streaming

Streaming audio requires data. Narration must be offline, bundled, or generated locally.

### Solution

Pre-record or synthesise narration as bundled audio files. The TTS engine (or pre-recorded
audio) is baked into the app — no streaming, no API calls. On first interaction, the app
speaks. The learner hears before they read.

---

## How it is implemented

### Audio delivery options

**Option A: Pre-recorded audio files** (higher quality, larger bundle)
- `.mp3` or `.webm` files bundled with the app
- Triggered on content reveal: `new Audio('narration/intro.mp3').play()`
- Offline from the start

**Option B: Web Speech API** (no bundle cost, variable quality)
- `speechSynthesis.speak(new SpeechSynthesisUtterance(text))`
- Works offline (OS-level TTS)
- Voice quality depends on the device

**Option C: Hybrid** (recommended for content-heavy apps)
- Key moments: pre-recorded audio
- Incidental navigation: Web Speech API

### Auto-play considerations

Browsers require a user gesture before auto-playing audio. The standard pattern:
- Show a "Tap to begin" screen on first visit
- After first tap, audio can auto-play for the rest of the session
- Store `audioUnlocked: true` in sessionStorage to avoid repeated prompts

### Household Mode integration

In voice-first apps that support Household Mode (Everyday Foundations, Our World):
- Each learner profile should have independent volume/narration settings
- The learner's name is spoken on profile select ("Welcome, Bongani!")

---

## Where it is used

| App | Narration style | Implementation |
|---|---|---|
| Everyday Foundations | Full narration of all content | Pre-recorded + Web Speech API |
| Our World | Narration of journey text and discoveries | Web Speech API (primary) |

**Future candidates:**
- ReadAfrica (literacy app — reading aloud is the pedagogical core)
- Math Adventure RPG (younger learners, ages 3–7 range)

---

## Rules and constraints

1. **Narration must be offline.** No TTS API calls to external services in the core loop.
   Web Speech API or bundled audio only.

2. **Never block on audio.** If audio fails or the user mutes, the app must still be
   fully navigable. Voice is an enhancement layer, not a blocker.

3. **Respect autoplay policy.** Always require one user gesture before first audio play.
   Never attempt to autoplay on page load.

4. **isiZulu narration is a priority.** English first, isiZulu as draft, then native
   speaker review (scheduled ~December 2026). Do not ship isiZulu narration without review.

5. **Speed control.** Adult literacy users (Everyday Foundations) may need slower TTS.
   Provide a speed control (0.75×, 1×, 1.25× minimum).

---

## Evolution

**Pre-2026:** Narration existed in Math Adventure RPG as an enhancement.

**2026-06-26 — Everyday Foundations:** Voice-first became a first-class design principle,
named explicitly because this app's adult literacy audience *requires* it.

**2026-06-27 — Our World:** Applied to the belonging journey for all-ages access.
Our World made Household Mode + Voice-first the standard for new "all ages" apps.
