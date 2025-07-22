# Claude Code Quick Start Setup

A comprehensive starter template for [Claude Code](https://claude.ai/code) with custom slash commands, best practices, and workflow optimizations.

## What is This Repository?

This repository serves as a learning and reference template for Claude Code best practices. It includes:

- **Custom slash commands** organized by category for common development workflows
- **CLAUDE.md configuration** with repository-specific guidance 
- **Best practice workflows** for efficient Claude Code usage
- **Example implementations** of testing, analysis, and Git workflows

## Quick Start

1. **Clone or download** this repository to your local machine
2. **Navigate** to the project directory in your terminal
3. **Start Claude Code** in the directory: `claude`
4. **Test the setup** by running `/test` to verify slash commands work

## Repository Structure

```
.claude/
├── commands/           # Custom slash commands organized by category
│   ├── analysis/       # Code analysis commands
│   │   ├── context.md  # Generate comprehensive codebase context
│   │   └── deadcode.md # Detect unused code
│   ├── git/           # Git workflow commands
│   │   ├── commitAndPush.md
│   │   ├── gitignore.md
│   │   ├── pr-review.md
│   │   ├── prdesc.md
│   │   └── resolveMerge.md
│   ├── testing/       # Testing and quality commands
│   │   ├── coverage-analysis/
│   │   │   ├── java-coverage-analysis.md
│   │   │   └── jest-coverage-analysis.md
│   │   └── test-generation/
│   │       ├── angular-component-scaffold.md
│   │       ├── java-generate-unit-tests.md
│   │       └── jest-generate-unit-tests.md
│   └── workflow/      # Task management commands
│       ├── spawn.md   # Delegate tasks to specialized agents
│       └── think.md   # Extended reasoning and planning
CLAUDE.md              # Repository-specific Claude Code configuration
.mcp.json             # Model Context Protocol configuration
```

## Available Commands

### Testing Commands
- `/jest-generate-unit-tests` - Generate comprehensive Jest unit tests
- `/java-generate-unit-tests` - Generate JUnit tests for Java classes
- `/angular-component-scaffold` - Create Angular component with tests
- `/jest-coverage-analysis` - Analyze and improve test coverage
- `/java-coverage-analysis` - Java-specific coverage analysis

### Git Workflow Commands
- `/commitAndPush` - Stage, commit with AI-generated message, and push
- `/prdesc` - Generate comprehensive pull request descriptions
- `/pr-review` - Perform thorough code review of pull requests
- `/resolveMerge` - Intelligently resolve merge conflicts
- `/gitignore` - Generate appropriate .gitignore files

### Analysis Commands
- `/context` - Generate comprehensive codebase understanding
- `/deadcode` - Identify and remove unused code

### Workflow Commands
- `/think` - Extended reasoning for complex problems
- `/spawn` - Create specialized agents for specific tasks

### System Commands
- `/test` - Verify slash command system functionality

## Usage Examples

### Generate Unit Tests
```bash
# For JavaScript/TypeScript projects
/jest-generate-unit-tests

# For Java projects  
/java-generate-unit-tests
```

### Analyze Your Codebase
```bash
# Get comprehensive codebase context
/context

# Find unused code
/deadcode
```

### Git Workflows
```bash
# Commit and push with AI-generated message
/commitAndPush

# Generate PR description
/prdesc
```

## Best Practices

### Recommended Workflow
1. **Explore** → Use `/context` to understand the codebase
2. **Plan** → Use `/think` for complex problem analysis
3. **Code** → Implement with Claude Code assistance
4. **Test** → Use testing commands to ensure quality
5. **Commit** → Use `/commitAndPush` for clean commits

### Tips for Success
- **Be specific** in your instructions rather than vague
- **Use tab completion** to reference files and folders
- **Provide visual context** (screenshots, mockups) when relevant
- **Break complex tasks** into smaller, manageable steps
- **Use `/clear`** to reset context between different tasks
- **Course correct early** using the Escape key

### Context Management
- Keep CLAUDE.md focused on actionable information
- Use the `#` key to automatically add content to CLAUDE.md during sessions
- Document frequently used patterns and project-specific commands

## Customization

### Adding New Commands
1. Create a new `.md` file in the appropriate category folder under `.claude/commands/`
2. Follow the existing command structure and format
3. Test the command with Claude Code

### Modifying CLAUDE.md
Update `CLAUDE.md` with:
- Project-specific guidelines
- Common workflows for your codebase
- Custom commands and their usage
- Development environment setup instructions

## Requirements

- [Claude Code CLI](https://claude.ai/code) installed and configured
- Git (for Git workflow commands)
- Node.js/npm (for JavaScript/TypeScript commands)
- Java/Maven (for Java commands)
- GitHub CLI (for advanced Git commands)

## Contributing

This repository serves as a template and learning resource. Feel free to:
- Fork and customize for your own projects
- Submit improvements to existing commands
- Add new useful slash commands
- Share feedback and suggestions

## License

MIT License - feel free to use this template for any purpose.

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Claude Code Best Practices](https://docs.anthropic.com/en/docs/claude-code/common-workflows)
- [Custom Slash Commands Guide](https://docs.anthropic.com/en/docs/claude-code/slash-commands)