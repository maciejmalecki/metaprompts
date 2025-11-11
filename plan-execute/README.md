# Plan & Execute Method

This folder contains meta-prompts for the Plan & Execute method of software development with AI Agents.

**BEWARE:** This README.md is AI generated. I have reviewed it thoroughly, but there may still be inaccuracies. Please report any issues.

## Overview

The Plan & Execute method is a structured workflow for using AI coding assistants to develop software features and fix bugs. It separates the development process into two distinct phases:

1. **Planning Phase** - Comprehensive analysis and preparation
2. **Execution Phase** - Implementation based on the plan

This methodology helps:
- Break down complex features into manageable, deliverable increments
- Ensure thorough context gathering before implementation
- Create atomic commits that can be safely merged
- Reduce rework and improve code quality
- Provide clear tracking and transparency for development progress

## The Three-Command Workflow

### 1. Plan Command (`create-plan.md`)

**Purpose:** Generate a comprehensive development plan for a feature or bug fix.

**When to use:** At the start of a new feature development or when tackling a complex bug.

**Process:**
- Takes an issue number, feature name, and task specification as input
- Scans the existing codebase for relevant context and patterns
- Generates a structured plan with:
  - Feature description
  - Root cause analysis (when applicable)
  - Relevant code references
  - Open questions (for clarification with stakeholders)
  - Self-reflection questions for the AI
  - Detailed, enumerated execution steps/phases
  - Acceptance criteria

**Output:** A markdown file stored in `.ai/` folder with naming convention: `{issue-number}_{feature-short-name}.md`

### 2. Execute Command (`execute.md`)

**Purpose:** Implement an action plan by executing selected steps or phases.

**When to use:** After a plan has been created and reviewed, to implement the work.

**Process:**
- User selects which steps or phases to execute ("all" or specific ranges)
- Optionally requests prompts between each step/phase for review
- Implements each step systematically
- Updates the plan with execution status
- Marks completed, skipped, or pending steps

**Key features:**
- Flexible execution (partial or full)
- Interactive checkpoints for user approval
- Progress tracking within the plan
- Clear documentation of what was completed

### 3. Plan-Update Command (`plan-update.md`)

**Purpose:** Update an existing plan when specifications change or clarifications are needed.

**When to use:** When:
- Requirements change during development
- Open questions get answered
- Additional acceptance criteria are identified
- Stakeholder feedback necessitates plan revision

**Process:**
- User identifies the plan to update
- Specifies the scope of changes (spec changes, Q&A answers, new criteria, etc.)
- Agent updates the plan consistently across all relevant sections
- Interactively clarifies incomplete information

## How to Use These Meta-Prompts

These files are **meta-prompts** - prompts that generate other prompts. Here's how to use them:

### Step 1: Generate Claude Commands

Take each meta-prompt file (e.g., `create-plan.md`, `execute.md`, `plan-update.md`) and use it with Claude Code to generate actual commands:

1. Ask Claude Code: *"Using the guidance in this meta-prompt [insert file contents], generate a complete Claude command for me"*
2. Claude will create a comprehensive prompt designed to orchestrate AI behavior
3. Save the generated prompt in `.claude/commands/` folder with the appropriate name (e.g., `plan.md`, `execute.md`, `plan-update.md`)

### Step 2: Use the Generated Commands

Once installed as Claude commands, use them in your workflow:

```bash
/plan               # Start planning a new feature
/execute            # Execute an existing plan
/plan-update        # Update an existing plan
```

### Step 3: Follow the Workflow

- Create a plan with `/plan` for new features
- Review and refine the plan
- Execute with `/execute` when ready
- Update with `/plan-update` if needed
- Commit changes following the conventional commit format defined in CLAUDE.md

## Deliverable Increments

The Plan & Execute method emphasizes breaking work into **deliverable increments** - discrete chunks of work that:
- Represent a complete, testable feature or fix
- Can be safely merged into the main branch
- Don't compromise code quality or stability
- Each can be released independently if needed

This approach enables continuous integration and reduces the risk of large, monolithic commits.

## Adaptation for Other Tools

These meta-prompts were created for **Claude Code**, but the methodology is tool-agnostic and can be easily adapted for:

- **GitHub Copilot** - Generate similar commands/workflows adapted to Copilot's interfaces
- **Cursor** - Customize for Cursor's command system
- **Windsurf** - Adapt the methodology to Windsurf's capabilities
- **Cline** - Adjust for Cline's specific AI orchestration patterns

To adapt for another tool:
1. Understand the tool's command/prompt system
2. Take the relevant meta-prompt
3. Ask Claude to regenerate the prompt for your target tool
4. Adjust syntax/formatting to match the tool's requirements
5. Test with a sample feature

The core methodology remains the same regardless of the AI tool used.

## Best Practices

1. **Always plan first** - Don't jump to implementation without a plan
2. **Gather context** - Let the plan command scan your codebase thoroughly
3. **Ask clarifying questions** - Use the open questions section to resolve ambiguities
4. **Commit by phase** - Create commits for each completed phase
5. **Update plans** - Keep plans in sync with specification changes
6. **Review before execution** - Always review generated plans before execution begins