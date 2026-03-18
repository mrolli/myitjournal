# AI and AI tools

## Copilot (CLI)

### Add Atlassian Rovo MCP Server to Copilot CLI

To add the Atlassian Rovo MCP server to Copilot CLI, connect using the
mcp-remote proxy as follows:

1. Open your terminal.
1. Run: npx -y mcp-remote@latest <https://mcp.atlassian.com/v1/mcp>
1. Configure your client's settings with this format:  

```json
"mcp.servers": {
  "atlassian-mcp-server": {
     "command": "npx",
     "args": ["-y", "mcp-remote@latest", "https://mcp.atlassian.com/v1/mcp"]
  }
}

```

1. Authenticate when prompted and leave your terminal session open.
1. Follow your client’s documentation to trigger or test an MCP action.

Source:  <https://support.atlassian.com/atlassian-rovo-mcp-server/docs/setting-up-ides/>
