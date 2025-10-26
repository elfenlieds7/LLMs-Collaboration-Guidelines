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

1. Check `MOBILE_UPDATES.md` for pending syncs (process immediately if found)
2. Check project status:
   ```bash
   gh issue list --state open --limit 5
   gh issue list --label in-progress
   git status
   git log -5 --oneline
   ```
3. Wait for PM to assign task

### For Mobile AI

**Every new session**:

1. Check for `[MOBILE]` issues or `mobile-task` label assigned to you
2. Read issue instructions carefully
3. Confirm what you CAN/CANNOT do in mobile environment
4. Guide user through required steps
5. Document findings in `MOBILE_UPDATES.md`

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

## 📱 Mobile ↔ PC Sync Protocol

### Direction 1: Mobile → PC (Discussions & Findings)

**When Desktop AI sees content in MOBILE_UPDATES.md**:

1. ✅ Read and understand decisions/findings
2. ✅ Execute action items (create issues, update docs, etc.)
3. ✅ Update GitHub
4. ✅ Mark section: "✅ Synced to GitHub on YYYY-MM-DD"
5. ✅ Keep content for history (don't delete)
6. ✅ Commit with reference:
   ```bash
   git commit -m "feat: Implement X based on mobile discussion (MOBILE_UPDATES.md)"
   ```

**Template in `MOBILE_UPDATES.md`** - follow it exactly.

### Direction 2: PC → Mobile (Task Assignment)

**When Desktop AI needs Mobile to do platform-specific work**:

1. ✅ Create GitHub issue with `[MOBILE]` prefix in title
2. ✅ Add label `mobile-task` (create label if doesn't exist)
3. ✅ In issue body, clearly specify:
   - What Mobile CAN do (screenshots, app interactions, HTTP capture, guide user, edit MOBILE_UPDATES.md)
   - What Mobile CANNOT do (file creation, git operations, terminal commands)
   - Expected deliverable (usually: entry in MOBILE_UPDATES.md with specific template)
4. ✅ Provide step-by-step instructions
5. ✅ Include template for MOBILE_UPDATES.md entry

**Example scenarios**:
- iOS app API reverse engineering
- Mobile app testing
- Screenshot analysis and UI feedback
- On-device debugging assistance

### For Mobile AI: Processing [MOBILE] Issues

**When you see issue with `[MOBILE]` prefix or `mobile-task` label**:

1. ✅ Read issue carefully
2. ✅ Guide user through mobile operations (app usage, HTTP capture, etc.)
3. ✅ Analyze screenshots/data user provides
4. ✅ Update `MOBILE_UPDATES.md` with findings using provided template
5. ✅ Comment on issue with progress updates
6. ⏸ Let Desktop AI handle file creation, testing, commits

**Your environment capabilities**:
- ✅ CAN: Browse web, analyze images, guide user, edit text files
- ❌ CANNOT: Create project files, run terminal commands, git operations

**Success criteria**: MOBILE_UPDATES.md contains all requested information in the specified format

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
gh issue view <number>
git status
cat MOBILE_UPDATES.md
```

### File Organization

| Content | Location |
|---------|----------|
| LLM entry point | `START_HERE_AI.md` |
| Core rules (this) | `docs/llm-rules.md` |
| Architecture | `docs/architecture.md` |
| Workflow details | `CONTRIBUTING.md` |
| Mobile sync | `MOBILE_UPDATES.md` |
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

**Last Updated**: [DATE]
**Prev File**: `START_HERE_AI.md`
**Next Step**: Check `MOBILE_UPDATES.md`, then wait for PM task assignment
