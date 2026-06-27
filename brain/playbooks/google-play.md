# Playbook: Google Play — Wind-Down Mode

> **IMPORTANT:** The Google Play track is closed. No new apps will be submitted.
> This playbook covers maintenance-only operations for the two apps that are
> already on Play: Math Adventure RPG and Science Sprouts.
>
> **Decision date:** 2026-06-21. See `brain/decisions/DECISIONS.md` for rationale.
> **Rationale summary:** Slow review cycles, morale cost, keystore management burden.
>  Web-first PWAs on Cloudflare Pages deliver the same offline experience faster.

---

## The two apps still on Play

| App | Package ID | Current key |
|---|---|---|
| Math Adventure RPG | `com.sifiso.mathadventurerpg` | `upload-new.jks` (rotated ~2026-06-09) |
| Science Sprouts | (check Play Console) | Same keystore setup |

---

## ⚠️ CRITICAL: Keystore backup

The signing keystores (`upload-new.jks`) are the single most important files in this
project after the source code.

**If the keystore is lost: you can never update these apps on Google Play. Ever.**
Google does not allow uploading a new signing key for an existing app.

**Current status as of 2026-06-27: LOCAL ONLY. Not backed up.**

### Backup instructions

1. Locate: `<repo>/android/upload-new.jks` (or wherever `keystore.properties` points)
2. Back up to at least two off-machine locations:
   - A password manager (Bitwarden, 1Password) as an attachment
   - An encrypted cloud drive (Google Drive, OneDrive) in a folder called `keystores/`
   - Optionally: a USB drive stored physically separate from your machine

3. Also back up `keystore.properties` (contains the passwords and alias)
   **Store the passwords separately from the keystore file** — ideally in a password manager.

---

## Updating an existing Play app (maintenance only)

This is for bug fixes or required API level updates. No new features needed.

### Build

```bash
cd <app-repo>
# For Capacitor apps:
npm run build
npx cap sync android
cd android
./gradlew bundleRelease
```

### Sign

The AAB is signed automatically if `keystore.properties` points to `upload-new.jks`.
Verify `android/app/build.gradle` has:
```groovy
signingConfigs {
    release {
        storeFile file(keystoreProperties['storeFile'])
        storePassword keystoreProperties['storePassword']
        keyAlias keystoreProperties['keyAlias']
        keyPassword keystoreProperties['keyPassword']
    }
}
```

### Upload

1. Play Console → <App> → Production → Create new release
2. Upload the `.aab` from `android/app/build/outputs/bundle/release/`
3. Add release notes (English required; isiZulu optional)
4. Submit for review

**Review time:** Typically 1–3 days for updates. Up to 7 days for major changes.
Target audience changes can add review time.

---

## Known issues from past releases

| Issue | What happened | Fix |
|---|---|---|
| "Expert Approved" badge rejected (Math Adventure) | Too much text for young ages; disruptive sounds | Reduce text for younger age tiers; calm sounds. Carry fix to PWA also. |
| Target audience change blocked (Math Adventure) | Audience changed from 5&under to 16–17 to reflect 3–17 content | Must re-declare the correct audience; takes time to propagate |
| Keystore rotation (Math Adventure, ~2026-06-09) | Original upload key lost; upload key rotated to `upload-new.jks` | Always back up the keystore immediately after any rotation |

---

## For all future apps: web-first only

New apps do NOT go to Google Play. They ship as Cloudflare Pages PWAs.
See [`cloudflare-pages.md`](./cloudflare-pages.md).

The reasons Play is wind-down:
1. PWA install = same offline experience, no review delay
2. Keystore management is a permanent operational risk
3. The Play review process (badges, content ratings, target audience) adds friction
   that doesn't improve the learner experience
4. Web-first reaches learners on any device, not just Android
