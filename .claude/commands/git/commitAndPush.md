# Commit and Push Command

This command stages all changes, creates a commit with a custom prefix and AI-generated message, then pushes to the remote repository.

## Purpose
Automate the git workflow of staging, committing with an intelligent message, and pushing changes in one command.

## Usage
Type `/commitAndPush` in Claude Code to execute this command.

## Action
When this command is executed, Claude should:

1. **Check Git Status**: Run `git status` to see current changes
2. **Analyze Changes**: Run `git diff` to understand what has been modified
3. **Review Recent Commits**: Run `git log --oneline -5` to understand commit message style
4. **Stage Changes**: Add all relevant files with `git add`
5. **Create Commit Message**: Generate an AI commit message with format:
   ```
   🚀 [prefix]: [descriptive message]
   
   🤖 Generated with Claude Code (https://claude.ai/code)
   
   Co-Authored-By: Claude <noreply@anthropic.com>
   ```
6. **Commit**: Create the commit with the generated message
7. **Push**: Push the changes to the remote repository
8. **Confirm**: Show final git status to confirm success

## Commit Message Guidelines
- Use a relevant emoji prefix (🚀 for features, 🐛 for fixes, 📝 for docs, ♻️ for refactor, etc.)
- Write a concise, descriptive message explaining the "why" not just the "what"
- Follow conventional commit style when possible
- Keep the first line under 50 characters

## Error Handling
- If no changes to commit, inform the user
- If push fails due to remote changes, suggest pulling first
- If commit hooks fail, show the error and let user decide next steps