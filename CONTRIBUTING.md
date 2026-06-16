# Contributing to BookLM-Orchestrator

## Getting Started

1. Clone repository:
```bash
git clone https://github.com/Yoann-CRAMATTE/booklm-orchestrator.git
cd booklm-orchestrator
```

2. Read docs:
- `README.md` — Overview
- `SPECIFICATION.md` — Features & architecture
- `GETTING_STARTED.md` — First use

## Development Workflow

### Branch naming
- `feature/analyzer` — New features
- `fix/segmenter-bug` — Bug fixes
- `docs/setup-guide` — Documentation

### Commit messages
- Conventional Commits format
- Example: `feat(generator): add video format support`
- Include why, not just what

### Before pushing

**✅ Should be in git:**
- Source code (src/*.md)
- Documentation (*.md files)
- Templates (templates/*.md)
- Guides (guides/*.md)
- Configuration (SKILL.md, .gitignore)

**❌ DO NOT COMMIT:**
- Course materials: `Cours/*.pdf`, `*.docx` (private, user files)
- Generated outputs: `examples/output_podcast_*.txt`, `examples/output_podcast_*.md` (test artifacts)
- Private config: `.claude/SETUP.md` (GitHub credentials, API keys)
- Local settings: `.claude/settings.local.json` (personal config)
- Test course files: `examples/test_course_*.txt` (temporary)
- Node modules, Python venv, build artifacts

**Why?**
- Course files = user's private property, not project source
- Generated outputs = ephemeral, recreated each test
- Private config = security risk (credentials exposed)
- Test artifacts = clutter, can regenerate anytime

### Checking before commit

```bash
# See what will be committed
git status
git diff --cached

# If suspicious files appear:
git reset HEAD [file]  # Remove from staging
# Add to .gitignore if needed
```

### .gitignore rules

Maintained in `.gitignore`. Key rules:
- `Cours/` — Course PDFs
- `examples/output_podcast_*.txt` — Generated instruction blocks
- `examples/output_podcast_*.md` — Generated markdown
- `examples/test_course_*.txt` — Test files
- `.claude/SETUP.md` — Private setup
- `.claude/settings.local.json` — Local config

## Testing Your Changes

1. **Understand spec** → Read SPECIFICATION.md
2. **See example input** → examples/example-input-course.md
3. **Review example output** → examples/example-output-podcasts.md
4. **Test locally** → Use your own course file, generate output
5. **Validate** → Ensure output is usable

## Code Style

- Markdown: Clear, structured, no jargon
- Technical docs: Include examples
- Comments: Only "why", never "what"
- No dead code, unused imports, or commented-out sections

## Pull Requests

1. Create branch from `main`
2. Make changes
3. Ensure clean git status (nothing accidentally committed)
4. Create PR with:
   - Clear title (under 70 chars)
   - Summary of changes
   - Why this matters
5. Reference related issues if any

## Questions?

- Check [README.md](README.md) for overview
- Read [SPECIFICATION.md](SPECIFICATION.md) for features
- See [TROUBLESHOOTING.md](guides/TROUBLESHOOTING.md) for common issues

---

**Remember:** This skill helps educators create structured content. Keep it clean, documented, and secure.
