# LLM Collaboration Framework - Setup Guide

> **Purpose**: Guide for setting up this framework in your project
> **Compatibility**: Any LLM (Claude, GPT-4, Gemini, etc.)

---

## 📦 What This Framework Provides

A complete framework for **human-led, multi-agent AI collaboration**:

- ✅ Clear authority: Human decides, AI proposes/implements
- ✅ 200K context management (issues < 6h)
- ✅ Token-efficient documentation
- ✅ Works with any LLM (Claude, GPT-4, Gemini, etc.)
- ✅ Mobile/PC sync workflow
- ✅ Session handoff protocol

---

## 🆕 New Project Setup (5 minutes)

If you're starting a **brand new project**, setup is trivial:

```bash
# 1. Copy files
cp START_HERE_AI.md YOUR_PROJECT/
cp CONTRIBUTING_TEMPLATE.md YOUR_PROJECT/CONTRIBUTING.md  # ← Direct copy
cp -r docs/ YOUR_PROJECT/

# 2. Replace placeholders
find YOUR_PROJECT -type f -name "*.md" -exec sed -i '' \
  's/\[PROJECT_NAME\]/YourProject/g' {} +
# Repeat for: [PROJECT_DESCRIPTION], [TECH_STACK], [AI_TOOL_1], [AI_TOOL_2], [DATE]

# 3. Done!
```

**Why simple?** No existing content to merge, just copy and customize.

---

## 🔄 Integration into Existing Project (Main Guide)

> **This is the real challenge.** Your project already has CONTRIBUTING.md.

### Key Principle

**Don't replace your CONTRIBUTING.md - Merge AI collaboration content into it.**

```
Your existing CONTRIBUTING.md:
├── Getting Started
├── Development Workflow (technical)
├── Testing
└── ...

After integration:
├── Getting Started  (preserved)
├── AI Assistant Collaboration  ← INJECTED from CONTRIBUTING_TEMPLATE.md
├── Technical Development Workflow  (preserved, renamed)
├── Testing  (preserved)
└── ...
```

---

### Prerequisites Check

Before starting, verify:

- [ ] GitHub repository with active development
- [ ] Existing `CONTRIBUTING.md` OR willing to create one
- [ ] Multiple contributors or AI tools in use
- [ ] Issues tracked in GitHub

---

### Step 1: Determine Your Scenario

#### Scenario A: No CONTRIBUTING.md

**Action**: Use CONTRIBUTING_TEMPLATE.md as-is

```bash
cp CONTRIBUTING_TEMPLATE.md YOUR_PROJECT/CONTRIBUTING.md
# Replace placeholders
# Skip to Step 5 (Customize)
```

#### Scenario B: Simple CONTRIBUTING.md (< 100 lines)

**Action**: Use template as base, manually merge your content

```bash
cp YOUR_PROJECT/CONTRIBUTING.md YOUR_PROJECT/CONTRIBUTING.md.backup
cp CONTRIBUTING_TEMPLATE.md YOUR_PROJECT/CONTRIBUTING.md
# Manually add back your project-specific sections
# Replace placeholders
```

#### Scenario C: Mature CONTRIBUTING.md (> 100 lines) ← **Most Common**

**Action**: Extract AI sections from template, inject into your file

**This is complex. Continue to Step 2.**

---

### Step 2: Analyze Conflicts (For Mature Projects)

Open both files side-by-side:
- Your `CONTRIBUTING.md`
- This repo's `CONTRIBUTING_TEMPLATE.md`

Look for these conflicts:

| Your Section | Template Section | Conflict? | Resolution |
|-------------|------------------|-----------|------------|
| "Development Workflow" | "AI Development Workflow" | ✅ Yes | Rename yours to "Technical Development Workflow" |
| "Commit Guidelines" | "Commit Convention" | ⚠️ Partial | Keep yours, add AI requirement (issue #) |
| "Testing" | "Testing" (AI rule) | ⚠️ Partial | Keep yours, add "No untested code" rule |
| "Documentation" | "Documentation" | ⚠️ Partial | Keep yours, add doc update triggers |

**Goal**: Identify where to inject AI sections without breaking existing structure.

---

### Step 3: Extract AI Sections from Template

From `CONTRIBUTING_TEMPLATE.md`, you need these sections:

**Must Extract** (for all projects):
1. ✅ **Roles & Authority** (Human PM, AI assistants)
2. ✅ **Decision Authority Matrix** (table)
3. ✅ **AI Development Workflow** (Propose → Approve → Implement)
4. ✅ **Session Handoff Protocol**
5. ✅ **Issue Size Management** (200K context rule)

**Optional** (skip if not applicable):
6. ⏸ **Mobile ↔ PC Sync** (only if using mobile AI)
7. ⏸ **GitHub Labels** (only if using this label system)

**How to extract**:
- Copy sections from CONTRIBUTING_TEMPLATE.md
- Or see `examples/integrations/CONTRIBUTING_INTEGRATED.md` for example

---

### Step 4: Merge (Inject AI Sections)

**Recommended injection point**: After "Getting Started", before your technical workflow.

**Process**:

1. **Backup first**:
   ```bash
   cp YOUR_PROJECT/CONTRIBUTING.md YOUR_PROJECT/CONTRIBUTING.md.backup
   ```

2. **Create merged version**:
   ```markdown
   # Contributing to [Your Project]

   [Your existing "Getting Started" section]

   ---

   ## AI Assistant Collaboration  ← NEW SECTION (injected)

   > For AI: Read START_HERE_AI.md first

   ### Roles & Authority
   [Copy from CONTRIBUTING_TEMPLATE.md]

   ### Decision Authority Matrix
   [Copy from CONTRIBUTING_TEMPLATE.md]

   ### AI Development Workflow
   [Copy from CONTRIBUTING_TEMPLATE.md]

   ### Session Handoff Protocol
   [Copy from CONTRIBUTING_TEMPLATE.md]

   ### Issue Size Management
   [Copy from CONTRIBUTING_TEMPLATE.md]

   ---

   ## Technical Development Workflow  ← RENAMED (was "Development Workflow")

   [Your existing technical workflow - preserved 100%]

   [All your other existing sections - preserved 100%]
   ```

3. **Optimization** (optional but recommended):
   - Use tables for roles (instead of long lists)
   - Remove dialogue examples, keep steps
   - Link to `docs/llm-rules.md` for details
   - See `examples/integrations/CONTRIBUTING_INTEGRATED.md` for example

---

### Step 5: Add Supporting Files

```bash
# Copy core files
cp START_HERE_AI.md YOUR_PROJECT/
cp docs/llm-rules.md YOUR_PROJECT/docs/
cp docs/quick-ref.md YOUR_PROJECT/docs/
```

---

### Step 6: Customize All Files

#### Replace placeholders everywhere:

| Placeholder | Replace With | Example |
|-------------|--------------|---------|
| `[PROJECT_NAME]` | Your project name | "Nexus" |
| `[PROJECT_DESCRIPTION]` | Brief description | "AI-native filesystem" |
| `[TECH_STACK]` | Main technologies | "Python 3.11+, PostgreSQL, FastAPI" |
| `[AI_TOOL_1]` | PC AI name | "Claude Code" |
| `[AI_TOOL_2]` | Mobile AI name | "Github Mobile" |
| `[DATE]` | Today's date | "2025-10-30" |

**Find & replace**:
```bash
# Mac/Linux
find YOUR_PROJECT -type f -name "*.md" -exec sed -i '' \
  's/\[PROJECT_NAME\]/YourProject/g' {} +

# Repeat for each placeholder
```

#### Customize project-specific content:

**In `docs/llm-rules.md`** (around line 50):
```markdown
**Doc update triggers**:

| Change Type | Update Files |
|-------------|--------------|
| API changes | docs/api/*.md |  ← Your actual doc structure
| Schema changes | docs/database.md |
| Add dependency | requirements.txt |  ← Your dependency file
```

**In `docs/quick-ref.md`**:
```markdown
## Testing

```bash
make test              # Replace with YOUR test command
pytest tests/          # npm test, cargo test, etc.
```

**In `START_HERE_AI.md`** (around line 135):
```markdown
| **Project** | Your Actual Project Name |
| **Description** | Real description |
| **Tech Stack** | Your actual stack |
| **Phase** | Current phase (e.g., "v0.5, active development") |
```

---

### Step 7: Verify Integration

#### File Checklist

```bash
# Check all files exist
ls -la YOUR_PROJECT/START_HERE_AI.md
ls -la YOUR_PROJECT/CONTRIBUTING.md
ls -la YOUR_PROJECT/CONTRIBUTING.md.backup  # backup exists
ls -la YOUR_PROJECT/docs/llm-rules.md
ls -la YOUR_PROJECT/docs/quick-ref.md

# Check no placeholders remain
grep -r '\[PROJECT_NAME\]' YOUR_PROJECT/*.md  # Should be empty
grep -r '\[AI_TOOL' YOUR_PROJECT/*.md         # Should be empty
```

#### Link Verification

Open each file and verify links work:
- [ ] START_HERE_AI.md → docs/llm-rules.md ✓
- [ ] START_HERE_AI.md → CONTRIBUTING.md ✓
- [ ] CONTRIBUTING.md → docs/llm-rules.md ✓
- [ ] All cross-references resolve

#### Content Verification

- [ ] Your original CONTRIBUTING.md content 100% preserved
- [ ] AI collaboration sections present and coherent
- [ ] Project-specific commands updated (not template placeholders)
- [ ] Doc update triggers reflect your actual doc structure

---

### Step 8: Test with AI

**New AI session**:
1. Tell AI: `"Read START_HERE_AI.md"`
2. Check it understands:
   - Its role (assistant, not PM)
   - Reading priorities (Tier 0 → 1 → 2)
   - Where to find information
3. Ask: `"What's your role and workflow?"`
4. Verify response matches: "I propose → You decide → I implement"

---

## 🔧 Advanced: Optional Enhancements

### Claude Skills (Claude Code Pro+ only)

If using Claude Code, add `.claude/skills/multi-agent-onboarding/` to automate:
- `git pull` on session start
- Reading START_HERE_AI.md
- Checking for handoff files

**Others**: Not applicable

### Project-Specific Skills

For standalone tools (like `update_schema.py`):
- Create `.claude/skills/project-tools/`
- Include SKILL.md with usage guide

**Note**: Core modules (imported by app) stay in `src/`, not skills

---

## 🔍 Troubleshooting

### Can't figure out where to inject AI sections

**Solution**: After "Getting Started", before technical workflow. When in doubt: earlier is better.

### Merge conflicts with existing content

**Solutions**:
- Chapter names conflict? Rename yours (e.g., add "Technical")
- Both have guidelines? Keep yours, add AI requirements
- Not sure? Ask: duplicate or separate?

### Docs too long (token waste)

**Solutions**: Use tables/minimal examples, link to details, remove redundancy. Target: ~80 lines for AI sections.

### Mobile section not applicable

**Solution**: Skip "Mobile ↔ PC Sync" when extracting if not using mobile AI.

---

## ✅ Final Checklist

After integration:

**Files**:
- [ ] Backup of original CONTRIBUTING.md exists
- [ ] START_HERE_AI.md has your project info (no placeholders)
- [ ] CONTRIBUTING.md has AI sections injected (not replaced)
- [ ] docs/llm-rules.md has your project's doc triggers
- [ ] docs/quick-ref.md has your actual commands

**Content**:
- [ ] No `[PLACEHOLDER]` strings remain anywhere
- [ ] All internal links work
- [ ] Your original content 100% preserved
- [ ] Project-specific info filled in

**Testing**:
- [ ] AI can successfully onboard (test with real session)
- [ ] AI understands its role (propose, not decide)
- [ ] File sizes reasonable (not bloated)

---

## 📊 Expected Results

### For You (Human PM)
- ✅ Retain 100% authority over decisions
- ✅ AI waits for approval before coding
- ✅ Clear workflow: AI proposes → You approve → AI implements
- ✅ Easy AI onboarding (5 min vs 30+ min)

### For AI Assistants
- ✅ 5-minute onboarding
- ✅ Clear role understanding
- ✅ Know where to find info
- ✅ Proper issue sizing (< 6h)
- ✅ Consistent commits with issue references

### For Your Project
- ✅ All work tracked in GitHub Issues
- ✅ Concise, token-efficient docs
- ✅ Structured AI collaboration (not chaos)

---

## 🎓 Best Practices

### For Integration
1. **Backup first** - Always create .backup before modifying
2. **Analyze conflicts** - Understand what clashes before executing
3. **Ask PM** - Don't assume what's needed
4. **Compress** - Use tables and minimal examples for mature projects
5. **Test early** - Verify with AI session before committing

### For Maintenance
1. **Update dates** when docs change
2. **Keep concise** - Remove outdated content promptly
3. **Document changes** - Note what and why in commit messages

---


## 📚 Resources

- **CONTRIBUTING_TEMPLATE.md**: Full template (source for extraction)
- **examples/integrations/**: Real integration examples (nexus and more)
- **.claude/skills/**: Optional Claude Code automation

---

## 📞 Support

**Issues?** Check [Troubleshooting](#-troubleshooting) or create GitHub issue

---

**Version**: 1.3 (2025-10-30)
**Update**: Integration guide based on real nexus experience
**Key clarification**: CONTRIBUTING_TEMPLATE.md is source for extraction, not direct copy in integration scenarios
