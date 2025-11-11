# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repository contains meta-prompts designed to be used with AI coding assistants (Claude Code, Copilot, Cursor, Windsurf, etc.) to enhance software development workflows. The primary focus is the **Plan & Execute methodology** for AI-assisted software development.

## Architecture & Key Concepts

### Plan & Execute Methodology

The repository implements a three-command workflow for structured software development:

1. **`plan` command** - Generates comprehensive development plans
   - Takes issue number, feature name, and task specification as input
   - Scans existing codebase for context
   - Produces structured plans with root cause analysis, relevant code sections, open questions, and detailed execution steps
   - Plans are stored in `.ai` folder in markdown format
   - Designed to break work into deliverable increments that can be safely merged

2. **`execute` command** - Implements action plans
   - Takes a plan (from `.ai` folder) and executes selected steps/phases
   - Allows partial execution or full execution with optional user prompts between steps
   - Updates the plan with execution status upon completion

3. **`plan-update` command** - Updates existing plans
   - Handles changes to specifications, answers to open questions, additional acceptance criteria
   - Maintains plan consistency across all sections
   - Interactively clarifies incomplete information with the user

### How Plans Are Structured

Plans follow a normalized structure that includes:
- Feature description
- Root cause analysis (when applicable)
- Relevant code references
- Open questions (both self-reflection and questions for stakeholders)
- Detailed, enumerated execution plan with phases
- Acceptance criteria

## Commit Message Guidelines

When implementing changes using the Plan & Execute methodology, follow these standards for commit messages:

### Commit Message Format

Use the conventional commit format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Commit Types

- **feat**: A new feature
- **fix**: A bug fix
- **refactor**: Code change that neither fixes a bug nor adds a feature
- **docs**: Documentation only changes
- **style**: Changes that don't affect code meaning (formatting, missing semicolons, etc.)
- **test**: Adding or updating tests
- **chore**: Build process, dependencies, or tooling changes
- **perf**: Code change that improves performance

### Subject Line Rules

- Use imperative mood ("add feature" not "added feature")
- Don't capitalize the first letter
- No period (.) at the end
- Limit to 50 characters
- Be specific about what changed

### Body Guidelines

- Wrap at 72 characters
- Explain **what** and **why**, not **how**
- Reference issue numbers when applicable (e.g., "Closes #123")
- Include reasoning for architectural decisions
- Mention any breaking changes

### Examples

**Feature with scope:**
```
feat(auth): add JWT token refresh mechanism

Implement automatic token refresh to improve session management and security.
Tokens now refresh 5 minutes before expiration.

Closes #42
```

**Bug fix:**
```
fix(api): resolve null pointer exception in user service

Added null check before accessing user properties in getUserById method.
This prevents crashes when user record is missing from cache.

Fixes #156
```

**Refactoring:**
```
refactor(config): simplify environment variable loading

Consolidate duplicate config parsing logic into single utility function.
No functional changes, improves maintainability.
```

### AI Assistant Guidance

When Claude Code generates commits:

1. **During Plan Execution** - Generate commits at the end of each phase if the phase represents a complete, testable feature
2. **Atomic Commits** - Each commit should be logically independent and pass tests on its own
3. **Plan Reference** - Include the plan issue number in the footer when the work is tracked in an issue
4. **Descriptive Messages** - Use commit messages that help future developers understand decisions and context
5. **Review Before Committing** - Always review git diff output before creating commits

## Development Notes

- Plan files should be stored in `.ai/` directory with naming convention: `{issue-number}_{feature-short-name}.md`
- Plans should be designed with deliverable increments - each phase should represent work that can be safely merged without compromising quality
- The methodology emphasizes gathering context before execution and interactive clarification of ambiguities
- These are prompt templates meant to be used as Claude commands (`.claude/commands/`) to orchestrate AI agent behavior
