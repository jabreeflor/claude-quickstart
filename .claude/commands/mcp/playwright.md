# Playwright MCP Setup

You are a helpful assistant that will guide the user through setting up the Playwright MCP server.

## Overview
Playwright MCP provides browser automation capabilities for web scraping, testing, and interaction with web applications.

## Installation Steps

### Step 1: Install Playwright MCP
```bash
npm install -g @modelcontextprotocol/server-playwright
```

### Step 2: Install Playwright Browsers
```bash
npx playwright install
```

### Step 3: MCP Configuration
Add this configuration to your MCP client settings:

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

### Alternative: Direct Node Execution
If you prefer direct node execution, first find the installation path:
```bash
npm list -g @modelcontextprotocol/server-playwright
```

Then use this configuration with the actual path:
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

### Environment Configuration (Optional)
You can configure Playwright behavior with environment variables:
```bash
export PLAYWRIGHT_HEADLESS=false  # Run browsers in headed mode
export PLAYWRIGHT_BROWSER=chromium  # Default browser (chromium, firefox, webkit)
export PLAYWRIGHT_TIMEOUT=30000  # Default timeout in milliseconds
```

## Verification
Once configured, you should have access to:
- **Browser Automation**: Control Chromium, Firefox, and WebKit browsers
- **Web Scraping**: Extract content from web pages
- **Screenshot Capture**: Take screenshots of pages or elements
- **Form Interaction**: Fill forms, click buttons, navigate pages
- **Network Monitoring**: Monitor network requests and responses
- **Mobile Testing**: Simulate mobile devices

## Usage Examples
The Playwright MCP enables:
- Automated web testing and validation
- Data extraction from dynamic websites
- Screenshot generation for documentation
- Form automation and submission
- Cross-browser compatibility testing
- Mobile responsiveness testing
- Performance monitoring and analysis

## Security Note
Playwright has access to browse the web and interact with websites. Use responsibly and be aware of:
- Rate limiting on target websites
- Terms of service compliance
- Privacy considerations when scraping data
- Security implications of automated browser actions

Your MCP client can now leverage powerful browser automation capabilities for web-related tasks.