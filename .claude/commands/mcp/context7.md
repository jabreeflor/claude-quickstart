# Context7 MCP Setup

You are a helpful assistant that will guide the user through setting up the Context7 MCP server with Claude Code integration. The Model Context Protocol (MCP) is an open protocol that enables LLMs to access external tools and data sources, providing enhanced context management and retrieval capabilities.

## Claude Code MCP Overview
MCP supports multiple transport types:
- **stdio** - Standard input/output communication (recommended for Context7)
- **SSE** - Server-Sent Events for web-based access  
- **HTTP** - Traditional HTTP-based communication

Configuration can be applied at three scope levels:
- **Local** - Personal, project-specific context management
- **Project** - Team-shared context configurations in `.mcp.json`
- **User** - Cross-project context servers accessible everywhere

## Overview
Context7 MCP provides enhanced context management and retrieval capabilities for maintaining conversation context across sessions, perfect for Claude Code's extended thinking and memory management features.

## Installation Steps

### Step 1: Install Context7 MCP
```bash
npm install -g @context7/mcp-server
```

### Step 2: Configure MCP with Claude Code

#### Option A: Using Claude Code CLI (Recommended)
Configure Context7 MCP using the Claude Code command:

```bash
# Add Context7 MCP server at project scope
claude mcp add context7 \
  --command npx \
  --args "@context7/mcp-server" \
  --scope project

# Alternative: Add at user scope for cross-project context
claude mcp add context7 \
  --command npx \
  --args "@context7/mcp-server" \
  --scope user
```

#### Option B: Manual JSON Configuration
Add this configuration to your MCP settings:

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

#### Option C: Direct Node Execution (Advanced)
For custom setups or specific Node.js configurations:

1. First find the installation path:
   ```bash
   npm list -g @context7/mcp-server
   ```

2. Add using Claude Code CLI:
   ```bash
   claude mcp add context7-direct \
     --command node \
     --args "/path/to/@context7/mcp-server/dist/index.js" \
     --scope project
   ```

3. Or use manual JSON configuration:
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

### Environment Configuration with Claude Code
Context7 supports environment variable expansion in Claude Code MCP configurations:

```bash
# Set Context7 environment variables
export CONTEXT7_API_KEY=your_api_key_here
export CONTEXT7_WORKSPACE=your_workspace_id
export CONTEXT7_DATA_PATH=/path/to/context/storage
```

You can reference these in your MCP configuration:
```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["@context7/mcp-server"],
      "env": {
        "CONTEXT7_API_KEY": "${CONTEXT7_API_KEY}",
        "CONTEXT7_WORKSPACE": "${CONTEXT7_WORKSPACE}",
        "CONTEXT7_DATA_PATH": "${CONTEXT7_DATA_PATH}"
      }
    }
  }
}
```

## Authentication & Security

### Managing Authentication with Claude Code
Use Claude Code's `/mcp` command for Context7 management:
```bash
# Check Context7 server status
/mcp status context7

# Restart Context7 server
/mcp restart context7

# View Context7 logs for troubleshooting
/mcp logs context7
```

### Security Considerations
**Important**: Context7 MCP handles sensitive conversation data. Be aware of:
- **Data Privacy**: Context data is stored locally or in configured workspace
- **API Key Security**: Ensure Context7 API keys are properly secured and not logged
- **Third-party Risk**: Use Context7 services responsibly and review their privacy policy
- **Access Control**: Context7 has access to conversation history and context data

### Resource Usage with @ Mentions
Reference Context7 MCP resources in Claude Code using `@` syntax:
- `@context7` - Reference the Context7 server directly
- Execute context retrieval and management as slash commands
- Build custom workflows with Context7 context management

## Verification & Testing

### Claude Code Integration Tests
1. **Server Status Check**:
   ```bash
   claude mcp list
   # Should show context7 as active
   ```

2. **Context Operations Test**:
   ```bash
   # Test context storage (use in Claude Code conversation)
   @context7 save_context "project_status" "Working on MCP enhancement"
   
   # Test context retrieval
   @context7 get_context "project_status"
   ```

3. **Claude Code Feature Test**:
   - Use `@context7` mentions in conversations
   - Test context persistence across sessions
   - Verify context search capabilities

### Context7 Service Verification
- Verify API key authentication (if using Context7 cloud)
- Test local context storage and retrieval
- Confirm workspace access and permissions

## Integration with Claude Code Memory Management

Context7 MCP enhances Claude Code's built-in memory features:

### CLAUDE.md Integration
Context7 can automatically update and reference your `CLAUDE.md` file:
- Store project-specific context and decisions
- Maintain coding patterns and preferences
- Track long-term project evolution

### Extended Thinking Support
Use Context7 with Claude Code extended thinking:
- Maintain context across multiple thinking sessions
- Build upon previous analysis and decisions
- Create persistent knowledge graphs for projects

## Key Features Available
Context7 MCP provides:
- **Context Persistence**: Save and retrieve conversation context across sessions
- **Session Management**: Maintain continuity in long-term projects
- **Context Search**: Find relevant context from previous interactions using semantic search
- **Memory Management**: Efficient context storage and retrieval with Claude Code integration
- **Workspace Integration**: Team-shared context management for collaborative projects
- **Automatic Context Updates**: Keep CLAUDE.md and project context synchronized

## Troubleshooting

### Common Issues
1. **Context7 Server Won't Start**:
   ```bash
   # Check Context7 installation
   npm list -g @context7/mcp-server
   
   # Verify API key configuration
   echo $CONTEXT7_API_KEY
   ```

2. **Claude Code Can't Connect**:
   ```bash
   # Verify server configuration
   claude mcp list
   
   # Check Context7 logs
   claude mcp logs context7 --tail 20
   ```

3. **Context Storage Issues**:
   ```bash
   # Check data path permissions
   ls -la $CONTEXT7_DATA_PATH
   
   # Verify workspace access
   curl -H "Authorization: Bearer $CONTEXT7_API_KEY" \
        https://api.context7.com/workspaces/$CONTEXT7_WORKSPACE
   ```

4. **Environment Variable Issues**:
   ```bash
   # Debug environment variable expansion
   claude mcp restart context7 --debug
   
   # Verify all required variables are set
   env | grep CONTEXT7
   ```

### Log Analysis
Monitor Context7 MCP activity:
```bash
# View recent Context7 logs
claude mcp logs context7 --tail 50

# Monitor live context operations
claude mcp logs context7 --follow

# Debug context search and retrieval
claude mcp logs context7 --level debug
```