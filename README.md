# LLM Collaboration Framework

> **Universal template for multi-agent, human-led AI collaboration in software projects**
>
> Works with any LLM: Claude, GPT-4, Gemini, Llama, etc.

---

## 🎯 What Is This?

A complete, production-tested framework for collaborating with AI assistants on software projects where:

- ✅ **Human is PM** - You decide, AI proposes and implements
- ✅ **Multi-agent** - Coordinate multiple AI tools (Mobile + PC)
- ✅ **Context-efficient** - Tiered docs save tokens, 5-min onboarding
- ✅ **Issue-driven** - All work < 6h (fits 200K context)
- ✅ **LLM-agnostic** - Works with any AI assistant

**Proven in production** through the POE2 Craft Advisor project.

---

## 📦 What's Included

```
llm-collaboration-template/
├── README.md                 ← You are here
├── SETUP_GUIDE.md           ← Detailed setup instructions
├── START_HERE_AI.md         ← Universal LLM entry point
├── CONTRIBUTING_TEMPLATE.md          ← Workflow documentation
├── MOBILE_UPDATES.md        ← Mobile ↔ PC sync template
├── README_AI_SECTION.md     ← Template for your README
└── docs/
    ├── llm-rules.md         ← Complete AI rules
    └── quick-ref.md         ← Command reference
```

---

## ⚡ Quick Start

### For New Projects

```bash
# 1. Copy templates to your project
cp -r llm-collaboration-template/* YOUR_PROJECT/

# 2. Replace placeholders (see SETUP_GUIDE.md)
[PROJECT_NAME], [AI_TOOL_1], [AI_TOOL_2], etc.

# 3. Add AI Onboarding section to README
# (Copy from README_AI_SECTION.md)

# 4. Tell your AI assistant
"Read START_HERE_AI.md"
```

**Time**: 15-20 minutes

### For Existing Projects

```bash
# 1. Copy templates
cp llm-collaboration-template/START_HERE_AI.md YOUR_PROJECT/
cp llm-collaboration-template/CONTRIBUTING_TEMPLATE.md YOUR_PROJECT/
cp llm-collaboration-template/MOBILE_UPDATES.md YOUR_PROJECT/
cp -r llm-collaboration-template/docs YOUR_PROJECT/

# 2. Customize placeholders
# 3. Integrate into your workflow
```

**See**: `SETUP_GUIDE.md` for complete instructions

---

## 🌟 Key Features

### 1. Tiered Documentation Strategy

**🔴 Tier 0** - START NOW (2 min)
- `START_HERE_AI.md` - Universal entry point

**🟡 Tier 1** - BEFORE WORKING (3 min)
- `docs/llm-rules.md` - Core rules
- `MOBILE_UPDATES.md` - Pending syncs

**🟢 Tier 2** - AS NEEDED (reference)
- `README.md`, `docs/architecture.md`, `docs/quick-ref.md`, `CONTRIBUTING_TEMPLATE.md`

**⚪ Tier 3** - SKIP (human-only)
- Deployment scripts, credentials, etc.

**Result**: AI onboards in 5 minutes instead of 30+

### 2. 200K Context Management

- All issues must complete in single session
- Issues limited to < 6h work
- AI alerts when issues too large
- Automatic context monitoring

**Result**: No lost context, complete work units

### 3. Clear Authority Structure

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

### 4. Mobile ↔ PC Sync

```
Mobile: Design discussions, brainstorming
   ↓
Human: Pastes summary to MOBILE_UPDATES.md
   ↓
PC: Reads, creates issues, updates docs, commits
```

**Result**: Seamless multi-agent collaboration

---

## 💡 Use Cases

### Solo Developer
- Use single AI tool (skip mobile sync)
- Fast onboarding for new AI sessions
- Structured workflow prevents AI "taking over"

### Small Team (2-5)
- Multiple team members use same framework
- Consistent AI behavior across team
- Easy to onboard new members

### Large Team (5+)
- Standardized AI collaboration
- Clear roles and boundaries
- Scalable across multiple projects

### Multi-AI Setup
- Different AIs for different tasks (design vs implementation)
- Coordinated through human PM
- Synced via MOBILE_UPDATES.md

---

## 🏆 Example Projects

Projects successfully using this framework:

### [POE2 Craft Advisor](https://github.com/elfenlieds7/poe2-craft-advisor)
**Description**: AI-powered crafting advisor for Path of Exile 2
- **Stack**: Python, LangGraph, PostgreSQL, Vector DB
- **AI Tools**: Claude Mobile (design) + Claude Code (implementation)
- **Scale**: ~36 GitHub issues, multi-phase development
- **Results**: Structured multi-agent collaboration, efficient context usage

**Key benefits realized**:
- 5-min AI onboarding vs previous ad-hoc approach
- Clean separation between design discussions and implementation
- All work tracked in < 6h issues
- Successful mobile ↔ PC sync workflow

---

### Your Project Here

**Using this framework?** [Submit a PR](https://github.com/elfenlieds7/multi-agent-and-human-guidelines/pulls) to add your project!

**Include**:
- Project name and GitHub link
- Brief description
- Tech stack
- Which AI tools you're using
- Key results or benefits

---

## 📊 Comparison

| Approach | Onboarding | Control | Context Mgmt | Multi-AI |
|----------|-----------|---------|--------------|----------|
| **No framework** | 30+ min | Low | Manual | Hard |
| **This framework** | 5 min | High | Automatic | Easy |

---

## 🎓 Philosophy

### Core Principles

1. **Human-Led**: AI assists, human decides
2. **Context-Conscious**: Every word costs tokens
3. **Issue-Driven**: All work tracked in GitHub
4. **Test-First**: No untested code
5. **Proposal-Based**: AI proposes, human approves

### Why This Works

- **For Humans**: Maintains control while getting AI acceleration
- **For AIs**: Clear rules prevent confusion and mistakes
- **For Projects**: Structured, trackable, maintainable

---

## 🔧 Compatibility

### Tested With

- ✅ Claude 3.5 Sonnet (Anthropic)
- ✅ Claude Code (Anthropic)
- ✅ GPT-4 (OpenAI)

### Should Work With

- 🔲 Google Gemini
- 🔲 Llama models
- 🔲 Any LLM with function calling

### Requirements

- GitHub repository
- GitHub CLI (`gh`)
- Git
- AI assistant with file read/write capability

---

## 📚 Documentation

| Document | Purpose | Audience |
|----------|---------|----------|
| `README.md` (this) | Overview | Everyone |
| `SETUP_GUIDE.md` | Detailed setup | Humans setting up |
| `START_HERE_AI.md` | Entry point | AI assistants |
| `docs/llm-rules.md` | Complete rules | AI assistants |
| `docs/quick-ref.md` | Commands | AI during work |
| `CONTRIBUTING_TEMPLATE.md` | Workflow | Humans & AI |
| `MOBILE_UPDATES.md` | Sync template | AI (PC) |
| `README_AI_SECTION.md` | README template | Humans setting up |

---

## 🚀 Getting Started

1. **Read** this README (you are here) - 5 min
2. **Read** `SETUP_GUIDE.md` - 10 min
3. **Copy** templates to your project - 2 min
4. **Customize** placeholders - 10 min
5. **Test** with an AI assistant - 5 min

**Total**: ~30 minutes to fully setup

---

## 🤝 Contributing

This framework is open for contributions. To suggest improvements:

1. Use it in your project
2. Document what works / doesn't work
3. Propose changes with reasoning
4. Test with multiple AI tools

---

## 📝 License

[Specify your license here]

---

## 🙏 Acknowledgments

Developed through practical experience building POE2 Craft Advisor with:
- Multiple AI agents (Claude Mobile + Claude Code)
- Human-led workflow
- Context optimization techniques
- Real project constraints

**Proven in production**, now available as a template.

---

## 📞 Support

**Questions?**
- Read `SETUP_GUIDE.md` for detailed instructions
- Check existing GitHub Issues
- Create new issue for bugs/suggestions

**Want to share your experience?**
- Create a discussion
- Share your customizations
- Help improve the framework

---

## 🎯 Success Metrics

After using this framework, you should see:

- ✅ AI onboarding: 30 min → 5 min
- ✅ Context waste: High → Low
- ✅ AI "overstepping": Frequent → Rare
- ✅ Issue completion: Often incomplete → Consistently complete
- ✅ Team consistency: Varies → Standardized
- ✅ Onboarding new AI tools: Hard → Easy

---

**Version**: 1.0
**Last Updated**: 2025-10-26
**Status**: Production-ready

**Start now**: Read `SETUP_GUIDE.md`
