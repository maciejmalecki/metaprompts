# Meta Prompts

## Purpose

This repository contains examples of meta prompts that can be used with different AI coding tools (such as Claude Code, GitHub Copilot, Windsurf, Cursor, etc.) to enhance software development workflows.
Prompts included there are to be used to generate prompts for various aspect of software development life cycle such as planning, coding, reviewing, and so on.

## Contents

### Plan & Execute Methodology

The [`plan-execute/`](./plan-execute/) folder contains meta-prompts for the **Plan & Execute method** of software development with AI Agents. This methodology provides a structured workflow that separates development into two distinct phases:

1. **Planning Phase** - Comprehensive analysis and preparation before implementation
2. **Execution Phase** - Implementation based on the generated plan

#### Key Features

- **Three-Command Workflow**:
  - **`plan`** - Generates comprehensive development plans with context analysis, open questions, and detailed execution steps
  - **`execute`** - Implements selected steps or phases from a plan with interactive checkpoints
  - **`plan-update`** - Updates existing plans when specifications change or clarifications are needed

- **Deliverable Increments** - Breaking work into discrete, testable chunks that can be safely merged independently
- **Atomic Commits** - Following conventional commit format for clear development history
- **Context-Aware** - Plans include root cause analysis, relevant code references, and stakeholder questions
- **Tool-Agnostic** - Can be adapted for Claude Code, GitHub Copilot, Cursor, Windsurf, and other AI coding tools

For detailed information about the Plan & Execute methodology, see [Plan & Execute README](./plan-execute/README.md).