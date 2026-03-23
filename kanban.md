# Kanban Board

<!-- Config: Last Task ID: 3 -->

## ⚙️ Configuration

**Columns**: 📝 To Do (todo) | 🚀 In Progress (in-progress) | 👀 In Review (in-review) | ✅ Done (done)

**Categories**: Frontend, Backend, Design, DevOps, Tests, Documentation

**Users**: @user (User), @luca

**Priorities**: 🔴 Critical | 🟠 High | 🟡 Medium | 🟢 Low

**Tags**: #bug #feature #ui #backend #urgent #refactor #docs #test

---

## 📝 To Do

### TASK-002 | Setup internationalisation
**Priority**: Low | **Category**: Frontend | **Assigned**: @luca
**Created**: 2026-03-22
**Tags**: #feature #ui

Setup internationalisation (i18n) infrastructure for the frontend to support multiple languages and locales. This includes translation management, language switching, and locale-specific formatting.

**Subtasks**:
- [ ] Choose i18n library (e.g., react-i18next, next-intl)
- [ ] Setup translation file structure
- [ ] Implement language switcher component
- [ ] Configure locale detection
- [ ] Add support for date/number formatting per locale
- [ ] Create translation management workflow
- [ ] Write tests for i18n functionality

**Notes**:
Research best practices for i18n in modern frontend frameworks and select appropriate library for project needs.

## 🚀 In Progress

## 👀 In Review

## ✅ Done

### TASK-003 | Add devlog functionality to task-manager
**Priority**: High | **Category**: Frontend | **Assigned**: @luca
**Created**: 2026-03-22 | **Finished**: 2026-03-22
**Tags**: #feature #ui

Extend the task-manager with a devlog section for writing weekly dev logs to markdown files. Analogous to the folder/task/archives/columns pattern.

**Subtasks**:
- [x] Add devlog button to header (analogous to archives/columns)
- [x] Create devlog list modal with search
- [x] Create new devlog form modal
- [x] Implement devlog.md file read/write (load/save/parse)
- [x] Add create, delete, and detail view functionality
- [x] Add translations (en/fr) for all devlog UI text
- [x] Wire button visibility into existing project load/unload flows

**Notes**:

**Result**:
Devlog feature fully implemented. Entries stored in devlog.md in the project folder using format `## DEVLOG-XXX | title` with Date, Tags, and freeform markdown content. Button appears in header alongside Archives/Columns once a project is loaded.

**Modified files**:
- task-manager.html (devlog button, 3 modals, JS parse/load/save/render functions, translations en+fr)

