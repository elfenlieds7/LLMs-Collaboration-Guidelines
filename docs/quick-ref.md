# Quick Reference - Command Cheatsheet

> Fast reference for common commands. For rules, see `docs/llm-rules.md`.

---

## 🔍 Session Startup

```bash
# Check for mobile sync tasks
cat MOBILE_UPDATES.md

# Check open issues
gh issue list --state open --limit 10

# Check in-progress work
gh issue list --label in-progress

# Recent activity
git log -5 --oneline
git status
```

---

## 📋 Issue Management

### View Issues

```bash
# List open issues
gh issue list --state open

# List by label
gh issue list --label high-priority
gh issue list --label blocker

# View specific issue
gh issue view 123
```

### Modify Issues

```bash
# Comment on issue
gh issue comment 123 --body "Progress update: ..."

# Add label
gh issue edit 123 --add-label in-progress
gh issue edit 123 --add-label blocker

# Remove label
gh issue edit 123 --remove-label in-progress

# Close issue
gh issue close 123 --comment "Completed. Summary: ..."
```

### Create Issue

```bash
# Create new issue (interactive)
gh issue create

# Create with details
gh issue create --title "Task: ..." --body "Description..." --label feature
```

---

## 🔄 Git Operations

### Status & History

```bash
# Check status
git status

# View recent commits
git log -5 --oneline
git log --oneline --graph --all -10

# View specific file history
git log --oneline -- path/to/file
```

### Commit & Push

```bash
# Stage and commit
git add path/to/file
git commit -m "feat(#123): Add feature X"

# Push to remote
git push origin branch-name

# View diff before commit
git diff
git diff --staged
```

### Branches

```bash
# List branches
git branch -a

# Create and switch
git checkout -b feature-branch

# Switch branch
git checkout main
```

---

## 📁 File Operations

### Search Files

```bash
# Find files by name
find . -name "*.ext" -type f

# List directory tree (limit depth)
tree -L 2
```

### Search Content

```bash
# Grep for text
grep -r "search_term" ./src

# Case insensitive
grep -ri "search_term" ./src

# Count occurrences
grep -rc "search_term" ./src
```

---

## 🧪 Testing

```bash
# Run all tests
[YOUR_TEST_COMMAND]

# Run specific test file
[YOUR_TEST_COMMAND] tests/test_file

# Run with coverage
[YOUR_TEST_COMMAND] --coverage

# Run verbose
[YOUR_TEST_COMMAND] -v
```

---

## 📦 Dependency Management

```bash
# Install dependencies
[YOUR_INSTALL_COMMAND]

# Update dependencies
[YOUR_UPDATE_COMMAND]

# Check installed packages
[YOUR_LIST_COMMAND]
```

---

## 🔍 Project-Specific Commands

[Add project-specific commands here]

```bash
# Example: Build project
# [BUILD_COMMAND]

# Example: Run development server
# [DEV_SERVER_COMMAND]

# Example: Lint code
# [LINT_COMMAND]
```

---

## 📊 Context Monitoring

### Estimate Token Usage

Rough estimates for context awareness:

| File Type | ~Tokens per Line |
|-----------|-----------------|
| Code | 15-25 |
| Markdown | 10-20 |
| JSON | 5-15 |
| Git log | 10-15 |

**200K limit ≈ 8,000-10,000 lines of code read**

### Check Session Usage

Monitor file reads:
- Each doc read = ~500-3000 tokens
- Each code file = ~1000-5000 tokens
- Keep running tally mentally

---

## 🚨 Emergency Recovery

### Lost Context?

```bash
# Recover state
git log -10
gh issue list --label in-progress
git status
git diff
cat MOBILE_UPDATES.md

# Check what was being worked on
gh issue view $(gh issue list --label in-progress --json number --jq '.[0].number')
```

### Uncommitted Changes?

```bash
# See what changed
git status
git diff

# Stash changes
git stash push -m "WIP: description"

# List stashes
git stash list

# Apply stash
git stash pop
```

---

## 🔧 Troubleshooting

### GitHub CLI Issues

```bash
# Check auth status
gh auth status

# Re-authenticate
gh auth login
```

### Git Issues

```bash
# Reset to last commit (CAREFUL!)
git reset --hard HEAD

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Discard local changes
git checkout -- path/to/file
```

---

## 📝 Commit Message Templates

```bash
# Feature
feat(#123): Add feature X

# Fix
fix(#45): Correct bug Y

# Docs
docs(#67): Update documentation

# Refactor
refactor(#89): Simplify code structure

# Test
test(#34): Add unit tests for X

# Chore
chore(#12): Update dependencies
```

---

## 🎯 Common Scenarios

### Starting Work on Issue

```bash
gh issue view 123                    # Read issue
gh issue edit 123 --add-label in-progress
# ... do work ...
git add .
git commit -m "feat(#123): ..."
git push
gh issue close 123 --comment "Done"
```

### Handling Blocker

```bash
gh issue edit 123 --add-label blocker
gh issue comment 123 --body "⚠️ BLOCKER: Need X before proceeding"
# Switch to different issue
```

### Processing Mobile Sync

```bash
cat MOBILE_UPDATES.md               # Read content
# ... create issues, update docs ...
git add MOBILE_UPDATES.md docs/
git commit -m "feat: Sync mobile discussion (MOBILE_UPDATES.md)"
git push
```

---

## 📚 File Locations Quick Map

```
START_HERE_AI.md          → LLM entry point
docs/llm-rules.md         → Core rules
docs/quick-ref.md         → This file
docs/architecture.md      → Technical design
MOBILE_UPDATES.md         → Mobile sync tasks
CONTRIBUTING.md           → Workflow details
README.md                 → Project overview
```

---

**Last Updated**: [DATE]
**Use Case**: Quick command lookup during work
**Full Rules**: See `docs/llm-rules.md`
