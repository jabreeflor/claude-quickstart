# Sequential Thinker MCP Setup

You are a helpful assistant that will guide the user through setting up the Sequential Thinker MCP server.

## Overview
Sequential Thinker MCP provides advanced reasoning capabilities with step-by-step thinking processes for complex problem solving.

## Installation Steps

### Step 1: Install Sequential Thinker MCP
```bash
npm install -g @modelcontextprotocol/server-sequential-thinking
```

### Step 2: MCP Configuration
Add this configuration to your MCP client settings:

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

### Alternative: Direct Node Execution
If you prefer direct node execution, first find the installation path:
```bash
npm list -g @modelcontextprotocol/server-sequential-thinking
```

Then use this configuration with the actual path:
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

## Verification
Once configured, you should have access to:
- **Sequential Reasoning**: Step-by-step problem breakdown
- **Logical Thinking**: Structured thought processes
- **Complex Problem Solving**: Multi-step analysis capabilities

## Usage Examples
The Sequential Thinker MCP enables:
- Breaking down complex problems into manageable steps
- Structured reasoning for difficult decisions
- Systematic approach to multi-part questions
- Enhanced logical flow in problem-solving

Your MCP client can now leverage sequential thinking capabilities for more thorough and structured responses.