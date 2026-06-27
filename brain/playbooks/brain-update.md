# Playbook: Brain Update Protocol

> How to keep the brain current after any significant session.
> The brain is only trustworthy if it reflects reality. A stale brain is dangerous
> — future AIs will act on wrong information.

---

## When to update

Update the brain when any of these happen:
- An app was shipped or reached a new milestone
- A significant decision was made (architecture, product, business)
- An incident occurred (Play rejection, build failure, security issue)
- A feature was added or fundamentally changed
- An idea was retired or pivoted away from
- A new pattern was identified that appears in two or more apps

---

## Quick decision guide

| What happened | Files to update |
|---|---|
| New app shipped | `apps/<app>.md` (create) · `CURRENT_STATE.md` · `PROJECT_TIMELINE.md` · `SESSION_HANDOFF.md` |
| App status changed (testing → live) | `apps/<app>.md` · `CURRENT_STATE.md` |
| Structural decision made | `decisions/DECISIONS.md` (append) |
| Incident or pivot | `history/HISTORY.md` (append) |
| New reusable pattern identified | `patterns/<name>.md` (create) · `patterns/README.md` (add to index) |
| Session ended (any significant work) | `SESSION_HANDOFF.md` (always update) |
| Terminology changed | `PROJECT_GLOSSARY.md` (append or clarify) |

---

## File-by-file update rules

### `brain/SESSION_HANDOFF.md`

**Update:** after every significant session, at the very end.
**Rule:** Prepend a new entry (newest first). Never delete old entries.

The entry must include:
- What was done (specific — not "improved the bot")
- State of ongoing work (where exactly to pick up)
- Next steps in order (the actual next action, not vague goals)
- Unresolved issues or risks
- Key files changed

### `brain/CURRENT_STATE.md`

**Update:** when any app status, platform piece, or track changes.
**Rule:** Edit in place — this is a snapshot, not an append log.
Always update the "As of:" date in the header.

### `brain/PROJECT_TIMELINE.md`

**Update:** when a significant milestone is reached.
**Rule:** Append entries within the appropriate year/period section. Never reorder.
Use exact dates where known; use `~<date>` for approximate.

### `brain/apps/<app-slug>.md`

**Update:** when the app's architecture, features, or status changes materially.
**Rule:** Add a dated "Evolution" or "Updates" entry at the bottom. Don't rewrite
the original — the history matters.

### `brain/decisions/DECISIONS.md`

**Update:** when a structural decision was made.
**Rule:** Append only. Format:

```markdown
## YYYY-MM-DD — <Decision title>

**Context:** What situation prompted this decision?
**Decision:** What was chosen?
**Alternatives rejected:** What else was considered and why it was rejected?
**Consequences:** What does this decision commit us to?
```

### `brain/history/HISTORY.md`

**Update:** when an incident, pivot, rename, or retired idea happens.
**Rule:** Append only. Include the date and what actually happened.

---

## The golden rule

**Append, don't rewrite.**

Old entries are evidence of how the project evolved. They are valuable even when they
describe things that are no longer true. Never delete them. Never edit them to make
them "correct" by today's standards.

If something was wrong in a past entry: add a new, dated entry saying it was wrong and
what is correct now.

---

## Gotchas

| Gotcha | Fix |
|---|---|
| Brain and ECOSYSTEM.md disagree on a URL | ECOSYSTEM.md wins (it's operational); update the brain to match |
| CURRENT_STATE.md shows an app as "testing" but it's live | Update CURRENT_STATE.md — the brain must reflect reality |
| SESSION_HANDOFF.md is months old | Write a catch-up entry. Even a short one is better than nothing. |
| An app memory file (`apps/<name>.md`) describes a feature that was removed | Append a dated note: "Feature X was removed on YYYY-MM-DD because..." |
