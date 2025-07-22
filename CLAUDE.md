# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Status

This is a learning repository for Claude Code best practices. Currently contains:

- `.claude/commands/` directory for custom slash commands
- Example test command demonstrating slash command functionality

## Best Practices for This Repository

### Workflow Recommendations
- Use the explore→plan→code→commit workflow for complex tasks
- Be specific in instructions rather than vague
- Use `/clear` to reset context between different tasks
- Course correct early and often using Escape key

### Custom Commands
- Custom slash commands are organized in `.claude/commands/` by category:
  - `git/` - Git workflow commands (commitAndPush, prdesc, pr-review, etc.)
  - `testing/` - Testing commands organized by purpose:
    - `coverage-analysis/` - Test coverage analysis (jest-coverage-analysis, java-coverage-analysis)
    - `test-generation/` - Unit test generation (jest-generate-unit-tests, java-generate-unit-tests, angular-component-scaffold)
  - `analysis/` - Code analysis commands (deadcode, context)
  - `workflow/` - Task management commands (think, spawn)
- Use `/test` to verify the slash command system is working
- Add new commands as Markdown files in appropriate category folders

### Context Management
- Keep CLAUDE.md concise and focused on actionable information
- Use the `#` key to automatically add content to CLAUDE.md during sessions
- Document frequently used patterns and commands here

### Development Guidelines
- IMPORTANT: Always be specific about requirements and constraints
- Use tab-completion to reference files and folders
- Provide visual context (screenshots, mockups) when relevant
- Break complex tasks into smaller, manageable steps

## Common Commands
- `/test` - Verify slash command system functionality
- `/clear` - Reset conversation context
- `/permissions` - Manage tool allowlist

## Notes

This repository serves as a testing ground for Claude Code workflows and best practices. Update this file as new patterns and commands are discovered.