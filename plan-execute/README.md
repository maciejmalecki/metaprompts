# Plan & Execute Method

This folder contains **self-contained meta-prompts** for the Plan & Execute method of software development with AI Agents. Each meta-prompt is a complete prompt designed to be pasted directly into an AI coding assistant (like Claude Code, Copilot, Cursor, etc.) to orchestrate development workflows.

**Important:** These meta-prompts should be used in the following order:
1. **`create-plan.md`** - Creates command that generates the initial plan
2. **`plan-update.md`** - Creates command that updates the plan
3. **`execute.md`** - Creates command that executes the plan

**BEWARE:** I was lazy and have generated this file via AI Agent. I did some manual changes to make it better, but there still might be some inconsistencies or errors, or notorious repetitions. Please report any issues you find.

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

## The Three Meta-Prompts

Each meta-prompt is a self-contained, ready-to-use prompt. Simply copy the contents of each file and paste it directly into your AI assistant. Each subsequent meta-prompt depends on outputs (a command file created) from the previous one.

### 1. Plan Meta-Prompt (`create-plan.md`) - Use First

**Purpose:** Generated command creates a comprehensive development plan for a feature or bug fix.

**Usage:**
1. Copy the contents of `create-plan.md`
2. Paste it directly into your AI assistant (Claude Code, Copilot, Cursor, etc.)
3. The AI will guide you through:
   - Gathering issue number, feature name, and task specification
   - Scanning your codebase for relevant context
   - Creating a structured plan with:
     - Feature description
     - Root cause analysis (when applicable)
     - Relevant code references
     - Open questions (for clarification)
     - Self-reflection questions for the AI
     - Detailed, enumerated execution steps/phases
     - Acceptance criteria
4. Output: A markdown file saved in `.ai/` folder named `{issue-number}_{feature-short-name}.md`

### 2. Plan-Update Meta-Prompt (`plan-update.md`) - Use Second (Optional)

**Purpose:** Generated command updates an existing plan when specifications change or clarifications are needed.

**Usage:**
1. Copy the contents of `plan-update.md`
2. Paste it directly into your AI assistant
3. The AI will guide you through:
   - Identifying the plan to update (created in step 1)
   - Specifying changes needed (spec changes, Q&A answers, new criteria, etc.)
   - Updating the plan consistently across all sections
   - Interactively clarifying incomplete information
4. Output: Updated plan in the same `.ai/` file

**When to use:** Only if requirements change or open questions get answered before execution.

### 3. Execute Meta-Prompt (`execute.md`) - Use Last

**Purpose:** Generated command implements the plan by executing selected steps or phases.

**Usage:**
1. Copy the contents of `execute.md`
2. Paste it directly into your AI assistant
3. The AI will guide you through:
   - Loading your plan (created/updated in steps 1-2)
   - Selecting which steps or phases to execute
   - Implementing each step systematically
   - Supporting interactive checkpoints for review
   - Updating the plan with execution status
4. Output: Implementation of the feature/fix and updated plan showing completion status

**Dependency:** Requires a plan created by `plan` command (optionally updated by `plan-update` command)

## How to Use These Meta-Prompts

These meta-prompts are **self-contained and ready to use immediately**. No setup or command installation required. Simply follow this workflow:

### Quick Start Workflow

1. **Create a plan:**
   - Copy the entire contents of `create-plan.md`
   - Paste it into your AI assistant

2. **Update the plan (optional):**
   - Copy the entire contents of `plan-update.md`
   - Paste it into your AI assistant

3. **Execute the plan:**
   - Copy the entire contents of `execute.md`
   - Paste it into your AI assistant

4. **Review and commit:**
   - Review generated prompts
   - Commit changes
   - Restart your AI Agent (i.e. Claude Code) and test generated commands using slash (/) notation

### How Each Meta-Prompt Works

- **`create-plan.md`** - Create command that orchestrates plan creation. Paste and follow the AI's guidance.
- **`plan-update.md`** - Create command that updates existing plans. References plans created by `create-plan.md`.
- **`execute.md`** - Create command that executes plans. References plans from `create-plan.md` and `plan-update.md`.

Each meta-prompt is independent and self-contained—no code generation, no command installation needed.

## Deliverable Increments

The Plan & Execute method emphasizes breaking work into **deliverable increments** - discrete chunks of work that:
- Represent a complete, testable feature or fix
- Can be safely merged into the main branch
- Don't compromise code quality or stability
- Each can be released independently if needed

This approach enables continuous integration and reduces the risk of large, monolithic commits.

## Adaptation for Other Tools

These meta-prompts are **tool-agnostic** - they work with any AI coding assistant and can be used immediately without modification. The methodology works equally well with:

- **GitHub Copilot** - Paste meta-prompts into Copilot chat
- **Cursor** - Use in Cursor's command system or chat
- **Windsurf** - Paste into Windsurf's AI interactions
- **Cline** - Use in Cline's conversation interface
- **Any AI coding assistant** - That accepts multi-paragraph prompts

The meta-prompts are self-contained and require **no adaptation** for different tools—just copy and paste.

### Customizing Meta-Prompts for Your Workflow

If you want to customize a meta-prompt for your specific needs:

1. **Read the meta-prompt** - Understand what it does
2. **Identify what to change** - E.g., different plan structure, additional questions, specific code patterns to look for
3. **Edit the meta-prompt file** - Modify the instructions directly in the markdown file
4. **Test with your AI assistant** - Paste the modified version and verify it works as expected

**Example customization:**
If you want the plan to include additional security considerations, you could edit `create-plan.md` to add:
```
- Security analysis: Identify any security implications of this feature
- Required security reviews: List any security reviews needed before merge
```

The core methodology remains effective regardless of tool or customization.

## Best Practices

1. **Always plan first** - Don't jump to implementation without a plan
2. **Gather context** - Let the plan command scan your codebase thoroughly
3. **Ask clarifying questions** - Use the open questions section to resolve ambiguities
4. **Commit by phase** - Create commits for each completed phase
5. **Update plans** - Keep plans in sync with specification changes
6. **Review before execution** - Always review generated plans before execution begins