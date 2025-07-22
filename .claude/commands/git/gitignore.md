# Add Claude Code Files to .gitignore

You are helping a developer add Claude Code-related files to their .gitignore to prevent them from being committed to version control.

## Instructions

1. **Check Current .gitignore**
   - Use Read tool to examine existing .gitignore file (if it exists)
   - Note existing patterns and structure

2. **Add Claude Code Entries**
   Add the following entries to .gitignore:
   - `.claudemd/` - Claude Code session directory
   - `.mcp.json` - MCP (Model Context Protocol) configuration
   - `CLAUDE.md` - Project instructions file (if it should be ignored)

3. **Update .gitignore**
   - If .gitignore exists, append the new entries with appropriate spacing
   - If .gitignore doesn't exist, create it with Claude Code entries
   - Add a comment section to organize the additions

## Pattern to Add

```
# Claude Code
.claudemd/
.mcp.json
CLAUDE.md
```

## Implementation Steps

1. Check if .gitignore exists in the project root
2. If it exists:
   - Read the current contents
   - Check if Claude Code entries already exist
   - If not present, append them with proper formatting
3. If it doesn't exist:
   - Create .gitignore with Claude Code entries
4. Ensure proper formatting and spacing
5. Confirm the changes were applied correctly

Note: Some projects may want to keep CLAUDE.md in version control for team collaboration. Consider the project's needs when adding this entry.