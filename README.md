# LLM Collaboration Framework

> **For**: Human developers evaluating/setting up this framework
> **Not for AI**: AI assistants should read `START_HERE_AI.md` instead
>
> **Universal framework for multi-agent, human-led AI collaboration in software projects**
>
> Works with any LLM: Claude, GPT-4, Gemini, Llama, etc.

---

## 🎯 What Is This?

A complete framework for collaborating with AI assistants on software projects where:

- ✅ **Human is PM** - You decide, AI proposes and implements
- ✅ **Multi-agent** - Coordinate multiple AI tools (Mobile + PC)
- ✅ **Tiered docs** - AI onboards in 5 minutes via structured reading
- ✅ **AI-driven integration** - AI merges framework into your existing docs
- ✅ **Context-efficient** - Token-conscious, all work < 6h
- ✅ **LLM-agnostic** - Works with any AI assistant

**Proven in production** through POE2 Craft Advisor (greenfield) and Nexus (integration).

---

## 📦 What's Included

```
LLMs-Collaboration-Guidelines/
├── README.md                 ← You are here (human-facing)
├── START_HERE_AI.md          ← AI entry point (all principles)
├── INTEGRATE_THIS.md         ← AI integration guide
├── CONTRIBUTING.md           ← Framework contribution guidelines
├── .claude/skills/           ← Optional Claude Code automation
│   └── multi-agent-onboarding/SKILL.md
└── examples/integrations/    ← Real integration case studies
    ├── README.md
    ├── MERGE_EXPERIENCE_nexus.md
    └── CONTRIBUTING_INTEGRATED.md
```

---

## ⚡ Quick Start

### AI-Driven Integration

**Tell your AI:**

**For new projects:**
```
"Integrate this framework: https://github.com/elfenlieds7/LLMs-Collaboration-Guidelines

Copy START_HERE_AI.md and customize placeholders for my project."
```

**For existing projects with AI guidelines:**
```
"Integrate this framework: https://github.com/elfenlieds7/LLMs-Collaboration-Guidelines

Read INTEGRATE_THIS.md and merge framework principles into my existing guidelines.
Preserve 100% of existing structure. Ask me before making changes."
```

**AI will:**
1. Read your existing guidelines (`.claude/CLAUDE.md`, `CONTRIBUTING.md`, etc.)
2. Propose integration plan
3. Merge framework principles into existing files (not create parallel structure)
4. Ask you to approve before committing

**Result**: Framework principles integrated while preserving your project's existing structure.

---

## 🌟 Key Features

### 1. Tiered Documentation Strategy

**🔴 Tier 0** - START NOW (5 min)
- `START_HERE_AI.md` - Universal entry point, all core principles

**🟡 Tier 1** - BEFORE WORKING (5 min)
- Project-specific AI guidelines (if exist) - they take precedence

**🟢 Tier 2** - AS NEEDED (reference)
- Project README, architecture docs, technical details

**⚪ Tier 3** - SKIP (human-only)
- Deployment scripts, credentials, human operational guides

**Result**: AI onboards in 5 minutes instead of 30+, reads only what's needed

### 2. Multi-Agent Coordination

**Desktop/PC AI (95% use case)**:
- Primary development work
- Code implementation, testing, commits
- Issue management and documentation

**Mobile AI (5% use case)**:
- Design discussions on-the-go
- Issue analysis and research
- Mobile app testing and screenshots
- Work in issue thread for full traceability

**Workflow**:
```
Human (PM) creates [MOBILE] issue with context
   ↓
Mobile AI: Reads issue → Works → Posts findings as comment
   ↓
Desktop AI: Reads findings → Implements → Closes issue
```

**Benefits**:
- Single source of truth (issue thread)
- Full traceability
- Native GitHub integration
- Simple coordination

### 3. AI-Driven Integration (Not Template Copying)

**Philosophy**: Framework merges into your existing docs, doesn't replace them.

**Example** (Nexus integration):
```
Before: .claude/CLAUDE.md (51 lines, PR rules + deploy)
After:  .claude/CLAUDE.md (67 lines, added AI workflow section)
Result: Single cohesive guide, existing rules preserved
```

### 4. 200K Context Management

- All issues must complete in single session
- Issues limited to < 6h work
- AI alerts when issues too large
- Automatic context monitoring during work

**Result**: No lost context, complete work units

### 5. Clear Authority Structure

```
Human (PM)
  ├─ Decides: Which issue, tech approach, architecture
  └─ Controls: Approvals, reviews, commits

AI (Assistant)
  ├─ Proposes: 2-3 options with pros/cons
  ├─ Implements: After approval
  └─ Waits: For approval before coding/committing
```

**Result**: Human maintains control, AI accelerates work

### 6. Session Handoff Protocol

**Files**:
- `NEXT_SESSION_START.md` - Quick context for next AI
- `SESSION_SUMMARY_*.md` - Detailed history

**Workflow**:
```
Session 1 (AI-Alpha):
- Creates handoff files
- Commits before session ends

Session 2 (AI-Beta):
- Checks for handoff files (automatic)
- Reads previous context
- Continues work seamlessly
```

**Benefits**:
- Zero context lost between sessions
- Works across different AI models
- Simple markdown files, no infrastructure

### 7. Claude Skills Enhancement (Optional)

**For Claude Code users** - Automates session startup:
- Auto `git pull`
- Auto-reads project AI guidelines
- Auto-checks handoff files
- Add to `.claude/skills/project-onboarding/`

**Architecture**: Skills complement guidelines, don't replace them. Other AIs use START_HERE_AI.md as before.

---

## 💡 Use Cases

### Solo Developer
- Use single AI tool or coordinate multiple AIs
- Fast onboarding for new AI sessions
- Structured workflow prevents AI "taking over"

### Existing Project with AI Guidelines
- Framework merges into existing docs
- Preserves your conventions 100%
- Example: Nexus (added 16 lines to existing CLAUDE.md)

### New Project (Greenfield)
- Copy START_HERE_AI.md as base
- Customize project info
- Example: POE2 Craft Advisor

### Multi-AI Setup
- Different AIs for different tasks (design vs implementation)
- Desktop + Mobile coordination
- Synced through GitHub issues

---

## 🏆 Example Projects

### [POE2 Craft Advisor](https://github.com/elfenlieds7/poe2-craft-advisor)
**Description**: AI-powered crafting advisor for Path of Exile 2
- **Stack**: Python, LangGraph, PostgreSQL, Vector DB
- **AI Tools**: Claude Mobile (design) + Claude Code (implementation)
- **Integration Type**: Greenfield project built with framework from start

**Key benefits realized**:
- 5-min AI onboarding vs ad-hoc approach
- Clean separation between design discussions and implementation
- All work tracked in < 6h issues
- Successful mobile ↔ PC sync workflow

---

### [Nexus](https://github.com/nexi-lab/nexus)
**Description**: AI-native filesystem for building intelligent agents
- **Stack**: Python 3.11+, PostgreSQL/SQLite, pgvector, FastAPI
- **AI Tools**: Claude Code (PC) + Github Mobile
- **Scale**: 133+ Python files, v0.5, active development
- **Integration Type**: Framework integrated into existing mature open-source project

**Key validation**:
- Successfully integrated into project with established conventions
- Preserved all existing documentation and workflows (100%)
- Real-world validation of destination-first integration philosophy

---

### Your Project Here

**Using this framework?** [Submit a PR](https://github.com/elfenlieds7/LLMs-Collaboration-Guidelines/pulls) to add your project!

---

## 🎓 Philosophy

### Core Principles

1. **Human-Led**: AI assists, human decides
2. **Multi-Agent**: Coordinate multiple AI tools through human PM
3. **Tiered Reading**: AI reads only what's needed (5-min onboarding)
4. **Destination-First**: Read existing guidelines, merge minimally (don't replace)
5. **Context-Conscious**: Every word costs tokens
6. **Issue-Driven**: All work tracked in GitHub
7. **Test-First**: No untested code

### Why This Works

**For Humans**:
- Maintains control while getting AI acceleration
- Existing project structure preserved
- Easy multi-agent coordination

**For AIs**:
- Clear rules prevent confusion
- Tiered reading saves tokens
- Existing guidelines take precedence
- Framework provides missing pieces only

**For Projects**:
- Structured, trackable, maintainable
- Easy integration
- Scalable across team and AIs

---

## 🔧 Compatibility

### Tested With

- ✅ Claude 3.5 Sonnet (Anthropic)
- ✅ Claude Code (Anthropic)
- ✅ GPT-4 (OpenAI)
- ✅ Google Gemini
- ✅ GitHub Mobile Copilot (for mobile AI collaboration)

### Should Work With

- 🔲 Llama models
- 🔲 Any LLM with file read/write capability

### Requirements

- GitHub repository
- Git
- AI assistant with file read/write capability
- (Optional) GitHub CLI (`gh`) for issue management

---

## 📚 Documentation

| Document | Purpose | Audience |
|----------|---------|----------|
| `README.md` (this) | Overview & philosophy | Humans evaluating framework |
| `START_HERE_AI.md` | All principles and rules | AI assistants |
| `INTEGRATE_THIS.md` | Integration process | AI performing integration |
| `CONTRIBUTING.md` | Contribution guidelines | Humans & AI contributing to framework |
| `.claude/skills/*/SKILL.md` | Session automation | Claude Code (optional) |
| `examples/integrations/` | Real case studies | Everyone |

---

## 🚀 Getting Started

### For Humans

1. **Read** this README (you are here) - 5 min
2. **Decide** integration approach:
   - New project: Copy START_HERE_AI.md, customize
   - Existing project: Let AI merge into existing guidelines
3. **Tell your AI**: "Integrate this framework: [repo URL]"
4. **Review** AI's integration plan
5. **Approve** and test

**Total**: ~10-20 minutes

### For AIs

Read `START_HERE_AI.md` for all principles.
Read `INTEGRATE_THIS.md` when performing integration.

---

## 🤝 Contributing

See `CONTRIBUTING.md` for:
- Documentation guidelines (avoid "lose focus" problem)
- Code minimization rules (for Claude)
- How to propose improvements

---

## 📝 License

MIT License

---

## 🙏 Acknowledgments

Developed and validated through:
- **POE2 Craft Advisor**: Initial framework development (greenfield project)
- **Nexus**: Integration validation (existing mature project)
- Multiple AI agents (Claude Mobile + Claude Code)
- Real project constraints and production use

**Proven in production**, validated through diverse project types.

---

## 📞 Support

**Questions?**
- Read `INTEGRATE_THIS.md` for AI integration process
- Check existing GitHub Issues
- Create new issue for bugs/suggestions

**Want to share your experience?**
- Create a discussion
- Share your integration results
- Help improve the framework

---

## 🎯 Success Metrics

After using this framework, you should see:

- ✅ AI onboarding: 30 min → 5 min
- ✅ Context waste: High → Low
- ✅ AI "overstepping": Frequent → Rare
- ✅ Issue completion: Often incomplete → Consistently complete
- ✅ Multi-agent coordination: Hard → Easy
- ✅ Integration: Manual copying → AI-driven

---

**Version**: 1.3
**Last Updated**: 2025-10-30
**Status**: Production-ready

**Start now**: Tell your AI to integrate this framework!
