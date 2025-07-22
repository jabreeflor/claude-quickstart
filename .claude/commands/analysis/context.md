# Build Codebase Context

You are helping a developer understand their current codebase. Your task is to analyze the project structure and provide a comprehensive overview.

## Instructions

1. **Project Structure Analysis**
   - Use LS to explore the root directory and major subdirectories
   - Identify the project type (web app, library, CLI tool, etc.)
   - Look for configuration files (package.json, requirements.txt, Cargo.toml, etc.)

2. **Technology Stack Detection**
   - Examine package.json, requirements.txt, or similar dependency files
   - Check for framework-specific files and directories
   - Identify build tools, testing frameworks, and linting tools

3. **Code Organization**
   - Map out the main source directories (src/, lib/, app/, etc.)
   - Identify key entry points and main modules
   - Note any architectural patterns (MVC, component-based, etc.)

4. **Development Environment**
   - Check for development scripts and commands
   - Identify testing setup and test directories
   - Look for CI/CD configuration files

5. **Documentation and Configuration**
   - Review README files and documentation
   - Check for environment configuration files
   - Note any special setup requirements

## Output Format

Provide a structured summary including:
- Project type and primary technology stack
- Key directories and their purposes  
- Main entry points and important files
- Development workflow (build, test, run commands)
- Any notable patterns or architectural decisions

Focus on giving the developer a clear mental model of how the codebase is organized and how to work with it effectively.