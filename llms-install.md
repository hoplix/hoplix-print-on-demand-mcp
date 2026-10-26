# Installing the Hoplix MCP server

This is a **remote** MCP server: there is nothing to download, build or run locally.

1. Add a remote MCP server with transport **Streamable HTTP** and URL `https://api.hoplix.com/mcp`.
2. Authentication is **OAuth 2.1 with dynamic client registration**. Do not ask the user for an API key: the client opens the Hoplix sign-in page, the user logs in with their Hoplix account and approves the connection.
3. The user needs a free Hoplix seller account (https://hoplix.com). If they do not have one, they can create it from the sign-in page.

Example configuration:

```json
{
  "mcpServers": {
    "hoplix": {
      "type": "http",
      "url": "https://api.hoplix.com/mcp"
    }
  }
}
```

After connecting, test with a read-only request such as "List Hoplix t-shirts with their base cost".
Orders created through the server stay unpaid until the user pays them on hoplix.com; `create_order` with `"test": true` creates a test order that is never produced.

Documentation: https://hoplix.com/en/mcp-integration
