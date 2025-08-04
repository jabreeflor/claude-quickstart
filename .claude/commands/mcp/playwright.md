# Playwright MCP Setup

You are a helpful assistant that will guide the user through setting up the Playwright MCP server with Claude Code integration. The Model Context Protocol (MCP) is an open protocol that enables LLMs to access external tools and data sources, providing powerful browser automation capabilities for testing and web interaction.

## Claude Code MCP Overview
MCP supports multiple transport types:
- **stdio** - Standard input/output communication (recommended for Playwright)
- **SSE** - Server-Sent Events for web-based browser automation
- **HTTP** - Traditional HTTP-based communication for remote browser control

Configuration can be applied at three scope levels:
- **Local** - Personal, project-specific browser automation
- **Project** - Team-shared browser testing configurations in `.mcp.json`
- **User** - Cross-project browser automation servers accessible everywhere

## Overview
Playwright MCP provides browser automation capabilities for web scraping, testing, and interaction with web applications, perfect for Claude Code's testing workflows and web development tasks.

## Installation Steps

### Step 1: Install Playwright MCP
```bash
npm install -g @modelcontextprotocol/server-playwright
```

### Step 2: Install Playwright Browsers
```bash
npx playwright install
```

### Step 3: Configure MCP with Claude Code

#### Option A: Using Claude Code CLI (Recommended)
Configure Playwright MCP using the Claude Code command:

```bash
# Add Playwright MCP server at project scope
claude mcp add playwright \
  --command npx \
  --args "@modelcontextprotocol/server-playwright" \
  --scope project

# Alternative: Add at user scope for all projects
claude mcp add playwright \
  --command npx \
  --args "@modelcontextprotocol/server-playwright" \
  --scope user
```

#### Option B: Manual JSON Configuration
Add this configuration to your MCP settings:

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-playwright"
      ]
    }
  }
}
```

#### Option C: Direct Node Execution (Advanced)
For custom setups or specific Node.js configurations:

1. First find the installation path:
   ```bash
   npm list -g @modelcontextprotocol/server-playwright
   ```

2. Add using Claude Code CLI:
   ```bash
   claude mcp add playwright-direct \
     --command node \
     --args "/path/to/server-playwright/dist/index.js" \
     --scope project
   ```

3. Or use manual JSON configuration:
   ```json
   {
     "mcpServers": {
       "playwright": {
         "command": "node",
         "args": [
           "/path/to/server-playwright/dist/index.js"
         ]
       }
     }
   }
   ```

### Environment Configuration with Claude Code
Playwright supports environment variable expansion in Claude Code MCP configurations:

```bash
# Set Playwright environment variables
export PLAYWRIGHT_HEADLESS=false  # Run browsers in headed mode
export PLAYWRIGHT_BROWSER=chromium  # Default browser (chromium, firefox, webkit)
export PLAYWRIGHT_TIMEOUT=30000  # Default timeout in milliseconds
export PLAYWRIGHT_DOWNLOAD_PATH=/path/to/downloads
```

You can reference these in your MCP configuration:
```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-playwright"],
      "env": {
        "PLAYWRIGHT_HEADLESS": "${PLAYWRIGHT_HEADLESS}",
        "PLAYWRIGHT_BROWSER": "${PLAYWRIGHT_BROWSER}",
        "PLAYWRIGHT_TIMEOUT": "${PLAYWRIGHT_TIMEOUT}",
        "PLAYWRIGHT_DOWNLOAD_PATH": "${PLAYWRIGHT_DOWNLOAD_PATH}"
      }
    }
  }
}
```

## Authentication & Security

### Managing Authentication with Claude Code
Use Claude Code's `/mcp` command for Playwright management:
```bash
# Check Playwright server status
/mcp status playwright

# Restart Playwright server
/mcp restart playwright

# View Playwright logs for troubleshooting
/mcp logs playwright
```

### Security Considerations
**Important**: Playwright MCP provides powerful browser automation capabilities. Be aware of:
- **Browser Access**: Full control over Chromium, Firefox, and WebKit browsers
- **Web Interaction**: Can navigate to any website and interact with content
- **File System Access**: Can download files and take screenshots to local system
- **Network Monitoring**: Can intercept and monitor all network traffic
- **Third-party Risk**: Use Playwright MCP responsibly and review target websites' terms of service
- **Rate Limiting**: Be mindful of automated requests to prevent being blocked
- **Privacy Considerations**: Browser automation may expose user data and browsing patterns

### Resource Usage with @ Mentions
Reference Playwright MCP resources in Claude Code using `@` syntax:
- `@playwright` - Reference the Playwright server directly
- Execute browser automation as slash commands
- Build custom testing workflows with Playwright automation

## Verification & Testing

### Claude Code Integration Tests
1. **Server Status Check**:
   ```bash
   claude mcp list
   # Should show playwright as active
   ```

2. **Browser Operations Test**:
   ```bash
   # Test browser launch (use in Claude Code conversation)
   @playwright launch_browser chromium
   
   # Test navigation and screenshot
   @playwright navigate "https://example.com" --screenshot
   ```

3. **Claude Code Feature Test**:
   - Use `@playwright` mentions in conversations
   - Test browser automation through Claude Code interface
   - Verify screenshot and content extraction capabilities

### Playwright Service Verification
- Verify browsers are properly installed
- Test cross-browser compatibility (Chromium, Firefox, WebKit)
- Confirm mobile device simulation works

## Integration with Claude Code Testing Workflows

Playwright MCP enhances Claude Code's testing capabilities:

### Automated Testing Integration
Use Playwright with Claude Code for:
- **End-to-End Testing**: Create comprehensive test suites for web applications
- **Visual Testing**: Generate and compare screenshots for visual regression testing
- **Performance Testing**: Monitor web application performance and load times
- **Cross-Browser Testing**: Verify compatibility across different browsers and devices

### Testing Documentation
Playwright can automatically generate:
- Test documentation with screenshots
- Step-by-step testing guides
- Bug reports with visual evidence
- Performance analysis reports

## Verification Features
Once configured, you should have access to:
- **Browser Automation**: Control Chromium, Firefox, and WebKit browsers
- **Web Scraping**: Extract content from web pages with advanced selectors
- **Screenshot Capture**: Take full-page or element-specific screenshots
- **Form Interaction**: Fill forms, click buttons, and navigate complex workflows
- **Network Monitoring**: Monitor and intercept network requests and responses
- **Mobile Testing**: Simulate mobile devices and responsive designs
- **Claude Code Integration**: Seamless browser automation within conversations

## Usage Examples with Claude Code
The Playwright MCP enables:
- **Automated Web Testing**: Create and execute comprehensive test suites through Claude Code conversations
- **Data Extraction**: Extract content from dynamic websites with intelligent selectors
- **Screenshot Generation**: Capture full-page or element-specific screenshots for documentation
- **Form Automation**: Automate complex form filling and submission workflows
- **Cross-Browser Testing**: Verify compatibility across Chromium, Firefox, and WebKit
- **Mobile Responsiveness Testing**: Test applications on various mobile device simulations
- **Performance Monitoring**: Analyze page load times, network requests, and resource usage

### Example Claude Code Workflows:
```bash
# Test a web application with screenshots
"@playwright navigate to https://myapp.com, fill the login form, and take a screenshot of the dashboard"

# Extract data from a dynamic website
"@playwright scrape product information from the e-commerce site and return structured data"

# Cross-browser compatibility testing
"@playwright test the checkout process on Chromium, Firefox, and WebKit browsers"

# Mobile responsiveness testing
"@playwright simulate iPhone 13 and test the mobile navigation menu"
```

## Troubleshooting

### Common Issues
1. **Playwright Server Won't Start**:
   ```bash
   # Check Playwright installation
   npm list -g @modelcontextprotocol/server-playwright
   
   # Verify browsers are installed
   npx playwright install --dry-run
   ```

2. **Claude Code Can't Connect**:
   ```bash
   # Verify server configuration
   claude mcp list
   
   # Check Playwright logs
   claude mcp logs playwright --tail 20
   ```

3. **Browser Launch Issues**:
   ```bash
   # Test Playwright directly
   npx playwright test --list
   
   # Check browser installations
   npx playwright install chromium firefox webkit
   ```

4. **Environment Variable Issues**:
   ```bash
   # Debug environment variable expansion
   claude mcp restart playwright --debug
   
   # Verify all required variables are set
   env | grep PLAYWRIGHT
   ```

### Browser-Specific Issues
1. **Chromium Issues**:
   ```bash
   # Test Chromium specifically
   npx playwright test --browser=chromium
   
   # Check Chromium installation
   npx playwright install chromium --force
   ```

2. **Firefox Issues**:
   ```bash
   # Test Firefox specifically
   npx playwright test --browser=firefox
   
   # Check Firefox dependencies
   npx playwright install-deps firefox
   ```

3. **WebKit Issues**:
   ```bash
   # Test WebKit specifically (macOS/Linux only)
   npx playwright test --browser=webkit
   
   # Install WebKit dependencies
   npx playwright install-deps webkit
   ```

### Performance and Timeout Issues
1. **Slow Page Loads**:
   ```bash
   # Increase timeout values
   export PLAYWRIGHT_TIMEOUT=60000
   claude mcp restart playwright
   ```

2. **Network Issues**:
   ```bash
   # Test network connectivity
   npx playwright test --trace on
   
   # Check proxy settings
   export HTTP_PROXY=http://proxy.company.com:8080
   ```

### Log Analysis
Monitor Playwright MCP activity:
```bash
# View recent Playwright logs
claude mcp logs playwright --tail 50

# Monitor live browser automation
claude mcp logs playwright --follow

# Debug specific browser issues
claude mcp logs playwright --level debug --filter chromium
```

## Security Best Practices
When using Playwright MCP, ensure:
- **Rate Limiting**: Respect website rate limits and use delays between requests
- **Terms of Service**: Review and comply with target websites' terms of service
- **Data Privacy**: Be cautious when extracting and storing personal or sensitive data
- **Authentication**: Secure any credentials used for automated login processes
- **Network Security**: Use HTTPS where possible and validate SSL certificates
- **Local Security**: Secure downloaded files and screenshots appropriately

Your Claude Code client can now leverage powerful browser automation capabilities for comprehensive web testing and interaction workflows.