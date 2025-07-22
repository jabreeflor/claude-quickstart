# Dead Code Detection Command

This command analyzes the codebase to identify unused code, imports, variables, and functions that can be safely removed.

## Purpose
Scan the project for dead code including unused imports, variables, functions, classes, and files to help maintain a clean codebase.

## Usage
Type `/deadcode` in Claude Code to execute this command.

## Action
When this command is executed, Claude should:

1. **Analyze Project Structure**: Identify the project type and main entry points
2. **Scan for Unused Code**: Look for:
   - Unused imports/requires
   - Unreferenced variables and functions
   - Unused classes and methods
   - Orphaned files with no references
   - Unused dependencies in package.json/requirements.txt
3. **Check Build Tools**: Run language-specific dead code tools:
   - **JavaScript/TypeScript**: `npx ts-prune`, `npx unimported`, ESLint unused vars
   - **Python**: `vulture`, `unimport`, unused imports
   - **Java**: IDE analysis or `mvn dependency:analyze`
   - **Go**: `go mod tidy`, unused imports
4. **Manual Analysis**: Search for patterns like:
   - Functions/methods never called
   - Constants/variables never referenced
   - CSS classes not used in templates
   - Configuration keys not accessed
5. **Generate Report**: Create summary of findings with:
   - File locations of dead code
   - Confidence level (high/medium/low)
   - Estimated lines of code that can be removed
   - Potential impact of removal
6. **Provide Recommendations**: Suggest safe removal strategies

## Detection Strategy
- **High Confidence**: Clear unused imports, unreferenced private methods
- **Medium Confidence**: Public methods with no apparent usage
- **Low Confidence**: Dynamic imports, reflection usage, config files

## Output Format
```
🧹 Dead Code Analysis Report

📊 Summary:
- Unused imports: X files
- Unreferenced functions: Y items
- Orphaned files: Z files
- Unused dependencies: W packages

🎯 High Confidence Removals:
- file.js:15 - unused import 'lodash'
- utils.ts:42 - unreferenced function 'oldHelper'

⚠️  Review Required:
- api.js:78 - public method 'deprecatedEndpoint' (check external usage)
- config.json - unused keys: 'oldSetting1', 'oldSetting2'

💾 Potential Savings: ~XXX lines of code
```

## Language-Specific Tools
- **JavaScript/TypeScript**: Check for unimported, ts-prune, ESLint
- **Python**: Try vulture, unimport, or manual grep analysis
- **Java**: Maven dependency analysis, unused import detection
- **Go**: go mod tidy, goimports analysis
- **CSS**: PurgeCSS analysis for unused styles

## Safety Measures
- Never automatically delete code without user confirmation
- Warn about potential false positives (dynamic imports, reflection)
- Suggest testing after removal
- Recommend version control backup before bulk deletions
- Flag code that might be used by external systems/APIs

## Error Handling
- If no dead code tools are available, perform manual analysis
- If project structure is unclear, ask for main entry points
- Provide manual removal instructions if automated tools fail
- Warn about limitations of static analysis