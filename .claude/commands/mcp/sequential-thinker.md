# Sequential Thinker MCP Setup

You are a helpful assistant that will guide the user through setting up the Sequential Thinker MCP server with Claude Code integration. The Model Context Protocol (MCP) is an open protocol that enables LLMs to access external tools and data sources, providing advanced reasoning capabilities for complex problem solving.

## Claude Code MCP Overview
MCP supports multiple transport types:
- **stdio** - Standard input/output communication (recommended for Sequential Thinker)
- **SSE** - Server-Sent Events for web-based reasoning access
- **HTTP** - Traditional HTTP-based communication for distributed reasoning

Configuration can be applied at three scope levels:
- **Local** - Personal, project-specific reasoning enhancement
- **Project** - Team-shared reasoning configurations in `.mcp.json`
- **User** - Cross-project reasoning servers accessible everywhere

## Overview
Sequential Thinker MCP provides advanced reasoning capabilities with step-by-step thinking processes for complex problem solving, perfect for Claude Code's extended thinking and analytical workflows.

## Installation Steps

### Step 1: Install Sequential Thinker MCP
```bash
npm install -g @modelcontextprotocol/server-sequential-thinking
```

### Step 2: Configure MCP with Claude Code

#### Option A: Using Claude Code CLI (Recommended)
Configure Sequential Thinker MCP using the Claude Code command:

```bash
# Add Sequential Thinker MCP server at project scope
claude mcp add sequential-thinker \
  --command npx \
  --args "@modelcontextprotocol/server-sequential-thinking" \
  --scope project

# Alternative: Add at user scope for all projects
claude mcp add sequential-thinker \
  --command npx \
  --args "@modelcontextprotocol/server-sequential-thinking" \
  --scope user
```

#### Option B: Manual JSON Configuration
Add this configuration to your MCP settings:

```json
{
  "mcpServers": {
    "sequential-thinker": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-sequential-thinking"
      ]
    }
  }
}
```

#### Option C: Direct Node Execution (Advanced)
For custom setups or specific Node.js configurations:

1. First find the installation path:
   ```bash
   npm list -g @modelcontextprotocol/server-sequential-thinking
   ```

2. Add using Claude Code CLI:
   ```bash
   claude mcp add sequential-thinker-direct \
     --command node \
     --args "/path/to/server-sequential-thinking/dist/index.js" \
     --scope project
   ```

3. Or use manual JSON configuration:
   ```json
   {
     "mcpServers": {
       "sequential-thinker": {
         "command": "node",
         "args": [
           "/path/to/server-sequential-thinking/dist/index.js"
         ]
       }
     }
   }
   ```

## Authentication & Security

### Managing Authentication with Claude Code
Use Claude Code's `/mcp` command for Sequential Thinker management:
```bash
# Check Sequential Thinker server status
/mcp status sequential-thinker

# Restart Sequential Thinker server
/mcp restart sequential-thinker

# View Sequential Thinker logs for troubleshooting
/mcp logs sequential-thinker
```

### Security Considerations
**Important**: Sequential Thinker MCP processes reasoning and analysis. Be aware of:
- **Data Processing**: Reasoning operations may process sensitive information
- **Local Processing**: All reasoning is performed locally for security
- **Third-party Risk**: Use Sequential Thinker MCP responsibly and keep it updated
- **Resource Usage**: Complex reasoning may consume significant computational resources

### Resource Usage with @ Mentions
Reference Sequential Thinker MCP resources in Claude Code using `@` syntax:
- `@sequential-thinker` - Reference the Sequential Thinker server directly
- Execute complex reasoning as slash commands
- Build custom analytical workflows with structured thinking

## Verification & Testing

### Claude Code Integration Tests
1. **Server Status Check**:
   ```bash
   claude mcp list
   # Should show sequential-thinker as active
   ```

2. **Reasoning Operations Test**:
   ```bash
   # Test sequential reasoning (use in Claude Code conversation)
   @sequential-thinker analyze_problem "How to optimize database performance"
   
   # Test step-by-step breakdown
   @sequential-thinker breakdown_task "Implement user authentication system"
   ```

3. **Claude Code Feature Test**:
   - Use `@sequential-thinker` mentions in conversations
   - Test complex problem analysis capabilities
   - Verify step-by-step reasoning outputs

### Sequential Thinker Service Verification
- Verify reasoning engine is responsive
- Test complex multi-step problem solving
- Confirm logical flow analysis works

## Integration with Claude Code Extended Thinking

Sequential Thinker MCP enhances Claude Code's analytical capabilities:

### Extended Thinking Integration
Use Sequential Thinker with Claude Code for:
- **Complex Problem Analysis**: Break down intricate technical challenges
- **Decision Making**: Structure complex decisions with logical reasoning
- **Architecture Planning**: Analyze system design decisions step-by-step
- **Code Review**: Systematic analysis of code quality and design patterns

### Analytical Documentation
Sequential Thinker can automatically generate:
- Step-by-step analysis reports
- Decision-making documentation
- Problem breakdown structures
- Logical reasoning chains for complex decisions

## Verification Features
Once configured, you should have access to:
- **Sequential Reasoning**: Step-by-step problem breakdown with logical flow
- **Logical Thinking**: Structured thought processes for complex decisions
- **Complex Problem Solving**: Multi-step analysis capabilities with dependencies
- **Analytical Framework**: Systematic approach to multi-part questions and challenges
- **Claude Code Integration**: Enhanced reasoning within extended thinking sessions

## Usage Examples with Claude Code
The Sequential Thinker MCP enables:
- **Complex Problem Breakdown**: Systematically analyze intricate technical challenges
- **Structured Decision Making**: Apply logical reasoning to architectural and design decisions
- **Multi-step Analysis**: Handle complex questions that require sequential reasoning
- **Enhanced Planning**: Break down project plans into logical, sequential steps
- **Code Architecture Analysis**: Systematically evaluate system design decisions

### Example Claude Code Workflows:
```bash
# Analyze complex technical problem
"@sequential-thinker break down the performance optimization challenge for our microservices architecture"

# Structure architectural decision
"@sequential-thinker analyze the trade-offs between SQL and NoSQL for our user data requirements"

# Plan complex implementation
"@sequential-thinker create a step-by-step plan for migrating from monolith to microservices"
```

## Troubleshooting

### Common Issues
1. **Sequential Thinker Server Won't Start**:
   ```bash
   # Check Sequential Thinker installation
   npm list -g @modelcontextprotocol/server-sequential-thinking
   
   # Verify npx can find the server
   npx @modelcontextprotocol/server-sequential-thinking --help
   ```

2. **Claude Code Can't Connect**:
   ```bash
   # Verify server configuration
   claude mcp list
   
   # Check Sequential Thinker logs
   claude mcp logs sequential-thinker --tail 20
   ```

3. **Reasoning Performance Issues**:
   ```bash
   # Test reasoning engine directly
   echo '{"method": "analyze", "params": {"problem": "simple test"}}' | npx @modelcontextprotocol/server-sequential-thinking
   
   # Check system resources
   top -p $(pgrep -f sequential-thinking)
   ```

4. **Complex Analysis Timeouts**:
   ```bash
   # Increase timeout values
   export SEQUENTIAL_THINKER_TIMEOUT=120000
   claude mcp restart sequential-thinker
   ```

### Performance Optimization
1. **Memory Usage**:
   ```bash
   # Monitor memory usage during analysis
   ps aux | grep sequential-thinking
   
   # Set memory limits if needed
   export NODE_OPTIONS="--max-old-space-size=4096"
   ```

2. **Analysis Complexity**:
   ```bash
   # Limit analysis depth for performance
   export SEQUENTIAL_THINKER_MAX_DEPTH=10
   
   # Enable performance profiling
   export SEQUENTIAL_THINKER_PROFILE=true
   ```

### Log Analysis
Monitor Sequential Thinker MCP activity:
```bash
# View recent Sequential Thinker logs
claude mcp logs sequential-thinker --tail 50

# Monitor live reasoning operations
claude mcp logs sequential-thinker --follow

# Debug specific reasoning issues
claude mcp logs sequential-thinker --level debug --filter analysis
```

Your Claude Code client can now leverage advanced sequential thinking capabilities for comprehensive problem analysis and structured reasoning workflows.