# Contributing Guide

> **Philosophy**: Rapid iteration, human-led development, AI assistance.

---

## 🚀 Quick Start

**For AI Assistants**: Read [`START_HERE_AI.md`](START_HERE_AI.md) first.

**For Humans**: Read [`README.md`](README.md), then this file.

---

## 👥 Roles & Authority

### Human (PM) - Decision Maker & Product Manager

**Authority**:
- ✅ Selects issues to work on
- ✅ Approves all designs, architectures, and technical approaches
- ✅ Reviews and accepts/rejects code
- ✅ Controls development pace and priorities
- ✅ Final say on all major decisions

**Responsibilities**:
- Provide clear task direction
- Review AI proposals and diffs
- Approve commits
- Guide product direction

### [AI_TOOL_1] (PC) - Senior Developer (AI Assistant)

**Authority**:
- ✅ Propose solutions (2-3 options with pros/cons)
- ✅ Implement after approval
- ✅ Handle implementation details (after approach approved)
- ✅ Update documentation
- ✅ Manage GitHub issues and commits (with PM approval)

**Constraints**:
- ❌ NEVER: Select issues, start coding, make major decisions, or commit without approval
- ❌ NEVER: Assume requirements or technical approach
- ✅ ALWAYS: Wait for approval, propose options, show diffs first

**Full rules**: See [`docs/llm-rules.md`](docs/llm-rules.md)

### [AI_TOOL_2] (Mobile) - Design Consultant (AI Assistant)

**Authority**:
- ✅ Brainstorm with PM
- ✅ Discuss designs and architecture
- ✅ Has GitHub read access (check project state)

**Constraints**:
- ❌ Cannot write to GitHub directly
- ❌ Cannot implement code
- ✅ Works in GitHub issue threads (post findings as comments)

**Note**: Mobile and PC are independent instances (no shared context)

---

## 📊 Decision Authority Matrix

| Decision | Who Decides | Requires Approval |
|----------|-------------|-------------------|
| Which issue to work on | Human PM | - |
| Tech approach | Human PM | ✅ |
| Architecture | Human PM | ✅ |
| DB schema | Human PM | ✅ |
| API design | Human PM | ✅ |
| Implementation details | AI (after approach approved) | ❌ |
| Code style, variable names | AI | ❌ |
| Documentation updates | AI | ❌ |

---

## 🔄 Development Workflow

### 1. Issue Selection (Human)

```
Human: "Let's work on #X"
AI: [Reads issue] "Got it. Summarizing..."
```

### 2. Design Proposal (AI → Human)

```
AI: "I see 2-3 approaches:

    A. [Approach A]
       Pros: ...
       Cons: ...

    B. [Approach B]
       Pros: ...
       Cons: ...

    Which approach do you prefer?"
Human: "Go with B"
```

### 3. Approval (Human → AI)

```
Human: "Go ahead"
AI: "Starting implementation..."
```

### 4. Implementation (AI, supervised by Human)

AI implements, shows progress. Human reviews diffs in editor.

### 5. Review & Commit (Human approval required)

```
AI: "Done. Here's the diff: [shows changes]
     Ready to commit?"
Human: [Reviews diff] "Yes, commit it"
AI: [Commits with proper message]
```

---

## 📏 Issue Size Management

**CRITICAL**: Every issue must complete in single 200K token session.

### Size Limits

| Size | Time | Action |
|------|------|--------|
| ✅ Small | 1-4h | Perfect |
| ⚠️ Medium | 4-6h | Monitor context |
| ❌ Large | >6h | **MUST SPLIT** |

**Details**: See [`docs/llm-rules.md#issue-size-management`](docs/llm-rules.md#issue-size-management)

### AI Responsibility

When encountering >6h issues:
1. Alert PM immediately
2. Propose split into 2-4h sub-issues
3. Wait for approval before starting

---

## 📱 Mobile ↔ PC Sync

### Workflow

```
1. PC creates [MOBILE] issue with complete context
2. Mobile reads issue → Works on mobile tasks → Posts findings as comment
3. PC reads Mobile's comment → Implements technical work → Closes issue
```

**Issue Template**: See `.github/ISSUE_TEMPLATE/mobile-task.md`

**Label Flow**: `mobile-task` → `mobile-done-pc-todo` → closed

**PC Actions**: Create mobile issues, implement findings, update docs, commit changes

---

## 📝 Writing Guidelines

**Be concise** - every word costs tokens. New sessions re-read all docs.

| Prefer | Avoid |
|--------|-------|
| Bullets | Paragraphs |
| Tables | Long text |
| 1 example | Multiple examples |
| Direct | Conversational |

---

## 🔨 Commit Convention

Format: `<type>(#issue): description`

**Types**: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`

**Always** reference issue number.

**Examples**:
- `feat(#123): Add authentication module`
- `fix(#45): Correct validation logic`
- `docs(#67): Update API documentation`

---

## 🧪 Testing

- Critical paths must have tests
- Run tests before marking done
- Document test approach in issue

---

## 📚 Documentation

**Update immediately when**:
- Architecture changes → `docs/architecture.md`
- Add dependency → `README.md`, `[DEPENDENCY_FILE]`
- Change API → `docs/api.md`
- Add config → `[CONFIG_FILE]`

---

## 📖 Additional Resources

| Document | Purpose |
|----------|---------|
| [`START_HERE_AI.md`](START_HERE_AI.md) | AI onboarding entry point |
| [`docs/llm-rules.md`](docs/llm-rules.md) | Complete rules for AI |
| [`docs/quick-ref.md`](docs/quick-ref.md) | Command cheatsheet |
| [`docs/architecture.md`](docs/architecture.md) | Technical architecture |
| [`README.md`](README.md) | Project overview |
| `.github/ISSUE_TEMPLATE/mobile-task.md` | Mobile task template |

---

## ❓ Questions?

Create GitHub issue with `question` label.

---

**Last Updated**: [DATE]
**For AI**: Read `START_HERE_AI.md` first
**For Humans**: This document covers the workflow
