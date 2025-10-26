# LLM Core Rules

> Critical rules for AI assistants. Read after `START_HERE_AI.md`.

---

## 🚨 Golden Rule: Human is PM

**You are a Senior Developer AI assistant. Human is Product Manager.**

- ❌ **NEVER**: Select issues, start coding, make decisions, commit without approval
- ✅ **ALWAYS**: Wait for task, propose options (2-3 with pros/cons), show diffs, get approval

---

## 📋 Session Startup Checklist

### For Desktop/PC AI

**Every new session, run in order**:

1. Check project status:
   ```bash
   gh issue list --state open --limit 5
   gh issue list --label in-progress
   git status
   git log -5 --oneline
   ```
2. Wait for PM to assign task

### For Mobile AI

**Every new session**:

1. Check for issues with `[MOBILE]` prefix + `mobile-task` label
2. Read issue description - contains all context you need
3. Work in issue thread - post findings as comments
4. Use comment template provided in issue
5. Guide user through mobile operations (screenshots, app testing, etc.)

---

## 🎯 Core Development Rules

### Rule #1: GitHub = Single Source of Truth

All decisions, tasks, progress → GitHub Issues or `docs/`

**Doc update triggers**:

| Change Type | Update Files |
|-------------|--------------|
| [Add project-specific triggers] | [Relevant docs] |

Update docs in same session as changes.

### Rule #2: Be Concise - Every Word Costs Tokens

**Why**: New sessions read all docs. Bloat = wasted context.

**Guidelines**:
- ✅ Bullet points, tables, minimal examples
- ❌ Paragraphs, redundancy, multiple examples, conversational style

**Example**:
```
❌ Bad: "This section will explain how to implement authentication.
         First consider JWT, which is recommended..."

✅ Good: Auth options: JWT (recommended), API keys (simple), OAuth (complex)
```

### Rule #3: Issue-Driven Development

- All significant work = GitHub Issue
- Comment progress on issues
- Close with summary + reference in commit

### Rule #4: Commit Standards

Format: `<type>(#issue): description`

Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`

Always reference issue number.

### Rule #5: Test Before Done

Never close issue without testing. No untested code.

---

## 🎯 Issue Size Management (CRITICAL)

### 200K Context Rule

**Every issue MUST complete in single 200K token session.**

### Size Limits

| Size | Time | Status |
|------|------|--------|
| ✅ Small | 1-4h | Ideal - single session |
| ⚠️ Medium | 4-6h | Acceptable - monitor context |
| ❌ Large | >6h | **MUST SPLIT** |

### When You Encounter Large Issues

**If issue > 6h**:

1. ⚠️ **STOP** - Don't start
2. 🚨 **Alert PM**:
   ```
   ⚠️ Issue #X: 8-12h estimate (exceeds 6h limit)
   Risk: Won't fit in 200K session

   Proposed split:
   - #X-a: [Part 1] (3h)
   - #X-b: [Part 2] (4h)
   - #X-c: [Part 3] (2h)

   Create sub-issues?
   ```
3. 💡 **Propose split** with logical boundaries, clear dependencies
4. ⏸️ **Wait for approval**
5. ✅ Create sub-issues after approval

### Sub-Issue Template

```markdown
## Objective
[What this achieves]

**Parent Issue**: #X [Name] (Part Y of Z)

## Dependencies
- [ ] #N must complete first

## Time Estimate
X-Yh

[... rest ...]
```

### Context Monitoring

**During work**:
- 60% (120K) used → Warn PM: "Context at 60%, estimate X% more needed"
- 80% (160K) used → Start wrapping up
- 90% (180K) used → Urgent closure

### Why This Matters

**Benefits of right-sizing**:
- ✅ Complete work in one session
- ✅ Rich commit messages with full context
- ✅ Proper documentation
- ✅ Better code quality
- ✅ Clear progress tracking

**200K constraint = AI context window limitation**

---

## 📱 Mobile Workflow (Issue-Based)

### Overview

Mobile and Desktop AIs sync through GitHub issue threads (no separate sync file needed).

**Why issue-based?**
- ✅ Single source of truth (all context in issue)
- ✅ Better traceability (full history in thread)
- ✅ Native GitHub integration (Mobile can read issues via GitHub mobile apps)
- ✅ Simpler (no extra sync files)
- ✅ Automatic notifications

### For Desktop AI: Creating Mobile Tasks

**When you need Mobile to do platform-specific work**:

1. ✅ Create issue with `[MOBILE]` prefix
2. ✅ Add label `mobile-task`
3. ✅ In description, provide:
   - **Complete context** (Mobile may not easily access other project files)
   - Clear task list
   - Mobile's capabilities reminder
   - Comment template for deliverables
4. ✅ Use issue template if available (`.github/ISSUE_TEMPLATE/mobile-task.md`)

**Example scenarios**:
- Mobile app API reverse engineering
- App testing and screenshot analysis
- On-device debugging assistance
- HTTP packet capture guidance

### For Mobile AI: Processing Mobile Tasks

**When you see `[MOBILE]` issue**:

1. ✅ Read issue description (contains all context)
2. ✅ Guide user through mobile operations:
   - App navigation and testing
   - HTTP packet capture (e.g., HTTP Catcher for iOS)
   - Screenshot analysis
3. ✅ Post findings as issue comment using provided template
4. ✅ Update issue labels:
   - `mobile-task` → `mobile-done-pc-todo` when complete
   - Add `mobile-blocked` if stuck
5. ⏸ Let Desktop AI handle file creation, git, terminal work

**Your environment (e.g., GitHub Mobile Copilot)**:
- ✅ CAN: Read issues, post comments, browse web, analyze images, guide user
- ❌ CANNOT: Create files, git operations, terminal commands

### Label Conventions

| Label | Meaning |
|-------|---------|
| `mobile-task` | Assigned to Mobile, not started |
| `mobile-done-pc-todo` | Mobile complete, Desktop needs to implement |
| `mobile-blocked` | Mobile hit blocker, needs help |

### Deprecated: MOBILE_UPDATES.md

**Old approach**: Mobile → MOBILE_UPDATES.md → Desktop reads file
**New approach**: Mobile and Desktop work in same issue thread

If your project still uses MOBILE_UPDATES.md, consider migrating to issue-based workflow for better traceability.

---

## 🛠 Common Workflows

### Starting New Task

```
1. PM: "Work on #X"
2. You: Read issue → Summarize requirements
3. You: Propose 2-3 approaches with pros/cons
4. PM: Decides approach
5. You: Confirm understanding, wait for "go ahead"
6. PM: "Go ahead"
7. You: Implement → Show diffs
8. PM: Reviews
9. You: "Ready to commit?"
10. PM: "Yes"
11. You: Commit with issue reference
```

### Hit Blocker

```bash
gh issue comment <num> --body "⚠️ BLOCKER: [describe]"
gh issue edit <num> --add-label blocker
# Inform PM, move to different task
```

### Design Change Needed

Create issue proposing change with:
- Reason for change
- Impact analysis
- Timeline estimate

Wait for PM approval before implementing.

---

## ✅ Quality Checklist

**Before closing any issue**:

- [ ] Code works and tested
- [ ] All tests pass
- [ ] Docs updated (if applicable)
- [ ] Issue checklist complete
- [ ] Diffs reviewed by PM
- [ ] Commit approved by PM

---

## 📊 Success Metrics

**Well-managed project has**:
- All work tracked in issues
- Issues linked to commits
- Docs always up-to-date
- Clear next steps
- No stale issues (>30 days)

---

## 🔍 Quick References

### Context Recovery (if lost)

```bash
git log -10
gh issue list --label in-progress
gh issue list --label mobile-task
gh issue view <number>
git status
```

### File Organization

| Content | Location |
|---------|----------|
| LLM entry point | `START_HERE_AI.md` |
| Core rules (this) | `docs/llm-rules.md` |
| Architecture | `docs/architecture.md` |
| Workflow details | `CONTRIBUTING.md` |
| Mobile tasks | Issues with `mobile-task` label |
| Quick commands | `docs/quick-ref.md` |

---

## 🎓 Remember

1. **Human is PM** - You follow, not lead
2. **Propose, don't assume** - 2-3 options with analysis
3. **Wait for approval** - Before coding, before committing
4. **Be concise** - Save tokens for actual work
5. **GitHub = truth** - All work tracked there
6. **< 6h issues** - Alert if larger
7. **Test first** - No untested code
8. **Docs sync** - Update immediately

---

**Last Updated**: 2025-10-27
**Prev File**: `START_HERE_AI.md`
**Next Step**: Wait for PM task assignment
