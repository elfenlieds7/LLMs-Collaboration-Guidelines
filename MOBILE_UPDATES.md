# Mobile Discussion Updates

> **Purpose**: This file serves as a bridge between [AI_TOOL_2] (Mobile, design discussions) and [AI_TOOL_1] (PC, implementation).
>
> **Workflow**:
> 1. User discusses with [AI_TOOL_2] (Mobile)
> 2. Mobile AI summarizes discussion
> 3. User pastes summary here
> 4. [AI_TOOL_1] (PC) reads this file and syncs to GitHub
> 5. PC marks as processed

---

## Instructions for [AI_TOOL_1] (PC)

**When you see new content here:**

1. ✅ Read and understand the discussion/decisions
2. ✅ Take the requested actions (create issues, update docs, etc.)
3. ✅ Update GitHub accordingly
4. ✅ Mark the section as "✅ Synced to GitHub" with date
5. ✅ Leave the content for history (don't delete)
6. ✅ Commit changes with reference to this sync

**Example workflow:**
```bash
# 1. Read MOBILE_UPDATES.md
# 2. Create issues, update docs as requested
# 3. Mark as synced
# 4. Commit
git commit -m "feat: Implement feature X based on mobile discussion (MOBILE_UPDATES.md)"
```

---

## [Template - Copy this for new updates]

```markdown
## [YYYY-MM-DD] Topic Title

### Discussion Summary
Brief summary of what was discussed with Mobile AI

### Key Decisions
- Decision 1: Why and what
- Decision 2: Why and what

### Action Items for PC
- [ ] Create issue: Feature X with description
- [ ] Update docs/architecture.md: Add section Y
- [ ] Update [CONFIG_FILE]: Add new setting Z
- [ ] Create ADR: docs/adr/NNN-decision-title.md

### Context/Details
Any additional context that PC needs to understand

### Status
- [ ] Pending PC sync
- [ ] ✅ Synced to GitHub on YYYY-MM-DD

---
```

---

## Update History

<!-- New updates go below this line -->
<!-- Most recent first -->


## Archive

<!-- Processed updates older than 30 days can be moved here -->

<!-- Currently empty -->
