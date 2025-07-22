# Resolve Merge Conflicts Command

This command automatically analyzes and resolves merge conflicts using AI assistance.

## Purpose
Intelligently resolve git merge conflicts by analyzing the conflicting code and making informed decisions about which changes to keep.

## Usage
Type `/resolveMerge` in Claude Code to execute this command.

## Action
When this command is executed, Claude should:

1. **Check Merge Status**: Run `git status` to identify files with merge conflicts
2. **Analyze Each Conflict**: For each conflicted file:
   - Read the file to see conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
   - Understand the context of both HEAD and incoming changes
   - Analyze the purpose and impact of each conflicting section
3. **Resolve Conflicts**: Make intelligent decisions to:
   - Keep the most logical/appropriate changes
   - Combine changes when both are needed
   - Remove conflict markers
   - Ensure code remains functional and follows project patterns
4. **Review Changes**: Show a summary of what was resolved and why
5. **Stage Resolved Files**: Run `git add` for each resolved file
6. **Complete Merge**: Run `git commit` to finalize the merge
7. **Verify**: Run basic checks (lint/typecheck if available) to ensure resolution didn't break anything

## Resolution Strategy
- **Code Logic**: Prefer changes that maintain or improve functionality
- **Style Consistency**: Follow existing project conventions and patterns
- **Dependencies**: Ensure imports, exports, and references remain valid
- **Comments/Docs**: Merge documentation updates when both sides add value
- **Tests**: Preserve or combine test cases from both branches
- **Configuration**: Carefully merge config changes, preferring non-breaking additions

## Safety Measures
- Create a backup branch before starting: `git branch backup-before-merge`
- If conflicts are too complex or risky, stop and ask for human guidance
- Always explain the reasoning behind resolution decisions
- Run available linting/type checking after resolution

## Error Handling
- If no merge conflicts exist, inform the user
- If conflicts are in binary files, request manual resolution
- If resolution would likely break functionality, ask for guidance
- Provide clear rollback instructions if something goes wrong