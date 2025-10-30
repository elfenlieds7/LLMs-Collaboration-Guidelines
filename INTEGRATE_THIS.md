# Integration Guide - For AI Assistants

> **For**: AI assistants integrating this framework into existing projects
> **Purpose**: AI-driven integration process with minimal disruption

---

## Core Philosophy

**Framework provides principles. Destination repo's guidelines remain central.**

---

## Integration Process

### Step 1: Understand Destination Project (CRITICAL)

**Before touching any files:**

1. **Read existing AI guidelines** (`.claude/`, `CONTRIBUTING.md`, AI-specific docs)
   - What workflow exists?
   - What rules are already defined?
   - What file structure is used?

2. **Understand project conventions**
   - How are commits formatted?
   - PR process? (direct push vs PR required?)
   - Testing requirements?
   - Documentation structure?

3. **Identify what's missing** (not what to add)
   - Does project lack AI role definition?
   - Session handoff mechanism missing?
   - Issue sizing guidance absent?
   - Mobile collaboration undefined?

**Output**: Tell PM what you found and what's missing.

---

### Step 2: Propose Integration Plan

**Ask PM**:

```
I've reviewed [PROJECT]'s existing guidelines:

Existing:
- [List what already exists, e.g., ".claude/CLAUDE.md with PR rules"]
- [List existing conventions]

Missing (that framework provides):
- [List gaps, e.g., "Session handoff protocol"]
- [List gaps, e.g., "Issue size management"]

Proposed integration:
- Option A: [Describe minimal approach]
- Option B: [Describe moderate approach]

Recommend: [Your recommendation with reasoning]

Questions:
- [Any conflicts or uncertainties]
```

**Wait for PM approval before proceeding.**

---

### Step 3: Minimal Augmentation

**Golden rule**: Merge into existing files, don't create parallel structure.

#### If project has AI guidelines (e.g., `.claude/CLAUDE.md`):

**Do**:
- ✅ Merge framework principles INTO existing file
- ✅ Keep existing file as primary AI guideline
- ✅ Preserve existing workflow, add missing pieces

**Don't**:
- ❌ Create START_HERE_AI.md alongside existing guidelines (creates confusion)
- ❌ Create docs/llm-rules.md that duplicates content
- ❌ Replace existing structure

**Example**:
```
Existing: .claude/CLAUDE.md (PR rules, deploy process)
Action: Add framework principles to CLAUDE.md, keep it as single AI guide
Result: CLAUDE.md now has both existing rules + framework principles
```

#### If project has NO AI guidelines:

**Do**:
- ✅ Copy START_HERE_AI.md
- ✅ Replace placeholders with project info
- ✅ Integrate into project docs naturally

---

### Step 4: Handle Conflicts

**When existing guidelines conflict with framework**:

1. **Project guidelines win** (deployment, PR rules, commit format, etc.)
2. **Ask PM** if unsure:
   ```
   Conflict found:
   - Project rule: [describe]
   - Framework suggests: [describe]

   How should I resolve this?
   ```

**Example conflicts**:
- Project uses different commit format → Keep project's format, add issue reference requirement
- Project has mobile workflow → Keep it, reference framework for enhancements only
- PR process differs → Follow project's process entirely

---

### Step 5: Preserve Workflow Integration

**Bottom line**: Existing guidelines must remain discoverable and central.

**Check**:
- [ ] If `.claude/CLAUDE.md` existed, is it still the primary AI guide?
- [ ] Are existing conventions preserved 100%?
- [ ] Does new content reference existing guidelines (not replace them)?
- [ ] Would a new AI find existing guidelines first?

**Anti-pattern**:
```
Before integration: .claude/CLAUDE.md (clear, focused)
After integration:  .claude/CLAUDE.md (buried), START_HERE_AI.md (new "main" guide)
Result: Original guidelines lost focus ❌
```

**Correct pattern**:
```
Before: .claude/CLAUDE.md (PR rules)
After:  .claude/CLAUDE.md (PR rules + framework principles merged)
Result: Single cohesive guide ✅
```

---

### Step 6: Verify Integration

**Before committing**:

1. **Read merged docs as if you're a new AI**
   - Are they clear?
   - Is there confusion about which file is "primary"?
   - Are existing guidelines still prominent?

2. **Check file count**
   - How many new files added?
   - Could you have added fewer?
   - Is each new file justified?

3. **Ask PM**: "I've integrated framework. Created/modified X files. Does this seem minimal enough?"

---

## Integration Checklist

- [ ] Read all existing AI guidelines first
- [ ] Identified what's missing (not what to add)
- [ ] Proposed integration plan to PM
- [ ] Got PM approval
- [ ] Merged into existing files (didn't create parallel structure)
- [ ] Preserved existing conventions 100%
- [ ] Existing guidelines remain central
- [ ] Verified as new AI reading docs
- [ ] File count minimized
- [ ] PM reviewed result

---

## Common Mistakes

### Mistake 1: "Framework-First" Thinking

❌ Bad: "Let me add all framework files, then adapt them"
✅ Good: "Let me understand project first, then add only what's missing"

### Mistake 2: Creating Parallel Structure

❌ Bad: Project has CLAUDE.md → I add START_HERE_AI.md → Two AI entry points
✅ Good: Project has CLAUDE.md → I merge framework into it → One entry point

### Mistake 3: Not Asking When Uncertain

❌ Bad: "Project uses different format, I'll just add both"
✅ Good: "Conflict detected, asking PM how to resolve"

### Mistake 4: Over-Engineering

❌ Bad: Added 5 new files for comprehensive coverage
✅ Good: Modified 1-2 files with minimal additions

---

## Success Criteria

**Successful integration means**:

1. ✅ New AI can onboard in ~5 minutes
2. ✅ Existing project conventions 100% preserved
3. ✅ No confusion about "which file to read"
4. ✅ Framework principles present but not dominating
5. ✅ Minimal file count increase (ideally 0-1 new files)

---

**Remember**: You're augmenting, not replacing. The project worked before framework - make it better, don't break it.

---

**Last Updated**: 2025-10-30
**For**: AI assistants performing framework integration
