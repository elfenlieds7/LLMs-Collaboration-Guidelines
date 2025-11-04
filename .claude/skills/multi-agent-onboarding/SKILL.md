---
name: multi-agent-onboarding
description: |
  Onboard AI assistants to multi-agent projects. Automatically:
  - Run git pull to get latest code
  - Read START_HERE_AI.md for project context
  - Check for session handoffs from previous AIs
  - Read project documentation (BUILT_IN_TOOLS.md if exists)

  Invoke when: User says "start", "begin", "onboard", "catch up", or at session start.
---

# Multi-Agent Onboarding

> **Template Skill** - Copy to your project's `.claude/skills/` directory

## When to Activate

Activate at the beginning of every AI session when:
- User says: "start", "begin", "onboard", "catch up"
- Starting a new session
- Returning after a break

## Steps

### Step 1: Pull Latest Changes

```bash
git pull
```

**Why**: Other AIs may have committed changes between sessions.

**Report**: Show commit hash after pull.

### Step 2: Read Entry Point

Read `START_HERE_AI.md` in repo root to understand:
- Project structure and phase
- Core rules and constraints
- Reading priorities (Tier 0→1→2)
- Your role (propose → approve → implement)

### Step 3: Check for Session Handoff

**Issue-based workflow** (see project's CONTRIBUTING.md for handoff format):

1. Check for in-progress issues:
   ```bash
   gh issue list --label in-progress --limit 5
   ```

2. Read issue comments for "🔄 Session Handoff" marker:
   ```bash
   gh issue view <number> --comments
   ```

**If found**: Read the handoff, suggest continuing to PM
**If not found**: Proceed to next step

### Step 4: Read Project-Specific Docs

**If project has BUILT_IN_TOOLS.md**:
- Read it to know available tools/modules
- Avoid reimplementing existing functionality

**If project has other must-read docs**:
- Listed in START_HERE_AI.md Tier 1
- Read those before starting work

### Step 5: Check Project Status

Run:
```bash
gh issue list --state open --limit 5
git log -3 --oneline
```

Get quick overview of:
- Open issues
- Recent commits

### Step 6: Report Ready

Output format:
```
✅ Pulled to: [commit hash]
✅ START_HERE_AI.md: Read
✅ Handoff: [Found in issue #X / Not found]
✅ Project docs: [List what was read]
✅ Open issues: [count]
⏸ Ready for task assignment
```

## Customization

When copying to your project:
1. Keep Steps 1-3 (universal)
2. Update Step 4 with project-specific docs
3. Add project-specific checks in Step 5 if needed

## Important Notes

- **Wait for PM** to assign task (don't pick issues yourself)
- **This skill is optional** - other AIs follow START_HERE_AI.md manually
- **START_HERE_AI.md is source of truth** - this skill just automates it

## For Non-Claude AIs

If you're not using Claude Code:
1. Manually run `git pull`
2. Read `START_HERE_AI.md`
3. Follow the checklist in that file

---

**Template Version**: 1.0
**Last Updated**: 2025-10-29
**Compatibility**: Claude Code (auto-load), Other AIs (read manually)
