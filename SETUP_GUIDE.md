# LLM Collaboration Framework - Setup Guide

> **Purpose**: Guide for setting up this multi-agent collaboration framework in your project
> **Time**: 15-20 minutes
> **Compatibility**: Any LLM (Claude, GPT-4, Gemini, etc.)

---

## 📦 What's Included

This template package provides a complete framework for **human-led, multi-agent AI collaboration**:

**Core Documents**:
- `START_HERE_AI.md` - Universal LLM entry point
- `docs/llm-rules.md` - Complete rules for AI assistants
- `docs/quick-ref.md` - Command reference
- `CONTRIBUTING_TEMPLATE.md` - Workflow documentation
- `templates/ISSUE_TEMPLATE_mobile.md` - Mobile task issue template
- `README_AI_SECTION.md` - README template

**Key Features**:
- ✅ Works with any LLM (Claude, GPT-4, Gemini, etc.)
- ✅ Clear authority: Human decides, AI proposes/implements
- ✅ 200K context management (issues < 6h)
- ✅ Mobile/PC sync workflow
- ✅ Token-efficient documentation
- ✅ Tiered reading strategy (🔴🟡🟢⚪)

---

## 🚀 Quick Setup (5 Steps)

### Step 1: Copy Files to Your Project

```bash
# Copy all template files to your project root
cp llm-collaboration-template/START_HERE_AI.md YOUR_PROJECT/
cp llm-collaboration-template/CONTRIBUTING_TEMPLATE.md YOUR_PROJECT/

# Copy docs and templates
cp -r llm-collaboration-template/docs YOUR_PROJECT/
cp -r llm-collaboration-template/templates YOUR_PROJECT/

# Optional: Copy mobile issue template to GitHub
mkdir -p YOUR_PROJECT/.github/ISSUE_TEMPLATE
cp YOUR_PROJECT/templates/ISSUE_TEMPLATE_mobile.md YOUR_PROJECT/.github/ISSUE_TEMPLATE/mobile-task.md
```

### Step 2: Customize Placeholders

Replace these placeholders in **all files**:

| Placeholder | Replace With | Example |
|-------------|--------------|---------|
| `[PROJECT_NAME]` | Your project name | "MyApp" |
| `[PROJECT_DESCRIPTION]` | Brief description | "E-commerce platform" |
| `[ARCHITECTURE_SUMMARY]` | Tech overview | "React + Node.js + PostgreSQL" |
| `[TECH_STACK]` | Main technologies | "TypeScript, React, Express" |
| `[CURRENT_PHASE]` | Development phase | "MVP Development" |
| `[AI_TOOL_1]` | PC AI name | "Claude Code", "GitHub Copilot" |
| `[AI_TOOL_2]` | Mobile AI name | "Claude Mobile", "ChatGPT" |
| `[DATE]` | Today's date | "2025-10-26" |
| `[YOUR_TEST_COMMAND]` | Test command | "npm test", "pytest" |
| `[YOUR_INSTALL_COMMAND]` | Install deps | "npm install", "pip install -r requirements.txt" |
| `[DEPENDENCY_FILE]` | Dependency file | "package.json", "requirements.txt" |
| `[CONFIG_FILE]` | Config file | ".env", "config.yml" |

**Find & Replace**:
```bash
# On Mac/Linux
find YOUR_PROJECT -type f -name "*.md" -exec sed -i '' 's/\[PROJECT_NAME\]/MyApp/g' {} +

# On Windows (PowerShell)
Get-ChildItem -Path YOUR_PROJECT -Filter *.md -Recurse | ForEach-Object {
    (Get-Content $_.FullName) -replace '\[PROJECT_NAME\]', 'MyApp' | Set-Content $_.FullName
}
```

### Step 3: Add AI Onboarding Section to README

Open `README_AI_SECTION.md`, customize it, and paste into your `README.md`:

```markdown
# Your Project Name

[Your existing content...]

---

[PASTE CUSTOMIZED AI ONBOARDING SECTION HERE]

---

## License
[...]
```

### Step 4: Customize Project-Specific Content

**`docs/llm-rules.md`**:
- Add project-specific doc update triggers (line ~30)

**`docs/quick-ref.md`**:
- Add your test commands
- Add your project-specific commands (build, lint, etc.)

**`START_HERE_AI.md`**:
- Add human-only docs to Tier 3 (line ~50)
- Fill in "Project Quick Facts" table (line ~90)

### Step 5: Verify Setup

Create a checklist issue in GitHub:

```markdown
## Setup Verification

- [ ] All files copied and placeholders replaced
- [ ] README.md has AI Onboarding section
- [ ] Project-specific commands added to quick-ref.md
- [ ] Mobile task labels created (`mobile-task`, `mobile-done-pc-todo`, `mobile-blocked`)
- [ ] Tested with at least one AI assistant
```

---

## 📋 Complete File Checklist

After setup, your project should have:

```
YOUR_PROJECT/
├── START_HERE_AI.md          ✅ LLM entry point
├── CONTRIBUTING_TEMPLATE.md  ✅ Workflow guide
├── README.md                  ✅ (with AI Onboarding section added)
├── .github/
│   └── ISSUE_TEMPLATE/
│       └── mobile-task.md    ✅ Mobile task template
├── templates/
│   └── ISSUE_TEMPLATE_mobile.md  ✅ Template source
└── docs/
    ├── llm-rules.md          ✅ Core AI rules
    ├── quick-ref.md          ✅ Command reference
    └── architecture.md        📝 (create if not exists)
```

---

## 🔧 Customization Guide

### For Different Project Types

#### Web App (Frontend + Backend)
- Update quick-ref.md with: `npm run dev`, `npm run build`, `npm test`
- Add to Tier 3 (skip): Deployment scripts, CI/CD configs

#### Python Project
- Update quick-ref.md with: `pytest`, `pip install -r requirements.txt`
- Add to Tier 3 (skip): Virtual env setup, deployment scripts

#### Mobile App
- Update quick-ref.md with: `npm run ios`, `npm run android`
- Add to Tier 3 (skip): Signing configs, store deployment

### For Different AI Tools

#### Using OpenAI GPT-4
- Replace `Claude Code` → `GPT-4` in CONTRIBUTING_TEMPLATE.md
- Replace `Claude Mobile` → `ChatGPT` in CONTRIBUTING_TEMPLATE.md

#### Using Google Gemini
- Replace `Claude Code` → `Gemini` in CONTRIBUTING_TEMPLATE.md
- May need to adjust context limits if Gemini has different limits

#### Using Multiple Tools
- Keep `[AI_TOOL_1]` and `[AI_TOOL_2]` generic
- Document which tool is used where in README

### Adding Project-Specific Rules

Create `docs/project-rules.md` for additional rules:
```markdown
# Project-Specific Rules

## Code Style
- [Your conventions]

## Testing Requirements
- [Your requirements]

## Deployment Process
- [Your process]
```

Add to Tier 2 in START_HERE_AI.md.

---

## 🧪 Testing Your Setup

### Test 1: New LLM Onboarding

1. Open a new AI assistant session
2. Tell it: `"Read START_HERE_AI.md"`
3. Verify it understands:
   - Its role (assistant, not decision maker)
   - Reading priority (🔴→🟡→🟢→⚪)
   - Where to find information

### Test 2: Mobile Workflow

1. Create a test mobile task issue using the template
2. Tell Mobile AI (if available): `"Check for mobile tasks"`
3. Verify workflow:
   - Mobile reads issue
   - Mobile posts findings as comment
   - PC reads comment and acts on it
   - Issue gets closed

**Alternative test (PC only)**:
- Create a `[MOBILE]` issue manually
- Verify PC recognizes mobile task labels

### Test 3: Issue Size Management

1. Create a large issue (>6h estimate)
2. Tell AI: `"Let's work on #X"`
3. Verify it:
   - Recognizes it's too large
   - Alerts you
   - Proposes split into sub-issues
   - Waits for approval

---

## 📊 Expected Outcomes

After setup, you should see:

### For Human PM
- ✅ Clear authority over all decisions
- ✅ AI waits for approval before coding
- ✅ Structured proposal → approval → implementation workflow
- ✅ Easy to onboard new AI tools (just point to START_HERE_AI.md)

### For AI Assistants
- ✅ 5-minute onboarding time
- ✅ Clear understanding of role and constraints
- ✅ Know where to find information
- ✅ Proper issue sizing (< 6h per issue)
- ✅ Consistent commit messages

### For Project
- ✅ All work tracked in GitHub Issues
- ✅ Clean, concise documentation
- ✅ Mobile/PC collaboration works smoothly
- ✅ Context-efficient (saves tokens)

---

## 🔍 Troubleshooting

### AI doesn't follow rules

**Problem**: AI starts coding without approval

**Solution**:
1. Point it to: `"Read docs/llm-rules.md section 'Golden Rule'"`
2. Remind: `"Wait for my approval before implementing"`
3. If persistent, add to your session prompt

### AI reads too many docs

**Problem**: AI wastes context reading everything

**Solution**:
1. Emphasize START_HERE_AI.md tiered approach
2. Tell it: `"Only read 🔴 and 🟡 tiers initially"`
3. Add: `"Read 🟢 tier only when needed"`

### Mobile workflow not working

**Problem**: Mobile AI can't find mobile tasks

**Solution**:
1. Verify labels exist: `mobile-task`, `mobile-done-pc-todo`, `mobile-blocked`
2. Create labels: `gh label create mobile-task --color "FFA500"`
3. Ensure issues have `[MOBILE]` prefix in title
4. If using GitHub mobile app, verify Copilot access

### Issues are too large

**Problem**: Issues consistently exceed 6h

**Solution**:
1. Break down features more granularly
2. Use parent issues + sub-issues structure
3. Train AI to alert earlier (at estimation phase)

---

## 🎓 Best Practices

### For Humans

1. **Always review diffs** before approving commits
2. **Provide clear requirements** when assigning issues
3. **Be explicit** with approval: "Yes, go ahead" not just "ok"
4. **Keep issues small** (< 6h) from the start

### For Teams

1. **Onboard new members** with this same framework
2. **Document project-specific patterns** in project-rules.md
3. **Review AI-generated code** in pull requests
4. **Iterate on the workflow** based on team feedback

### For Long-Term Maintenance

1. **Update dates** when docs change
2. **Keep docs concise** - remove outdated content
3. **Close stale mobile issues** (> 30 days)
4. **Version your templates** if you make significant changes

---

## 📚 Additional Resources

### Understanding the Framework

- **Why 200K limit?** - AI context window constraints
- **Why < 6h issues?** - Ensures completion in single session
- **Why tiered reading?** - Faster onboarding, less context waste
- **Why approval-based?** - Human maintains control and oversight

### Adapting for Scale

**Small team (1-3 people)**:
- Can be more informal with approvals
- Single AI tool might be sufficient

**Medium team (4-10 people)**:
- Strict approval process important
- Multiple AI tools for different roles
- Regular sync meetings about AI usage

**Large team (10+ people)**:
- Standardized templates critical
- Team-specific rule documents
- Designated "AI coordinators"

---

## 🎁 Optional: Claude Skills Enhancement

> **Optional** - Only relevant if using Claude Code with Pro/Team/Enterprise

### What is This?

This repo includes a **Skills template** (`.claude/skills/multi-agent-onboarding/`) that automates session start for Claude Code users.

**For Claude Code users**: Skills auto-load and reduce manual steps
**For other AIs**: Not applicable, continue with START_HERE_AI.md

### Setup Decision

**Ask the user**:
```
"Are you using Claude Code with Pro/Team/Enterprise subscription?
- Yes → I'll copy the skills template to your project
- No → Skip this (can add later if you switch to Claude)"
```

**If Yes (Claude doing setup)**:
1. Copy `.claude/skills/` from this repo to project
2. Customize if needed (project-specific docs in SKILL.md)
3. Commit to git
4. Done - skills will auto-load on restart

**If Yes (Other AI doing setup)**:
- Tell user: "Skills setup requires Claude Code. When you have it, copy `.claude/skills/` from template repo to your project."

**If No**:
- Skip this section entirely

### Creating Project-Specific Skills

If project has **independent tools** (standalone scripts like `update_schema.py`):
- Consider creating `.claude/skills/project-tools/`
- Include SKILL.md (usage guide) + scripts
- Core modules (imported by app) stay in `src/`

**For Claude**: You know how to create skills - use this repo's skill as reference

**For other AIs**: Suggest this to user for future when they have Claude Code

---

## 🎯 Next Steps

After setup:

1. ✅ Test the framework with a small task
2. ✅ Adjust templates based on your project needs
3. ✅ Train team members on the workflow
4. ✅ Iterate and improve based on experience

**Questions or issues?** Create a GitHub issue or discussion in your project.

---

## 📝 Version History

- **v1.2** (2025-10-29): Claude Skills enhancement
  - Added `.claude/skills/` template (optional)
  - Updated SETUP_GUIDE.md with Skills section
  - Compressed session templates (75-84% token reduction)
  - Skills = enhancement, not dependency
- **v1.1** (2025-10-27): Issue-based mobile workflow
  - Replaced MOBILE_UPDATES.md with issue-based sync
  - Added mobile task issue template
  - Improved traceability
- **v1.0** (2025-10-26): Initial template release
  - Core framework with START_HERE_AI.md
  - Tiered documentation structure
  - 200K context management

---

**Template maintained by**: [Your Name/Team]
**Last updated**: [DATE]
**License**: [Your License]

---

## 🙏 Credits

This framework was developed through practical experience with:
- Multi-agent AI collaboration
- Human-led development workflows
- Context window optimization
- Token-efficient documentation

Tested with: Claude (Anthropic), GPT-4 (OpenAI), and designed for universal LLM compatibility.
