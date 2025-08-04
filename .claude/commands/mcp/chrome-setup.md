# Chrome MCP Quick Setup

You are a helpful assistant that will guide the user through setting up Chrome MCP Server with Claude Code integration. The Model Context Protocol (MCP) is an open protocol that enables LLMs to access external tools and data sources, providing powerful browser automation capabilities.

## Claude Code MCP Overview
MCP supports multiple transport types:
- **stdio** - Standard input/output communication
- **SSE** - Server-Sent Events for web-based access  
- **HTTP** - Traditional HTTP-based communication

Configuration can be applied at three scope levels:
- **Local** - Personal, project-specific servers
- **Project** - Team-shared configurations in `.mcp.json`
- **User** - Cross-project servers accessible everywhere

## Prerequisites Check
First, verify the user has the required prerequisites:
- Node.js >= 18.19.0 
- pnpm or npm installed
- Chrome/Chromium browser
- Claude Code CLI installed and configured

## Installation Steps

### Step 1: Download Chrome Extension
Guide the user to download the latest Chrome extension:
- Go to https://github.com/hangwin/mcp-chrome/releases
- Download the latest release
- Extract the extension files

### Step 2: Install mcp-chrome-bridge
Help the user install the bridge globally:

For npm users:
```bash
npm install -g mcp-chrome-bridge
```

For pnpm users (recommended approach):
```bash
# Enable scripts globally first
pnpm config set enable-pre-post-scripts true
pnpm install -g mcp-chrome-bridge
```

If automatic registration fails with pnpm:
```bash
pnpm install -g mcp-chrome-bridge
mcp-chrome-bridge register
```

### Step 3: Load Chrome Extension
Guide the user through loading the extension:
1. Open Chrome and navigate to `chrome://extensions/`
2. Enable "Developer mode" (toggle in top right)
3. Click "Load unpacked" 
4. Select the extracted extension folder from Step 1
5. Click the extension icon and then "connect" to see MCP configuration

### Step 4: Configure MCP with Claude Code

#### Option A: Using Claude Code CLI (Recommended)
Configure Chrome MCP using the Claude Code command:

```bash
# Add Chrome MCP server at project scope
claude mcp add chrome-mcp-server \
  --type streamableHttp \
  --url http://127.0.0.1:12306/mcp \
  --scope project

# Alternative: Add at user scope for all projects
claude mcp add chrome-mcp-server \
  --type streamableHttp \
  --url http://127.0.0.1:12306/mcp \
  --scope user
```

#### Option B: Manual JSON Configuration
Add this streamable HTTP configuration to your MCP settings:

```json
{
  "mcpServers": {
    "chrome-mcp-server": {
      "type": "streamableHttp", 
      "url": "http://127.0.0.1:12306/mcp"
    }
  }
}
```

#### Option C: STDIO Configuration (Advanced)
For custom setups or when HTTP transport isn't suitable:

1. First find the installation path:
   ```bash
   npm list -g mcp-chrome-bridge
   # or
   pnpm list -g mcp-chrome-bridge
   ```

2. Add using Claude Code CLI:
   ```bash
   claude mcp add chrome-mcp-stdio \
     --command npx \
     --args "node,/path/to/mcp-chrome-bridge/dist/mcp/mcp-server-stdio.js" \
     --scope project
   ```

3. Or use manual JSON configuration:
   ```json
   {
     "mcpServers": {
       "chrome-mcp-stdio": {
         "command": "npx",
         "args": [
           "node", 
           "/path/to/mcp-chrome-bridge/dist/mcp/mcp-server-stdio.js"
         ]
       }
     }
   }
   ```

## Authentication & Security

### Managing Authentication
Use Claude Code's `/mcp` command to manage authentication:
```bash
# Check MCP server status
/mcp status

# Restart a specific MCP server
/mcp restart chrome-mcp-server

# View MCP server logs
/mcp logs chrome-mcp-server
```

### Security Considerations
**Important**: Chrome MCP provides powerful browser automation capabilities. Be aware of:
- **Third-party Risk**: Use MCP servers at your own risk and verify their security
- **Browser Access**: Full access to your Chrome browser and all logged-in sessions
- **Network Exposure**: HTTP transport exposes server locally on port 12306
- **Extension Permissions**: The Chrome extension has broad browser permissions

### Resource Usage with @ Mentions
Reference Chrome MCP resources in Claude Code using `@` syntax:
- `@chrome-mcp-server` - Reference the server directly
- Execute MCP prompts as slash commands for automation workflows

## Verification & Testing

### Claude Code Integration Tests
1. **Server Status Check**:
   ```bash
   claude mcp list
   # Should show chrome-mcp-server as active
   ```

2. **Connection Test**:
   ```bash
   curl http://127.0.0.1:12306/mcp
   # Should return MCP protocol response
   ```

3. **Claude Code Feature Test**:
   - Use `@chrome-mcp-server` mentions in conversations
   - Test browser automation through Claude Code interface
   - Verify screenshot and content analysis capabilities

### Browser Extension Verification
- Chrome extension should show "Connected" status
- Extension icon should be active in Chrome toolbar
- Test basic automation through extension interface

## Key Features Available
Inform the user they now have access to:
- **Browser Management**: 6 tools for tab and window control
- **Screenshots & Visual**: Capture full pages or specific elements  
- **Network Monitoring**: 4 tools for request analysis
- **Content Analysis**: 4 tools for semantic search and text extraction
- **Interaction**: 3 tools for browser automation
- **Data Management**: 5 tools for bookmarks, history, etc.

The setup leverages their existing Chrome browser with all login states and configurations preserved, making it more efficient than traditional automation tools.

## Troubleshooting

### Common Issues
1. **MCP Server Won't Start**:
   ```bash
   # Check if bridge is properly installed
   mcp-chrome-bridge --version
   
   # Re-register the bridge
   mcp-chrome-bridge register
   ```

2. **Claude Code Can't Connect**:
   ```bash
   # Verify server configuration
   claude mcp list
   
   # Restart the MCP server
   claude mcp restart chrome-mcp-server
   ```

3. **Extension Connection Issues**:
   - Reload the Chrome extension
   - Check if port 12306 is available
   - Verify the extension has proper permissions

4. **Environment Variables**:
   ```bash
   # Set custom port if needed
   export MCP_CHROME_PORT=12307
   
   # Enable debug logging
   export MCP_CHROME_DEBUG=true
   ```

### Log Analysis
Check Claude Code MCP logs for detailed troubleshooting:
```bash
# View recent logs
claude mcp logs chrome-mcp-server --tail 50

# Monitor live logs
claude mcp logs chrome-mcp-server --follow
```