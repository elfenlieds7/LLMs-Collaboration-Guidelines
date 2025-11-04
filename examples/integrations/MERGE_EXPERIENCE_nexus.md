# Merge Experience Record - nexus CONTRIBUTING.md

> **Project**: nexi-lab/nexus
> **Date**: 2025-10-30
> **Scenario**: Type 3 - Mature project with comprehensive CONTRIBUTING.md (246 lines)

---

## 📊 Document Structure Analysis

### Nexus CONTRIBUTING.md (Existing)
```
1. Getting Started
   - Prerequisites
   - Development Setup
2. Development Workflow (Technical)
   - Making Changes
   - Code Style
   - Testing
   - Type Checking
3. Pull Request Process
4. Code Structure
5. Commit Message Guidelines (Conventional Commits)
6. Architecture Guidelines
7. Documentation (Google docstrings)
8. Getting Help
9. License
```

### Framework CONTRIBUTING_TEMPLATE.md
```
1. Quick Start
2. Roles & Authority (Human PM, AI assistants)
3. Decision Authority Matrix
4. Development Workflow (AI collaboration: Propose → Approve → Implement)
5. Session Handoff Protocol
6. Issue Size Management (200K context)
7. GitHub Labels (SSOT principle)
8. Mobile ↔ PC Sync
9. Writing Guidelines
10. Commit Convention
11. Testing (high-level rules)
12. Documentation (update triggers)
```

---

## 🔍 Identified Conflicts

### Conflict 1: "Development Workflow" - Chapter Name Collision
**Problem**: Both documents have this chapter, but different meanings
- **Nexus**: Technical workflow (git branches, formatting, linting)
- **Framework**: AI collaboration workflow (propose → approve → implement)

**Solution**:
- Keep framework's "Development Workflow" for AI collaboration (more important for AI)
- Rename nexus's chapter to "Technical Development Workflow"

**Rationale**: AI needs to understand collaboration model before technical details

---

### Conflict 2: Commit Message Guidelines
**Problem**: Both documents define commit conventions
- **Nexus**: Conventional commits with detailed examples
- **Framework**: Generic commit format template

**Solution**:
- Keep nexus's detailed "Commit Message Guidelines" section
- Framework references it instead of duplicating

**Change in merged doc**:
```markdown
## Commit Convention

See [Commit Message Guidelines](#commit-message-guidelines) below for detailed format.

**Key requirement for AI**: Always reference issue number in commits.
**human**: adopt this requirements for template repo, this is benefitial for AI works.
```

---

### Conflict 3: Testing
**Problem**: Both documents have testing sections
- **Nexus**: Technical details (pytest, coverage, mypy)
- **Framework**: High-level rule ("No untested code")

**Solution**:
- Keep nexus's technical "Testing" section in "Technical Development Workflow"
- Add framework's rule to "AI Collaboration" section

---

### Conflict 4: Documentation
**Problem**: Both documents have documentation sections
- **Nexus**: Technical details (Google docstrings, examples)
- **Framework**: Update triggers ("When to update docs")

**Solution**:
- Keep nexus's technical "Documentation" section
- Merge framework's update triggers into it

---

### Conflict 5: Mobile ↔ PC Sync
**Problem**: Framework includes mobile AI collaboration
- **Initial assumption**: Desktop-only project
- **Correction (from PM)**: Nexus DOES use Github Mobile for mobile AI collaboration

**Solution**: **Keep this section** - Nexus uses Github Mobile ↔ Claude Code workflow

**Lesson**: Don't assume - always verify project needs with PM before removing sections

---

## ✅ Merge Strategy

### Injection Point
**Insert AI collaboration sections AFTER "Getting Started", BEFORE "Technical Development Workflow"**

Reasoning:
- AI reads role definition first
- Then understands technical workflow in proper context
- Logical flow: Who I am → How we work → Technical details

### Structure of Merged Document
```
1. [KEEP] Getting Started (nexus)

--- INSERT AI COLLABORATION SECTIONS HERE ---

2. [NEW] AI Assistant Collaboration
   2.1 Roles & Authority (framework)
   2.2 Decision Authority Matrix (framework)
   2.3 AI Development Workflow (framework)
   2.4 Session Handoff Protocol (framework)
   2.5 Issue Size Management (framework)
   2.6 GitHub Labels Principle (framework)
   2.7 Mobile ↔ PC Sync (framework) [KEEP - nexus uses Github Mobile]

--- END AI SECTIONS ---

3. [RENAME] Technical Development Workflow (was "Development Workflow")
   3.1 [KEEP] Making Changes (nexus)
   3.2 [KEEP] Code Style (nexus)
   3.3 [KEEP] Testing (nexus)
   3.4 [KEEP] Type Checking (nexus)

4. [KEEP] Pull Request Process (nexus)

5. [KEEP] Code Structure (nexus)

6. [KEEP] Commit Message Guidelines (nexus)
   [ADD] Note: AI must always reference issue numbers

7. [KEEP] Architecture Guidelines (nexus)

8. [MERGE] Documentation (nexus + framework update triggers)

9. [KEEP] Getting Help (nexus)

10. [KEEP] License (nexus)
```

---

## 📝 Placeholder Replacements Needed

From framework template:
- `[AI_TOOL_1]` → "Claude Code" (based on .claude/CLAUDE.md existence)
- `[AI_TOOL_2]` → "Github Mobile" (PM confirmed mobile AI collaboration needed)
- `[PROJECT_NAME]` → "Nexus"
- `[DATE]` → "2025-10-30"

---

## ⚠️ Special Considerations

### 1. Existing .claude/CLAUDE.md
**Status**: Nexus already has `.claude/CLAUDE.md` with PR/deploy workflows

**Strategy**:
- Keep `.claude/CLAUDE.md` for operational procedures (PR, PyPI release, GCP deploy)
- New `START_HERE_AI.md` references it: "See `.claude/CLAUDE.md` for PR and deployment procedures"
- Clear separation: START_HERE_AI = onboarding, CLAUDE.md = operations

### 2. Conventional Commits Already in Use
**Status**: Nexus already uses conventional commits extensively

**Strategy**: Framework adapts to project, not reverse
- Keep nexus's detailed commit guidelines
- Framework just adds AI-specific requirement (issue references)

### 3. Comprehensive Existing Documentation
**Status**: Nexus has 12+ doc directories, very complete

**Strategy**: Framework doesn't replace, it augments
- All existing docs remain
- AI collaboration layer sits on top

---

## 🎯 Success Criteria

After merge, the document should:
- ✅ Preserve 100% of existing technical content
- ✅ Add clear AI role definitions and collaboration workflow
- ✅ Have no contradictions between sections
- ✅ Feel like a natural evolution, not a forced insertion
- ✅ Maintain nexus's professional tone and formatting style

---

## 📊 Metrics

- **Original nexus CONTRIBUTING.md**: 246 lines
- **Estimated merged version**: ~450-500 lines
- **New content**: ~200-250 lines (AI collaboration)
- **Modified content**: ~10 lines (cross-references, minor adjustments)
- **Deleted content**: 0 lines

---

## 🔄 Feedback to Framework Template

### Improvement 1: Commit Issue Reference Requirement
**Source**: PM feedback on line 79

**Current state in framework**: Generic commit format, no explicit issue reference requirement

**Proposed change**: Update `docs/llm-rules.md` - Rule #4: Commit Standards
```markdown
Format: `<type>(#issue): description`

**ALWAYS reference issue number** - This is critical for:
- Tracing every code change to its task
- AI context recovery across sessions
- Code archaeology and debugging
```

**Rationale**: PM confirmed this is beneficial for AI work and should be adopted in template

---

### Improvement 2: Optional Section Markers
**Source**: Initial wrong assumption about Mobile sync

**Current state in framework**: All sections appear equally important

**Proposed change**: Mark optional sections in CONTRIBUTING_TEMPLATE.md
```markdown
## 📱 Mobile ↔ PC Sync [OPTIONAL - skip if no mobile AI workflow]
```

**Rationale**: Helps integrators quickly identify which sections can be skipped

---

### Improvement 3: Token Efficiency - Compress AI Sections
**Source**: PM feedback on merged draft - "too verbose, wastes tokens"

**Problem**: AI collaboration sections in template are too detailed:
- Role definitions list every permission redundantly
- Workflow examples include full dialogue snippets
- Session handoff protocol needs to use GitHub issues
- Code examples are verbose

**Current token cost**: ~200-250 lines for AI collaboration sections

**Proposed changes**:
1. **Roles**: Use bullet lists instead of separate paragraphs
2. **Workflow**: Remove dialogue examples, keep numbered steps only
3. **Session Handoff**: Use GitHub issues instead of local files
4. **Code blocks**: Keep only essential commands

**Target**: Reduce AI sections by 30-40% (~140-170 lines instead of 200-250)

**Rationale**:
- AI reads CONTRIBUTING.md every session
- Conciseness principle applies to framework itself
- Essential info can fit in much less space

**Action**: Create "CONTRIBUTING_TEMPLATE_COMPACT.md" variant for mature projects

---

## 🔄 Application Process

### Files Applied to Nexus (Local)

**Date**: 2025-10-30

#### New Files Created:
1. ✅ `/nexus/START_HERE_AI.md` (6.3KB)
   - Customized with Nexus project info
   - Placeholders replaced: PROJECT_NAME, DESCRIPTION, TECH_STACK, etc.
   - Links to `.claude/CLAUDE.md` for PR/deploy procedures

2. ✅ `/nexus/docs/llm-rules.md` (9.5KB)
   - Complete AI rules for Nexus
   - Nexus-specific testing commands
   - Doc update triggers table customized for Nexus structure

3. ✅ `/nexus/docs/quick-ref.md` (4.5KB)
   - Quick command reference
   - Nexus project structure
   - Common development patterns

#### Modified Files:
1. ✅ `/nexus/CONTRIBUTING.md` (6.0KB, was 246 lines, now ~290 lines)
   - Backup created: `CONTRIBUTING.md.backup`
   - Used COMPACT version (68% reduction in AI sections)
   - Preserved 100% of original technical content
   - Added AI collaboration sections (80 lines)

#### Existing Files Referenced (Not Modified):
- ✅ `.claude/CLAUDE.md` - Kept as operational procedures
- ✅ `README.md` - No changes
- ✅ `docs/` - Existing docs preserved

### Verification Results

**All links verified**:
- ✅ START_HERE_AI.md → docs/llm-rules.md ✓
- ✅ START_HERE_AI.md → CONTRIBUTING.md ✓
- ✅ START_HERE_AI.md → .claude/CLAUDE.md ✓
- ✅ CONTRIBUTING.md → docs/llm-rules.md ✓
- ✅ CONTRIBUTING.md → .claude/CLAUDE.md ✓
- ✅ docs/llm-rules.md → START_HERE_AI.md ✓
- ✅ docs/quick-ref.md → llm-rules.md ✓

**File sizes**:
```
6.3KB   START_HERE_AI.md
6.0KB   CONTRIBUTING.md (was 246 lines)
9.5KB   docs/llm-rules.md
4.5KB   docs/quick-ref.md
---
26.3KB  Total new/modified AI collaboration docs
```

### Token Efficiency Achieved

**Before**: Original framework template sections = ~250 lines
**After**: Compressed sections = ~80 lines
**Reduction**: 68% compression

**Result**: Nexus AI collaboration docs add minimal token overhead while providing complete guidance.

---

## 🔄 Next Steps

1. ✅ Analysis complete (with PM corrections)
2. ✅ Draft merged CONTRIBUTING.md (COMPACT version)
3. ✅ Apply to nexus local
4. 🔄 Review with PM for approval
5. ⏸ Test with AI onboarding (new session, say "start")
6. ⏸ Apply feedback to framework template repo

---

**Status**: Applied to nexus local, ready for PM review and testing