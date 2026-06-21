# 06. Session Memory & State Recovery

## 🎯 Objective

Ensure every AI session is recoverable — no context is lost between sessions. The agent reads the memory file at start, updates it during work, and writes it before ending. A new session picks up exactly where the last one left off.

## 📍 Location

The memory file lives at `[chosen-root]/memory/memory.md` (e.g., `.archetype/memory/memory.md`). The folder `[chosen-root]/memory/` should be added to `.gitignore` as it contains per-developer runtime state.

## 📋 Structure

The file has two parts:

### YAML Frontmatter (machine-parseable)

```yaml
current_phase: "03"           # Current DLC phase number
active_card: "CARD-003"       # Card being worked on (null if none)
active_epic: "EPIC-001"       # Active epic context
last_session: "2026-06-22"    # Date of last session
phase_status:
  "00": completed
  "01": completed
  "02": completed
  "03": in_progress
  "04": pending
  "05": pending
  "06": pending
```

### Markdown Body (human-readable)

```markdown
## Key Decisions
- **2026-06-22** — Auth: Use JWT over session cookies
  - Rationale: Stateless, matches API-first design
  - Impact: Requires jsonwebtoken package

## Next Steps
- [x] CARD-002: Database schema
- [ ] CARD-003: Login UI
- [ ] CARD-004: Auth middleware

## Notes
Awaiting UI mockups from design team before CARD-005.
```

## 🔄 Session Protocol

### Start of Session
1. Read `[chosen-root]/memory/memory.md`.
2. Report to the user: current phase, active card, next steps.
3. If `last_session` is stale (>1 day), ask if context has changed.

### During Session
4. Append major decisions to **Key Decisions** as they're made.
5. Update **Next Steps** checkboxes as tasks complete.
6. Update `phase_status` when a phase transitions.

### End of Session
7. Update `last_session` to today's date.
8. Ensure all decisions and progress are captured.
9. The file is auto-saved by the agent's file writes.

## 🔧 Agent Instructions

Every agent instruction file (`CLAUDE.md`, `GEMINI.md`, `OPENCODE.md`, and all `agents/*.md`) must include:

> **Session Recovery:** Read `[chosen-root]/memory/memory.md` at session start. Update it as work progresses. Write final state at session end.

## 🚫 Non-Goals

- Not a replacement for `VISION.md`, Epics, or Cards (those track *what*; memory tracks *where we are*).
- Not a log file — don't dump raw conversation history.
- Not gitignored — it should be committed to preserve cross-session state across the team.
