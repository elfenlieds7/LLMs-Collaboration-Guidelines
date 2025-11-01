# Contributing to LLM Collaboration Framework

> Thank you for your interest in improving this framework!

---

## 🎯 Types of Contributions

We welcome:

### 1. Bug Reports
- Unclear documentation
- Broken examples
- Confusing instructions
- Issues with specific LLMs

### 2. Feature Suggestions
- New template files
- Additional workflow patterns
- LLM-specific optimizations
- Tools/platform integrations

### 3. Documentation Improvements
- Clearer explanations
- More examples
- Translation to other languages
- Better diagrams

### 4. Example Projects
- Share your success story
- Add your project to Example Projects section
- Write case studies

---

## 📝 How to Contribute

### Reporting Issues

1. Check [existing issues](https://github.com/elfenlieds7/multi-agent-and-human-guidelines/issues) first
2. Create new issue with:
   - Clear title
   - Detailed description
   - Steps to reproduce (if applicable)
   - Your environment (OS, LLM used, etc.)

### Suggesting Improvements

1. Open an issue first to discuss
2. Explain:
   - What problem it solves
   - Why current approach is insufficient
   - Proposed solution
   - Potential drawbacks

### Submitting Changes

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Test your changes:
   - Verify all placeholders still work
   - Check markdown formatting
   - Test with at least one LLM
5. Commit with clear message: `feat: Add X` or `docs: Improve Y`
6. Push to your fork
7. Create Pull Request

---

## ✅ Contribution Guidelines

### For Documentation

- **Be concise**: Remember, every word costs tokens
- **Use bullets**: Over paragraphs
- **Use tables**: For comparisons
- **One example max**: Per concept
- **Keep placeholders**: Like `[PROJECT_NAME]`, `[AI_TOOL_1]`

#### Avoid "Lose Focus" Problem

**Problem**: Too much content → AI loses focus on what's important

**When writing/updating docs**:
1. Ask PM: "What's the target length? What must be included?"
2. Prioritize core content (95% use cases)
3. Compress edge cases (5% use cases) to minimal form
4. Use tables/bullets instead of paragraphs
5. Remove examples unless critical

**Bottom line**: Before writing, check with PM about length/focus concerns.

#### Code in Documentation

**Rule**: When writing docs, minimize code examples. Only use code when genuinely clearer than prose.

**Applies to**: Claude (tends to overuse code blocks in descriptions).

### For Templates

- **Maintain structure**: Don't break the tiered approach (🔴🟡🟢⚪)
- **Test thoroughly**: With at least 2 different LLMs
- **Preserve universality**: Don't add tool-specific code
- **Update SETUP_GUIDE.md**: If adding new placeholders

### For Code/Scripts

- **Keep it simple**: This is a template, not production code
- **Add comments**: Explain what it does
- **Make it universal**: Should work on Windows/Mac/Linux

---

## 🧪 Testing Your Changes

Before submitting:

1. **Placeholder test**:
   - All placeholders still marked clearly
   - SETUP_GUIDE.md documents all placeholders

2. **LLM test**:
   - Feed START_HERE_AI.md to an LLM
   - Verify it understands in < 5 minutes
   - Test with different LLMs if possible

3. **Markdown test**:
   - Preview in GitHub-style markdown renderer
   - Check all links work
   - Verify formatting is correct

4. **Setup test**:
   - Follow SETUP_GUIDE.md in a test project
   - Verify all steps work
   - Check for missing instructions

---

## 📋 Pull Request Checklist

- [ ] Tested with at least one LLM
- [ ] All markdown renders correctly
- [ ] Placeholders documented in SETUP_GUIDE.md
- [ ] Follows existing style (concise, bullets, tables)
- [ ] No tool-specific dependencies added
- [ ] Examples are clear and minimal
- [ ] README.md updated if needed
- [ ] Commit messages are clear

---

## 🎨 Style Guide

### Writing Style

**Good**:
```markdown
## Quick Start

1. Copy files
2. Replace placeholders
3. Tell AI: "Read START_HERE_AI.md"
```

**Bad**:
```markdown
## Getting Started

In this section, we will walk through the process of getting started
with the framework. First, you'll need to copy all the necessary files
to your project directory. After that, you should replace all the
placeholder values...
```

### Commit Messages

Format: `<type>: <description>`

Types:
- `feat`: New feature or template
- `docs`: Documentation only
- `fix`: Bug fix
- `refactor`: Code restructure
- `test`: Test-related
- `chore`: Maintenance

Examples:
- `feat: Add Python-specific quick-ref commands`
- `docs: Clarify placeholder replacement steps`
- `fix: Correct broken link in SETUP_GUIDE`

---

## 🏆 Adding Your Project to Examples

If you've used this framework successfully:

1. Fork the repo
2. Edit `README.md`
3. Add your project under "Example Projects":

```markdown
### [Your Project Name](github-link)
**Description**: Brief description
- **Stack**: Your tech stack
- **AI Tools**: Which AIs you used
- **Scale**: Project size/complexity
- **Results**: Key benefits

**Key benefits realized**:
- Benefit 1
- Benefit 2
- Benefit 3
```

4. Submit PR with title: `docs: Add [Your Project] to examples`

---

## 🤝 Community Guidelines

- **Be respectful**: Everyone is learning
- **Be constructive**: Criticism should be helpful
- **Be patient**: Maintainers are volunteers
- **Be collaborative**: Help others in issues/discussions

---

## 📞 Questions?

- **General questions**: [Open a discussion](https://github.com/elfenlieds7/multi-agent-and-human-guidelines/discussions)
- **Bug reports**: [Create an issue](https://github.com/elfenlieds7/multi-agent-and-human-guidelines/issues)
- **Feature ideas**: [Create an issue](https://github.com/elfenlieds7/multi-agent-and-human-guidelines/issues) with "enhancement" label

---

## 🎓 Learning Resources

New to contributing to open source?

- [First Contributions Guide](https://github.com/firstcontributions/first-contributions)
- [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
- [Markdown Guide](https://www.markdownguide.org/)

---

## 📄 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Thank you for helping improve this framework!**

Every contribution, no matter how small, helps other developers build better AI collaboration workflows.
