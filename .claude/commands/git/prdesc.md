# Generate PR Description with Affected Changes

You are helping a developer create a comprehensive pull request description that includes all affected changes and their impact.

## Instructions

1. **Analyze Current Changes**
   - Run `git status` to see all modified, added, and deleted files
   - Run `git diff --cached` to see staged changes
   - Run `git diff` to see unstaged changes
   - Run `git log --oneline -10` to see recent commit history for context

2. **Categorize Changes**
   - **Features**: New functionality added
   - **Bug Fixes**: Issues resolved
   - **Refactoring**: Code improvements without behavior changes
   - **Documentation**: README, comments, or doc updates
   - **Tests**: New or updated test cases
   - **Configuration**: Build, CI/CD, or environment changes
   - **Dependencies**: Package updates or additions

3. **Identify Affected Areas**
   - Map changed files to functional areas of the codebase
   - Note any cross-cutting concerns or shared utilities modified
   - Identify potential breaking changes or API modifications
   - Consider impact on existing features or integrations

4. **Generate Description**
   Create a structured PR description with:
   - **Summary**: Brief overview of the changes
   - **Changes Made**: Detailed list organized by category
   - **Files Changed**: Key files and their modifications
   - **Testing**: How changes were tested
   - **Impact**: Areas of the codebase affected
   - **Breaking Changes**: Any breaking changes (if applicable)

## Output Format

```markdown
## Summary
[Brief description of what this PR accomplishes]

## Changes Made
### Features
- [Feature 1]
- [Feature 2]

### Bug Fixes
- [Bug fix 1]
- [Bug fix 2]

### [Other categories as applicable]

## Files Changed
- `path/to/file1.ext` - [Description of changes]
- `path/to/file2.ext` - [Description of changes]

## Testing
- [How changes were tested]
- [New tests added]

## Impact
- [Areas of codebase affected]
- [Potential side effects]

## Breaking Changes
- [Any breaking changes, or "None"]
```

Focus on clarity and completeness to help reviewers understand the scope and impact of the changes.