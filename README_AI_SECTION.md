# README.md - AI Onboarding Section Template

> **Instructions**: Copy this section and paste it into your project's README.md
> Replace placeholders like [PROJECT_NAME], [AI_TOOL_1], etc. with your actual values

---

## AI Onboarding

**For AI Assistants (Claude, GPT-4, Gemini, etc.)**:

### 🚀 Quick Start
1. Read [`START_HERE_AI.md`](START_HERE_AI.md) (2 min) - Universal entry point
2. Read [`docs/llm-rules.md`](docs/llm-rules.md) (3 min) - Core rules
3. Run status commands:
   ```bash
   gh issue list --state open --limit 5
   git status && git log -3 --oneline
   ```
4. Wait for PM to assign task

### 📚 Documentation Structure

| Priority | Document | Purpose | Read When |
|----------|----------|---------|-----------|
| 🔴 **Start** | `START_HERE_AI.md` | Entry point | First thing |
| 🟡 **Before work** | `docs/llm-rules.md` | Core rules | Before any task |
| 🟢 **As needed** | `README.md` (this) | Project overview | Reference |
| 🟢 **As needed** | `docs/architecture.md` | Technical details | During implementation |
| 🟢 **As needed** | `docs/quick-ref.md` | Command cheatsheet | Quick lookup |
| 🟢 **As needed** | `CONTRIBUTING_TEMPLATE.md` | Workflow details | Reference |
| ⚪ **Skip** | [Add human-only docs] | Human operations | Not for AI |

### 🎯 Key Principles

- **You are an assistant**: Human PM makes decisions, you propose and implement
- **Issue-driven**: All work tracked in GitHub Issues (< 6h per issue)
- **Approval-based**: Propose → Get approval → Implement → Show diff → Get commit approval
- **Context-conscious**: Keep docs concise, every word costs tokens
- **Test-first**: No untested code

**Full details**: [`START_HERE_AI.md`](START_HERE_AI.md)

---

## Collaboration Model

This project uses a unique **human-led** development model with AI assistance:

### Roles

- **Human (You)** - Product Manager & Decision Maker
  - Selects which issues to work on
  - Approves all design decisions and technical approaches
  - Reviews all code via diff tool before accepting
  - Controls development pace and priorities

- **[AI_TOOL_2] (Mobile)** - iOS Operations Specialist (AI Assistant)
  - iOS-specific tasks (app analysis, HTTP capture guidance)
  - Works in GitHub issue threads (via GitHub mobile app)
  - Can read issues and post comments
  - Cannot create files or run git/terminal commands

- **[AI_TOOL_1] (PC)** - Senior Developer (AI Assistant)
  - Proposes solutions with pros/cons
  - Implements after PM approval
  - Has full GitHub **read + write** access
  - Manages GitHub project (issues, docs, commits)
  - **WAITS for PM approval before coding**

- **Important**: Two AI instances are completely independent, no shared context

### Mobile ↔ PC Sync Workflow

```
PC creates [MOBILE] issue with complete context + template
                    ↓
Mobile reads issue (GitHub mobile app) → Works on task
                    ↓
Mobile posts findings as issue comment
                    ↓
PC reads comment → Implements technical work → Closes issue
```

**See**: `.github/ISSUE_TEMPLATE/mobile-task.md` for template and `START_HERE_AI.md` for AI onboarding.

**Management**: GitHub issues as single source of truth

---
