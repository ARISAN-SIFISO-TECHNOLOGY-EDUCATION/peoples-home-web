# Session Handoff

> **Purpose:** Every AI session that does meaningful work in this project should end
> by updating this file. This is the only reliable way to bridge sessions when context
> windows end.
>
> **Protocol:** Append a new entry at the TOP (newest first). Never delete old entries.
> Date every entry. Be specific — future-you has zero context.
>
> **If you are starting a session:** read the most recent entry below, then check
> `CURRENT_STATE.md`. That's enough to resume.

---

## Entry format

```markdown
## [YYYY-MM-DD] — Short description of what happened

**Done this session:**
- Bullet points of what was actually completed and committed

**State of ongoing work:**
- What is mid-flight (started but not finished)
- Exactly where to pick up

**Next steps (in order):**
1. The very next action needed
2. The action after that
...

**Unresolved issues / risks:**
- Anything that needs attention but wasn't resolved

**Files changed (key ones):**
- `path/to/file.ts` — what changed
```

---

## 2026-06-27 — The People's Home Brain built + Kilimanjaro Phases 5–7

**Done this session:**
- **Phase 5 (Platform Knowledge):** Added `src/knowledge/platform.ts` to Kilimanjaro with all 10 live World-A apps, correct URLs, descriptions, and age ranges. Added admin gating (`ADMIN_PHONE_NUMBER` env var).
- **Phase 6 (RAG / live search):** Added `src/knowledge/fetcher.ts` (daily Cloudflare Pages snapshot) and `src/knowledge/search.ts` (keyword-overlap search). Bot can now answer questions from live website content.
- **Phase 7 (Interactive messages):** Added WhatsApp button and list-picker support to the bot. New types in `src/whatsapp/types.ts` and `src/whatsapp/client.ts`. Brain now returns `BotResponse` union (`text | buttons | list`). `receive.ts` routes interactive replies. Welcome message is buttons. App menu is a list picker with all 10 apps in 2 sections.
- **Railway fix:** Moved `@types/express`, `@types/node`, `@types/node-cron`, `typescript`, `prisma` from devDependencies to dependencies (Nixpacks uses `NODE_ENV=production` → skips devDependencies at build time).
- **Knowledge correction:** Discovered all 10 World-A apps are live (bot previously thought only 1–2 were). Complete rewrite of `platform.ts` with accurate URLs and states.
- **Math Adventure Play link fixed:** Correct package ID is `com.sifiso.mathadventurerpg` (was incorrectly `com.ikhaYaai.mathadventurerpg`).
- **THE PEOPLE'S HOME BRAIN:** Built this entire `brain/` directory structure — migrated `docs/memory/` content, restructured canon into `vision/` and `architecture/`, wrote AI_ONBOARDING.md, SESSION_HANDOFF.md, PROJECT_GLOSSARY.md, patterns/, history/, decisions/ subdirectories.
- **Engine-1000 integration (A, B, C):** Created `docs/peoples-home/` in engine-1000 repo with cross-reference docs, TPH tracking, and roadmap mirror.

**State of ongoing work:**
- All Kilimanjaro phases 5–7 are deployed and verified working on Railway.
- Brain construction is complete as of this commit.
- Engine-1000 integration files created.
- Bot persona is "The People's Guide."

**Next steps (in order):**

1. **Add ADMIN_PHONE_NUMBER in Railway Variables**
   - Go to Railway → kilimanjaro project → Variables
   - Add: `ADMIN_PHONE_NUMBER=<your number in E.164 without +, e.g. 27821234567>`
   - This gates personal tools (notes, reminders, invoices) to admin only

2. **Brain deepening passes** — review existing app memory files for accuracy
   - `brain/apps/*.md` — some may predate the final shipped state
   - `brain/platform/tph-core.md` — update with `@tph/core` extraction status

3. **TPH Core SDK extraction** — pull TPH Core out of ReadAfrica into a shared `@tph/core`
   package; this is now the lead platform item

4. **isiZulu review** — deferred to ~December 2026 per ROADMAP

5. **Keystore backup** — the signing `.jks` files are local-only; back them up off-machine
   (high priority security risk — data loss = unrecoverable)

6. **iKhaya one-suburb beta** — background track for 2026 H2

**Unresolved issues / risks:**
- **Keystore backup outstanding** — if the local machine is lost, Math Adventure and
  Science Sprouts cannot be updated on Google Play. Back up `upload-new.jks` immediately.
- **Science Sprouts Play rollout** — in progress (rolling out to Google Play);
  the web PWA is fully live but Play may still be in review stages.
- **iKhaya #FreeForever funding fork** — must be resolved before 2027 launch.
  World A is free; iKhaya needs a revenue model that doesn't compromise the mission.
  This decision is deferred but must be made before iKhaya goes to production.

**Files changed (key ones, this session):**
- `kilimanjaro/src/knowledge/platform.ts` — complete rewrite, all 10 apps
- `kilimanjaro/src/knowledge/fetcher.ts` — snapshot cron
- `kilimanjaro/src/knowledge/search.ts` — keyword search
- `kilimanjaro/src/whatsapp/client.ts` — button + list message types
- `kilimanjaro/src/whatsapp/types.ts` — interactive webhook types
- `kilimanjaro/src/agent/brain.ts` — "The People's Guide" persona, interactive responses
- `kilimanjaro/src/webhook/receive.ts` — interactive reply routing
- `kilimanjaro/package.json` — moved types/build deps to dependencies
- `peoples-home/brain/` — entire directory (new)
- `repository-engine-1000/docs/peoples-home/` — new (engine integration)

---

*(Older entries will appear below as sessions accumulate.)*
