# 🤖 Guidelines for AI Assistants

This file contains general guidelines for all AI assistants (Claude, ChatGPT, Copilot, Gemini, etc.) using this Markdown task management system.

---

## 📋 Strict Task Format

### Mandatory Template

```markdown
### TASK-XXX | Task title

**Priority**: [Value] | **Category**: [Value] | **Assigned**: @user1, @user2
**Created**: YYYY-MM-DD | **Started**: YYYY-MM-DD | **Due**: YYYY-MM-DD | **Finished**: YYYY-MM-DD
**Tags**: #tag1 #tag2 #tag3

Free text description. **NO `##` or `###` headings allowed**.

**Subtasks**:
- [ ] First subtask
- [x] Completed subtask

**Notes**:
Additional notes with subsections `**Title**:`.

**Result**:
What was done.

**Modified files**:
- file.js (lines 42-58)
```

### Fields

**REQUIRED**: `### TASK-XXX |`, `**Priority**:`, `**Category**:`, `**Created**:`

**OPTIONAL**: `**Assigned**:`, `**Started**:`, `**Due**:`, `**Finished**:`, `**Tags**:`, Description, `**Subtasks**:`, `**Notes**:`

### ❌ FORBIDDEN

- `## Title` or `### Title` inside a task
- `**Subtasks**` or `**Notes**` without `:`

**Why?** The web application's HTML parser does not recognize `##` inside tasks.

---

## 🔄 Workflow

### 1. New request
1. Create task in `kanban.md` → "📝 To Do"
2. Unique ID (TASK-XXX) auto-incremented
3. Break down into subtasks if needed

### 2. Start work
1. Move → "🚀 In Progress"
2. Add `**Started**: YYYY-MM-DD`
3. Check off subtasks progressively

### 3. Finish work
1. Move → "✅ Done"
2. Add `**Finished**: YYYY-MM-DD`
3. Document in `**Notes**:`:
   - `**Result**:` - What was done
   - `**Modified files**:` - List with lines
   - `**Technical decisions**:` - Choices made
   - `**Tests performed**:` - Validated tests

### 4. Archiving

**⚠️ Tasks are NOT archived immediately!**

- Completed tasks remain in "✅ Done"
- **Only on user request** → move to `archive.md` section `## ✅ Archives`
- **Never archive directly at the end of work**

---

## 📝 Examples

### Simple Task

```markdown
### TASK-001 | Fix login bug

**Priority**: Critical | **Category**: Backend | **Assigned**: @bob
**Created**: 2025-01-20 | **Due**: 2025-01-21
**Tags**: #bug #urgent

Users cannot log in. Error 500 in logs.

**Notes**:
Check Redis, related to yesterday's deployment.
```

### Complete Task

```markdown
### TASK-042 | Notification system

**Priority**: High | **Category**: Backend | **Assigned**: @alice
**Created**: 2025-01-15 | **Started**: 2025-01-18 | **Finished**: 2025-01-22
**Tags**: #feature

Real-time notifications with WebSockets.

**Subtasks**:
- [x] Setup WebSocket server
- [x] REST API
- [x] Email sending
- [x] Notifications UI
- [x] E2E tests

**Notes**:

**Result**:
✅ Functional system with WebSocket, REST API and emails.

**Modified files**:
- src/websocket/server.js (lines 1-150)
- src/api/notifications.js (lines 20-85)

**Technical decisions**:
- Socket.io for WebSockets
- SendGrid for emails
- 30-day history in MongoDB

**Tests performed**:
- ✅ 100 simultaneous connections
- ✅ Auto-reconnection
- ✅ Emails < 2s
```

---

## 📔 Devlog Workflow

Devlogs are weekly (or per-sprint) narrative entries — distinct from tasks. They capture what happened, decisions made, and reflections. They are **not** task tracking.

### When to write a devlog entry

- End of a week or sprint
- After a significant milestone
- When the user asks: "Write a devlog", "Summarize this week", etc.

### How to write a devlog entry

1. Append a new `## DEVLOG-XXX | Title` block to `devlog.md`
2. Increment `<!-- Config: Last Devlog ID: XXX -->` at the top
3. Include `**Date**: YYYY-MM-DD` and optional `**Tags**:`
4. Write freeform markdown content — headings are allowed inside devlog entries

### Devlog example

```markdown
## DEVLOG-003 | Week 2026-W12 — Payment gateway shipped

**Date**: 2026-03-22
**Tags**: #backend #feature #milestone

## What we shipped

Stripe integration is live. Handles one-time payments and subscriptions.

## Decisions

- Chose Stripe over Paddle for better API ergonomics
- Webhooks validated with signature verification

## Next week

- Monitor error rates in production
- Start i18n infrastructure
```

### ❌ FORBIDDEN in devlogs

- Do **not** use `### TASK-XXX` format inside devlog entries
- Do **not** manually change the `Last Devlog ID` comment without updating entries

---

## 🎯 Golden Rules

### ✅ ALWAYS
1. Create task BEFORE coding
2. Strict format (no `##` in tasks)
3. Break down if complex
4. Real-time progress
5. Document result in `**Notes**:`
6. Reference tasks in commits (`TASK-XXX`)
7. Leave in "Done" (archive only on user request)
8. Write devlog entries when asked or at end of week/sprint

### ❌ NEVER
1. `## Title` in a task (devlog entries are the exception — headings allowed there)
2. Code without creating task
3. Forget to check off subtasks
4. Archive immediately (stay in "Done")
5. Forget to document the result
6. Use `TASK-XXX` format inside a devlog entry

---

## 📦 File Structure

### kanban.md

**⚠️ ID comment format**: `<!-- Config: Last Task ID: XXX -->` (auto-incremented by application)

```markdown
# Kanban Board

<!-- Config: Last Task ID: 42 -->

## ⚙️ Configuration

**Columns**: 📝 To Do | 🚀 In Progress | 👀 Review | ✅ Done
**Categories**: Frontend, Backend, DevOps
**Users**: @alice, @bob
**Tags**: #bug, #feature, #docs

---

## 📝 To Do

### TASK-001 | Title
[...]

## 🚀 In Progress

## 👀 Review

## ✅ Done

### TASK-003 | Completed task
[...]
```

### archive.md

```markdown
# Task Archive

> Archived tasks

## ✅ Archives

### TASK-001 | Archived task
[... full content ...]

---

### TASK-002 | Another archived task
[... full content ...]
```

### devlog.md

Weekly development log entries. One file per project, auto-created on first save.

**⚠️ ID comment format**: `<!-- Config: Last Devlog ID: XXX -->` (auto-incremented by application)

```markdown
# Dev Log

> Weekly development logs

<!-- Config: Last Devlog ID: 3 -->

## DEVLOG-001 | Week 2026-W10

**Date**: 2026-03-08
**Tags**: #backend #feature

What happened this week. Full markdown supported — headings, lists, code blocks, etc.

## DEVLOG-002 | Sprint review — auth refactor

**Date**: 2026-03-15
**Tags**: #refactor #backend

Summary of the sprint...
```

**Fields:**
- **REQUIRED**: `## DEVLOG-XXX |`, title
- **OPTIONAL**: `**Date**:`, `**Tags**:`, freeform content (any markdown)

**Rules:**
- Unlike tasks, devlog entries **allow `##` and `###` headings** inside the content — the parser only splits on `## DEVLOG-XXX`
- Entries are displayed newest-first in the UI but stored oldest-first in the file
- Never edit the `<!-- Config: Last Devlog ID: XXX -->` comment manually — the app manages it

---

## 🔧 User Commands

```bash
# Planning
"Plan [feature]"
"Create roadmap for 3 months"

# Execution
"Do TASK-XXX"
"Continue TASK-XXX"

# Tracking
"Where are we?"
"Weekly status"

# Modifications
"Break down TASK-XXX"
"Add subtask to TASK-XXX"

# Search
"Search in archives: [keyword]"
"Search in devlogs: [keyword]"

# Maintenance
"Archive completed tasks"

# Devlog
"Write a devlog entry for this week"
"Add a devlog entry: [title]"
"Show devlog entries"
```

---

## 📘 Git Integration

```bash
# Commits with reference
git commit -m "feat: Add feature (TASK-042 - 3/5)"
git commit -m "fix: Bug fix (TASK-001)"

# Branches
git checkout -b feature/TASK-042-notifications
```

---

## 📁 AI-Specific Configuration

Each AI has its own configuration file:

| AI Assistant | Configuration File | Location |
|--------------|-------------------|----------|
| **Claude** | `CLAUDE.md` | Project root |
| **GitHub Copilot** | `copilot-instructions.md` | `.github/` |
| **OpenAI CLI** | `OPENAI_CLI.md` | Project root |
| **ChatGPT** | `CHATGPT.md` or Custom GPT | Root or Web |
| **Gemini** | `GEMINI.md` or `instructions.md` | Root or `.gemini/` |
| **Qwen** | `QWEN.md` or `.qwenrc` | Project root |
| **Codeium / Windsurf** | `instructions.md` | `.windsurf/` or `.codeium/` |

**These files must:**
1. Reference this file `AI_WORKFLOW.md`
2. Be adapted to each AI's specifics
3. Remain minimalist (only a few lines)

### Minimal Template for AI Configuration File

```markdown
# 🤖 Instructions for [AI NAME]

## 📋 Task Management System

**Every action = One documented task in kanban.md**

## 📚 Complete Documentation

**⚠️ READ IMMEDIATELY**: `AI_WORKFLOW.md`

This file contains everything: format, workflow, commands, examples.

## ⚙️ Critical Rule #1

**NO `##` or `###` headings inside a task**
- Use `**Subtasks**:` and `**Notes**:` with colons
- Subsections: `**Result**:`, `**Modified files**:`

**Why?** The HTML parser does not recognize `##` inside tasks.

---

**Read `AI_WORKFLOW.md` now.**
```

---

## 🎓 First Use

### Initialization

On your first interaction with the AI:

```
"Read AI_WORKFLOW.md and use the task system"
```

The AI will automatically:
1. Read `AI_WORKFLOW.md`
2. Understand the complete format and workflow
3. Be ready to manage tasks according to defined rules

### Usage Examples

**Create a task:**
```
"Plan adding a real-time notification system"
```

**Work on a task:**
```
"Do TASK-007"
```

**Status update:**
```
"Where are we?"
```

**Archive:**
```
"Archive completed tasks"
```

**Write a devlog:**
```
"Write a devlog entry for this week"
"Summarize what we did in DEVLOG-004"
```

---

**This guide ensures complete transparency and traceability of AI work.**
