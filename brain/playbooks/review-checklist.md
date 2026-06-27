# Playbook: Pre-Ship Review Checklist

> Run this checklist before shipping any new app or major feature.
> Check every item. If something fails, fix it before deploying.

---

## DNA check (cannot ship if any fail)

- [ ] App works 100% offline (tested in Chrome DevTools → Network → Offline)
- [ ] App requires no login, no account, no email, no phone number
- [ ] App is free — no payment prompt, no IAP, no "upgrade" path
- [ ] No third-party tracking SDKs (Google Analytics, Meta Pixel, etc.)
- [ ] No content uses "Grade N" — all ranges are age-based ("Ages 8–10")
- [ ] All scenarios, names, and contexts are South African
- [ ] App is in a defined capability pillar (not a standalone content dump)

---

## Technical checks

- [ ] Service worker is registered and caching all assets
- [ ] Hard refresh in incognito window shows no network errors
- [ ] All audio files are bundled or service-worker-cached (no CDN URLs at runtime)
- [ ] `localStorage` keys are namespaced with `tph-<app-slug>-`
- [ ] Progress persists across browser refresh
- [ ] Progress persists after closing and reopening the browser
- [ ] `npm run build` succeeds with no TypeScript errors
- [ ] `dist/` contains all assets (no missing files)
- [ ] PWA manifest is present and valid (App Name, Icons, Theme Color, Start URL)
- [ ] App icons are present: 192×192 and 512×512 PNG

---

## Content checks

- [ ] No lorem ipsum or placeholder text in production build
- [ ] All SA scenarios and names reviewed for accuracy
- [ ] Age range is correct and used consistently throughout the app
- [ ] isiZulu content (if present) is marked DRAFT or has been through native-speaker review
- [ ] No "coming soon" screens in the first shipped experience (cut the feature, ship what's ready)

---

## Accessibility basics

- [ ] App is usable with keyboard navigation (Tab to focus, Enter/Space to activate)
- [ ] Images have alt text (or are decorative with `alt=""`)
- [ ] Colour contrast meets WCAG AA minimum (4.5:1 for text)
- [ ] If voice-first: audio plays after user gesture (not on page load)

---

## Platform integration

- [ ] App entry added to `kilimanjaro/src/knowledge/platform.ts`
- [ ] App detail card added to `kilimanjaro/src/agent/brain.ts` → `APP_RESPONSES`
- [ ] App added to `buildAppListSections()` (and 10-row limit respected)
- [ ] App URL added to `APP_URLS` in `brain.ts`

---

## Brain update (after shipping)

- [ ] `brain/apps/<app-slug>.md` created or updated
- [ ] `brain/CURRENT_STATE.md` updated with new status
- [ ] `brain/PROJECT_TIMELINE.md` updated with ship date
- [ ] `brain/SESSION_HANDOFF.md` updated with what was done and what is next
- [ ] `brain/decisions/DECISIONS.md` updated if any significant decision was made

---

## Final smoke test

- [ ] Open the app URL fresh in an incognito window
- [ ] Complete one full learning activity from start to finish
- [ ] Close and reopen — progress is preserved
- [ ] Go offline — app still works
- [ ] WhatsApp bot responds correctly to the app's name and ID

---

## Notes on what "shipping" means for this project

**"Shipped" = deployed to Cloudflare Pages + card on peoples-home-web.pages.dev.**

Google Play is no longer the bar. A World-A app is live when it is accessible on the web
as an offline PWA and surfaced in The People's Home.

The first version of every app ships with one area/journey/pillar deep. The rest can
be "Coming soon" — but the shipped portion must be fully functional, not a skeleton.
