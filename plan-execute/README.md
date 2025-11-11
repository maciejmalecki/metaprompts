# Plan & Execute Method

This folder contains **self-contained meta-prompts** for the Plan & Execute method of software development with AI Agents. Each meta-prompt is a complete prompt designed to be pasted directly into an AI coding assistant (like Claude Code, Copilot, Cursor, etc.) to orchestrate development workflows.

**Important:** These meta-prompts should be used in the following order:
1. **`create-plan.md`** - Creates command that generates the initial plan
2. **`plan-update.md`** - Creates command that updates the plan
3. **`execute.md`** - Creates command that executes the plan

**BEWARE:** I was lazy and have generated this README file via AI Agent. I did some manual changes to make it better, but there still might be some inconsistencies or errors, or notorious repetitions. Please report any issues you find.

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

## How to Use These Meta-Prompts

Each meta-prompt is a self-contained, ready-to-use prompt. Simply copy the contents of each file and paste it directly into your AI assistant. Each subsequent meta-prompt depends on outputs (a command file created) from the previous one.
No setup or command installation required. Simply follow this workflow:

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

- **`create-plan.md`** - Create command that orchestrates plan creation. Paste and follow the AI's guidance. Normally results in creation of `/plan` command.
- **`plan-update.md`** - Create command that updates existing plans. References plans created by `create-plan.md`. Normally results in creation of `/plan-update` command.
- **`execute.md`** - Create command that executes plans. References plans from `create-plan.md` and `plan-update.md`. Normally results in creation of `/execute` command.

## Adaptation for Other Tools

These meta-prompts are **tool-agnostic** - they work with any AI coding assistant and can be used immediately without major modification (although perhaps one needs to adjust file paths used internally, like instead `.claude\commands\plan.md` use `.github\prompts\plan.prompt.md` when using Copilot). The methodology works equally well with:

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