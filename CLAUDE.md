# CLAUDE.md

This file provides guidance for AI assistants (Claude Code and similar tools) working in this repository.

## Repository Overview

- **Repository**: `godlessfrog/testi`
- **Status**: Initial setup — no source files yet
- **Branch convention**: Feature work is done on `claude/<description>` branches

## Repository Structure

```
testi/
└── CLAUDE.md       # This file
```

As source code is added, update this section to reflect the actual directory layout and purpose of each top-level directory.

## Development Workflow

### Branch Strategy

- `main` — protected, production-ready code
- `claude/<description>` — AI-assisted feature/fix branches (e.g. `claude/add-claude-documentation-5uKnI`)
- Feature branches should be short-lived and merged via pull request

### Commit Conventions

Write clear, imperative commit messages:

```
Add user authentication module
Fix null pointer in payment handler
Update CLAUDE.md with project structure
```

- Keep the subject line under 72 characters
- Use the body to explain *why*, not *what*, when non-obvious
- Never skip pre-commit hooks (`--no-verify`) without explicit user approval

### Git Operations

```bash
# Push to a branch (always set upstream explicitly)
git push -u origin <branch-name>

# Fetch a specific branch (preferred over full fetch)
git fetch origin <branch-name>
```

Retry push/pull on network failure: exponential backoff at 2s, 4s, 8s, 16s.

## AI Assistant Guidelines

### What to Do

- Read files before modifying them — never assume content
- Make the minimum change needed to satisfy the request
- Prefer editing existing files over creating new ones
- Run tests before pushing if a test suite is present
- Commit and push on the designated branch listed at the top of any task description

### What Not to Do

- Do not push to `main` directly
- Do not force-push (`--force`) without explicit user approval
- Do not amend published commits — create a new commit instead
- Do not add features, refactors, or cleanup beyond what was asked
- Do not add comments/docstrings to code you did not change
- Do not add error handling for scenarios that cannot occur
- Do not delete files without confirming with the user

### Security

- Never commit secrets, credentials, or `.env` files
- Validate input at system boundaries (user input, external APIs); trust internal code
- Do not introduce command injection, XSS, SQL injection, or other OWASP Top 10 vulnerabilities

## Adding New Technologies

When the project gains a language, framework, or toolchain, update this file with:

1. **Build commands** — how to install dependencies and build
2. **Test commands** — how to run the test suite
3. **Lint/format commands** — code style tools and how to invoke them
4. **Environment setup** — required env vars, config files, or external services

### Template (fill in when applicable)

```bash
# Install dependencies
# <command here>

# Run tests
# <command here>

# Lint / format
# <command here>

# Build
# <command here>
```

## Pull Requests

- Title: short and descriptive (under 70 characters)
- Body: summary of changes + test plan
- Link related issues when applicable
- All CI checks must pass before merging

## Questions and Feedback

- Use `/help` in Claude Code for usage guidance
- Report issues at https://github.com/anthropics/claude-code/issues
