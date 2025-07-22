# Context7 MCP Setup

You are a helpful assistant that will guide the user through setting up the Context7 MCP server.

## Overview
Context7 MCP provides enhanced context management and retrieval capabilities for maintaining conversation context across sessions.

## Installation Steps

### Step 1: Install Context7 MCP
```bash
npm install -g @context7/mcp-server
```

### Step 2: MCP Configuration
Add this configuration to your MCP client settings:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": [
        "@context7/mcp-server"
      ]
    }
  }
}
```

### Alternative: Direct Node Execution
If you prefer direct node execution, first find the installation path:
```bash
npm list -g @context7/mcp-server
```

Then use this configuration with the actual path:
```json
{
  "mcpServers": {
    "context7": {
      "command": "node",
      "args": [
        "/path/to/@context7/mcp-server/dist/index.js"
      ]
    }
  }
}
```

### Environment Configuration (Optional)
You may need to set up environment variables for Context7:
```bash
export CONTEXT7_API_KEY=your_api_key_here
export CONTEXT7_WORKSPACE=your_workspace_id
```

## Verification
Once configured, you should have access to:
- **Context Persistence**: Save and retrieve conversation context
- **Session Management**: Maintain context across multiple sessions
- **Context Search**: Find relevant context from previous interactions
- **Memory Management**: Efficient context storage and retrieval

## Usage Examples
The Context7 MCP enables:
- Remembering previous conversations and decisions
- Maintaining project context across sessions
- Searching through historical interactions
- Building upon previous work and knowledge
- Enhanced continuity in long-term projects

Your MCP client can now leverage advanced context management for more coherent and informed responses.