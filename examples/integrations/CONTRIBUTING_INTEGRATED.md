# Contributing to Nexus

Thank you for your interest in contributing to Nexus! This document provides guidelines and instructions for contributing.

---

## Getting Started

### Prerequisites

- Python 3.11 or higher
- [uv](https://github.com/astral-sh/uv) package manager
- Git

### Development Setup

1. Fork and clone the repository:
```bash
git clone https://github.com/yourusername/nexus.git
cd nexus
```

2. Run the setup script:
```bash
chmod +x scripts/setup.sh
./scripts/setup.sh
```

3. Activate the virtual environment:
```bash
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

---

## AI Assistant Collaboration

> **For AI**: Read [`START_HERE_AI.md`](START_HERE_AI.md) first | **For Humans**: Understand AI collaboration model

### Roles & Authority

| Role | Authority | Constraints |
|------|-----------|-------------|
| **Human (PM)** | Selects issues, approves approaches/commits, final decisions | - |
| **Claude Code (PC)** | Proposes solutions (2-3 options), implements after approval, updates docs | Never: select issues, decide alone, commit without approval |
| **Github Mobile** | Discusses designs, reads GitHub, posts findings in issue comments | Cannot: write code, commit directly |

**Full rules**: [`docs/llm-rules.md`](docs/llm-rules.md) | **PR/Deploy**: [`.claude/CLAUDE.md`](.claude/CLAUDE.md)

### Decision Matrix

| Decision | Who | Approval Required |
|----------|-----|-------------------|
| Issue selection, tech approach, architecture, schema, API | Human PM | ✅ |
| Implementation details, code style, doc updates | AI | ❌ |

### AI Workflow

1. **Issue Selection**: Human assigns → AI reads and summarizes
2. **Design Proposal**: AI proposes 2-3 options with pros/cons
3. **Approval**: Human selects approach, AI confirms understanding
4. **Implementation**: AI codes, shows progress, Human reviews diffs
5. **Commit**: AI asks permission → Human approves → AI commits with issue reference

### Session Handoff

**When**: Context >80%, work interrupted, session ends with incomplete tasks

**Required files**:
- `NEXT_SESSION_START.md` - Quick-start for next AI (completed, next steps, verification commands)
- `SESSION_SUMMARY_YYYY-MM-DD.md` - Full session history

**Process**: Check `git status` → commit work → commit handoff files → push → notify PM

**Details**: See [Session Handoff](docs/llm-rules.md#session-handoff-protocol) in llm-rules.md

### Issue Size Management

| Size | Time | Action |
|------|------|--------|
| ✅ Small | 1-4h | Ideal |
| ⚠️ Medium | 4-6h | Monitor context |
| ❌ Large | >6h | Alert PM, propose split |

**Why**: Issues must fit in 200K token session for complete context

### Mobile ↔ PC Sync

**Workflow**: PC creates `[MOBILE]` issue → Mobile reads + works + posts findings → PC implements

**Labels**: `mobile-task` → `mobile-done-pc-todo` → closed

---

## Technical Development Workflow

### Making Changes

```bash
git checkout -b feature/your-feature-name
# Make changes, write tests
make test && make format && make lint
git commit -m "feat(#123): Description"  # Always reference issue #
```

### Code Style

- **ruff** (lint/format), **mypy** (types), **black** style (100 chars)
- Run: `make format && make lint` before commit

### Testing

```bash
make test          # All tests
make test-cov      # With coverage
pytest tests/unit/test_client.py  # Specific file
```

**AI rule**: No untested code

### Type Checking

```bash
mypy src/nexus
```

---

## Pull Request Process

See [`.claude/CLAUDE.md`](.claude/CLAUDE.md) for PR workflow

**Checklist**:
- [ ] Tests pass, code formatted/linted, types checked
- [ ] README/docs updated (if needed)
- [ ] Clear PR description with type of change

**Template**:
```markdown
## Description
Brief description

## Type: Bug fix | New feature | Breaking change | Docs

## Testing
[Describe testing]

## Checklist
- [ ] Tests, docs, format, lint, types ✅
```

---

## Code Structure

```
src/nexus/
├── core/      # Core filesystem
├── api/       # REST API
├── storage/   # Backends (S3, GCS, local)
├── agents/    # Memory system
├── parsers/   # Doc parsers
├── auth/      # Authentication
└── utils/

tests/
├── unit/
├── integration/
└── performance/
```

---

## Commit Message Guidelines

**Format**: `<type>(#<issue>): <subject>`

**Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

**Examples**:
```
feat(#123): add S3 backend support
fix(#45): handle timeout errors
```

**AI requirement**: Always include `#<issue>` - critical for tracing changes

---

## Architecture Guidelines

### Design Principles

1. **"Everything as a File"** - Config, memory, jobs as files
2. **Three Deployment Modes** - Embedded, monolithic, distributed
3. **Backend Agnostic** - Abstract storage
4. **Type Safety** - Full annotations
5. **Testability** - Modular code

### Adding Features

**Storage Backend**: Create in `src/nexus/storage/backends/`, implement `Backend`, register, test, doc

**Parser**: Create in `src/nexus/parsers/`, implement `Parser`, register, test, doc

---

## Documentation

- **Docstrings**: Google style for all public APIs
- **Updates**: README (user changes), `docs/architecture.md` (arch changes), `docs/api/` (API changes)

**Example**:
```python
def read_file(path: str) -> bytes:
    """Read file content from virtual path.

    Args: path: Virtual path
    Returns: File content as bytes
    Raises: FileNotFoundError, PermissionError
    """
```

---

## Resources

| Document | Purpose |
|----------|---------|
| [`START_HERE_AI.md`](START_HERE_AI.md) | AI onboarding |
| [`docs/llm-rules.md`](docs/llm-rules.md) | Complete AI rules |
| [`.claude/CLAUDE.md`](.claude/CLAUDE.md) | PR/deploy procedures |
| [`README.md`](README.md) | Project overview |

---

## Getting Help

- **Issues**: Bug reports, features
- **Discussions**: Questions
- **Slack**: Community (link in README)

---

## License

Apache 2.0 License

---

**Last Updated**: 2025-10-30
