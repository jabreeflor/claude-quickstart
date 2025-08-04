# Mermaid MCP Setup

You are a helpful assistant that will guide the user through setting up the Mermaid MCP server with Claude Code integration for generating diagrams and charts. The Model Context Protocol (MCP) is an open protocol that enables LLMs to access external tools and data sources, providing powerful diagram generation capabilities.

## Claude Code MCP Overview
MCP supports multiple transport types:
- **stdio** - Standard input/output communication (recommended for Mermaid)
- **SSE** - Server-Sent Events for web-based diagram generation
- **streamable** - Streamable HTTP for real-time diagram updates

Configuration can be applied at three scope levels:
- **Local** - Personal, project-specific diagram generation
- **Project** - Team-shared diagram configurations in `.mcp.json`
- **User** - Cross-project diagram servers accessible everywhere

## Overview
Mermaid MCP enables AI to dynamically generate mermaid diagrams and charts with full syntax support, theme configuration, and multiple export formats (PNG, SVG, mermaid), perfect for Claude Code's documentation and workflow visualization needs.

## Installation Steps

### Step 1: Choose Installation Method

#### Option A: Direct NPX (Recommended)
No installation required - uses npx to run directly.

#### Option B: Global Installation
For better performance or custom transport options:
```bash
npm install -g mcp-mermaid
```

### Step 2: Configure MCP with Claude Code

#### Option A: Using Claude Code CLI (Recommended)
Configure Mermaid MCP using the Claude Code command:

**For Mac/Linux:**
```bash
# Add Mermaid MCP server at project scope
claude mcp add mcp-mermaid \
  --command npx \
  --args "-y,mcp-mermaid" \
  --scope project

# Alternative: Add at user scope for all projects
claude mcp add mcp-mermaid \
  --command npx \
  --args "-y,mcp-mermaid" \
  --scope user
```

**For Windows:**
```bash
# Add Mermaid MCP server at project scope
claude mcp add mcp-mermaid \
  --command cmd \
  --args "/c,npx,-y,mcp-mermaid" \
  --scope project
```

#### Option B: Manual JSON Configuration

**For Mac/Linux Systems:**
```json
{
  "mcpServers": {
    "mcp-mermaid": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-mermaid"
      ]
    }
  }
}
```

**For Windows Systems:**
```json
{
  "mcpServers": {
    "mcp-mermaid": {
      "command": "cmd",
      "args": [
        "/c",
        "npx", 
        "-y",
        "mcp-mermaid"
      ]
    }
  }
}
```

#### Option C: HTTP/SSE Transport (Advanced)
For web-based access or when STDIO isn't suitable:

1. **Install globally first:**
   ```bash
   npm install -g mcp-mermaid
   ```

2. **Configure with Claude Code CLI:**
   ```bash
   # Add SSE transport server
   claude mcp add mcp-mermaid-sse \
     --type sse \
     --url http://localhost:3033/sse \
     --scope project
   
   # Add Streamable transport server
   claude mcp add mcp-mermaid-streamable \
     --type streamableHttp \
     --url http://localhost:3033/mcp \
     --scope project
   ```

3. **Start the transport servers:**
   ```bash
   # Run with SSE transport
   mcp-mermaid -t sse
   # Access at: http://localhost:3033/sse
   
   # Run with Streamable transport
   mcp-mermaid -t streamable
   # Access at: http://localhost:3033/mcp
   ```

4. **Custom configuration with environment variables:**
   ```bash
   # Set custom port and endpoint
   export MERMAID_MCP_PORT=8080
   export MERMAID_MCP_ENDPOINT=/custom-endpoint
   
   # Add to Claude Code with variables
   claude mcp add mcp-mermaid-custom \
     --type streamableHttp \
     --url "http://localhost:${MERMAID_MCP_PORT}${MERMAID_MCP_ENDPOINT}" \
     --scope project
   ```

## CLI Options
Available command-line options for mcp-mermaid:
- `--transport, -t`: Protocol ("stdio", "sse", "streamable") - default: "stdio"
- `--port, -p`: Port for SSE/streamable transport - default: 3033
- `--endpoint, -e`: Custom endpoint path
- `--help, -h`: Show help message

## Authentication & Security

### Managing Authentication with Claude Code
Use Claude Code's `/mcp` command for Mermaid MCP management:
```bash
# Check Mermaid server status
/mcp status mcp-mermaid

# Restart Mermaid server
/mcp restart mcp-mermaid

# View Mermaid logs for troubleshooting
/mcp logs mcp-mermaid
```

### Security Considerations
**Important**: Mermaid MCP generates diagrams and charts. Be aware of:
- **Local Processing**: Diagrams are generated locally for security
- **File System Access**: MCP may create temporary files for diagram generation
- **Third-party Risk**: Use mcp-mermaid responsibly and keep it updated
- **Export Security**: Be cautious when sharing generated diagrams externally

### Resource Usage with @ Mentions
Reference Mermaid MCP resources in Claude Code using `@` syntax:
- `@mcp-mermaid` - Reference the Mermaid server directly
- Execute diagram generation as slash commands
- Build custom workflows with Mermaid diagram creation

## Verification & Testing

### Claude Code Integration Tests
1. **Server Status Check**:
   ```bash
   claude mcp list
   # Should show mcp-mermaid as active
   ```

2. **Diagram Generation Test**:
   ```bash
   # Test diagram generation (use in Claude Code conversation)
   @mcp-mermaid generate_flowchart "Start -> Process -> End"
   
   # Test with specific theme
   @mcp-mermaid generate_diagram --theme dark --format svg
   ```

3. **Claude Code Feature Test**:
   - Use `@mcp-mermaid` mentions in conversations
   - Test diagram generation with different formats
   - Verify export capabilities (PNG, SVG, mermaid)

### Mermaid Service Verification
- Test local diagram generation
- Verify all supported diagram types work
- Confirm export format functionality

## Integration with Claude Code Workflows

Mermaid MCP enhances Claude Code's documentation and visualization:

### Documentation Integration
Mermaid can automatically generate diagrams for:
- Architecture documentation in CLAUDE.md
- Process flow diagrams for complex workflows
- System design visualizations
- Code structure and dependency graphs

### Slash Command Integration
Create custom slash commands that leverage Mermaid:
- `/diagram-architecture` - Generate system architecture diagrams
- `/workflow-chart` - Create process flow diagrams
- `/dependency-graph` - Visualize code dependencies

## Verification Features
Once configured, you should have access to:
- **Full Mermaid Syntax**: Support for all mermaid diagram types
- **Theme Configuration**: backgroundColor and theme customization
- **Multiple Export Formats**: PNG, SVG, and mermaid source
- **Syntax Validation**: Ensures correct mermaid syntax generation
- **Rich Styling**: AI can output detailed style configurations
- **Claude Code Integration**: Seamless diagram generation within conversations

## Supported Diagram Types
The Mermaid MCP supports all mermaid diagram types:
- Flowcharts
- Sequence diagrams
- Class diagrams
- State diagrams
- Entity relationship diagrams
- User journey diagrams
- Gantt charts
- Pie charts
- Git graphs
- And more...

## Usage Examples with Claude Code
The Mermaid MCP enables:
- **Dynamic Diagram Generation**: Create diagrams from natural language descriptions in Claude Code conversations
- **Visual Process Documentation**: Generate workflow diagrams for CLAUDE.md and project documentation
- **Technical Architecture Visualization**: Create system design diagrams during planning sessions
- **Interactive Chart Creation**: Build data visualization charts for analysis and reporting
- **Multi-format Export**: Export diagrams in PNG, SVG, or mermaid format for various use cases
- **Real-time Collaboration**: Generate and iterate on diagrams during team discussions

### Example Claude Code Workflows:
```bash
# Generate architecture diagram during planning
"@mcp-mermaid create a system architecture diagram showing frontend, backend, and database components"

# Create workflow diagram for process documentation
"@mcp-mermaid generate a flowchart for the user authentication process"

# Visualize code dependencies
"@mcp-mermaid create a diagram showing the relationships between our main modules"
```

## Troubleshooting

### Common Issues
1. **Mermaid Server Won't Start**:
   ```bash
   # Check mcp-mermaid installation
   npm list -g mcp-mermaid
   
   # Verify npx can find mcp-mermaid
   npx mcp-mermaid --help
   ```

2. **Claude Code Can't Connect**:
   ```bash
   # Verify server configuration
   claude mcp list
   
   # Check Mermaid logs
   claude mcp logs mcp-mermaid --tail 20
   ```

3. **Diagram Generation Issues**:
   ```bash
   # Test mcp-mermaid directly
   echo '{"method": "generate", "params": {"type": "flowchart", "content": "A --> B"}}' | npx mcp-mermaid
   
   # Check available diagram types
   npx mcp-mermaid --list-types
   ```

4. **Export Format Problems**:
   ```bash
   # Verify export dependencies
   npx mcp-mermaid --check-deps
   
   # Test specific format export
   npx mcp-mermaid --format png --test
   ```

### Transport-Specific Issues
1. **SSE Transport Problems**:
   ```bash
   # Check if port is available
   lsof -i :3033
   
   # Test SSE endpoint
   curl http://localhost:3033/sse
   ```

2. **Streamable Transport Issues**:
   ```bash
   # Test streamable endpoint
   curl http://localhost:3033/mcp
   
   # Check server logs
   mcp-mermaid -t streamable --verbose
   ```

### Log Analysis
Monitor Mermaid MCP activity:
```bash
# View recent Mermaid logs
claude mcp logs mcp-mermaid --tail 50

# Monitor live diagram generation
claude mcp logs mcp-mermaid --follow

# Debug diagram syntax issues
claude mcp logs mcp-mermaid --level debug
```

Your Claude Code client can now generate rich visual diagrams and charts using natural language descriptions, with full integration into your development workflow.