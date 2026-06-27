# Playbook: Kilimanjaro Update

> Use this when updating the WhatsApp bot — adding a new app to the menu,
> adding a feature, or redeploying to Railway.
>
> **Kilimanjaro repo:** `C:\Users\sifis\Next-Level-Projects\kilimanjaro`
> **Deployed on:** Railway (autodeploy from `main` branch)
> **Bot identity:** "The People's Guide"

---

## Adding a new app to the bot

When a new World-A app launches, the bot needs to know about it.

### 1. Update `src/knowledge/platform.ts`

Add an `AppEntry` to the `APPS` array:

```typescript
{
  name: "<App Name>",
  pillar: "<Pillar Name>",
  description: "<One paragraph — what it does, for whom, what makes it distinctive>",
  ageRange: "Ages X–Y",  // or "Adults" or "All ages"
  status: "live",
  webUrl: "https://<slug>.pages.dev/",
  playUrl: "https://play.google.com/...",  // only if on Play
  highlights: [
    "Highlight 1",
    "Highlight 2",
    "Offline · Free · No login",
  ],
  audience: ["children", "teens", "adults", "parents"],  // pick applicable
},
```

Also add to `APP_IDS`:
```typescript
"<App Name>": "app-<short-id>",
```

And add to `buildAppListSections()` — either `youngApps` or `teenApps` array.

**Important:** WhatsApp list messages have a max of 10 rows total across all sections.
As of 2026-06-27, the list is at exactly 10. When adding an 11th app, either:
- Replace the list with a text menu, or
- Add a "More apps" row that leads to a second level

### 2. Update `src/agent/brain.ts`

Add a detail card to `APP_RESPONSES`:
```typescript
"app-<short-id>": {
  kind: "buttons",
  body:
    "🎯 *<App Name>* ✅ LIVE\n<Age range>\n\n" +
    "<One compelling paragraph about the app.>\n\n" +
    "Offline · Free · No login.",
  buttons: [
    { id: "open-<short-id>",    title: "Open Web App" },
    { id: "back-to-menu",       title: "Back to Menu" },
  ],
},
```

Add to `APP_URLS`:
```typescript
"open-<short-id>": "🎯 *<App Name>*\nhttps://<slug>.pages.dev/",
```

### 3. Type-check and push

```bash
cd C:\Users\sifis\Next-Level-Projects\kilimanjaro
npx tsc --noEmit
git add -A
git commit -m "feat: add <App Name> to bot menu and knowledge base"
git push origin main
```

Railway autodeploys within 2–3 minutes.

---

## Adding a new feature to the bot

1. Decide which file the feature belongs in:
   - **New intent (text parsing):** `src/agent/intent.ts`
   - **New tool (admin only):** `src/tools/<tool-name>.ts` → import in `src/agent/brain.ts`
   - **New interactive response:** `src/agent/brain.ts` → `processInteractiveReply()`
   - **New message type handling:** `src/webhook/receive.ts`
   - **New knowledge source:** `src/knowledge/<name>.ts`

2. Write the feature.

3. Type-check: `npx tsc --noEmit`

4. Test locally if possible: `npx ts-node src/index.ts`

5. Push to `main`. Railway deploys automatically.

6. Test via WhatsApp.

---

## Railway environment variables

Go to Railway → kilimanjaro project → Variables.

| Variable | Description |
|---|---|
| `WHATSAPP_TOKEN` | Meta Graph API bearer token (permanent) |
| `WHATSAPP_PHONE_ID` | The phone ID (`1199517913234373`) |
| `WEBHOOK_VERIFY_TOKEN` | `kilimanjaro-secret-2026` |
| `ANTHROPIC_API_KEY` | Claude API key |
| `DATABASE_URL` | `file:/data/kilimanjaro.db` (Railway volume) |
| `ADMIN_PHONE_NUMBER` | E.164 without `+`, e.g. `27821234567` |

**Gotcha:** Railway's Nixpacks build uses `NODE_ENV=production`, which runs
`npm ci --omit=dev`. Build-time dependencies (`typescript`, `@types/*`, `prisma`) must
be in `dependencies`, not `devDependencies`. Only `ts-node` can stay in devDependencies
(it is only used locally).

---

## Monitoring a deployment

After pushing:
1. Railway Dashboard → kilimanjaro → Deployments
2. Click the active deploy to see build logs
3. A successful deploy shows: `🚀 Kilimanjaro listening on port XXXX`
4. Test: WhatsApp → send "menu" → should receive the app list picker

---

## Rollback

If a deploy breaks the bot:
1. Railway → Deployments → find last good deploy
2. Click **Redeploy** on the good deploy
3. Takes < 2 minutes

---

## Gotchas from past sessions

| Gotcha | Fix |
|---|---|
| Build fails: TS7016 (no declaration file) | Move `@types/*` packages to `dependencies` (not devDependencies) |
| Bot not responding after deploy | Check Railway logs — the most common cause is a missing env var |
| Interactive message not rendering | Check the button title is ≤20 chars; list row title ≤24 chars |
| List message fails: more than 10 rows | WhatsApp max is 10 rows total across all sections |
| Admin tools accessible to non-admin | Verify `ADMIN_PHONE_NUMBER` is set in Railway Variables |
| Wrong Google Play URL | Math Adventure: `com.sifiso.mathadventurerpg` (not `ikhaYaai`) |
