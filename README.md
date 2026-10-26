<p align="center"><img src="assets/icon.png" width="96" alt="Hoplix"></p>

# Hoplix Print on Demand — MCP server

**Print-on-demand from your AI assistant.** Browse products and base costs, create campaigns with your own designs, quote and place orders that [Hoplix](https://hoplix.com) prints and ships worldwide, and track them — from Claude, ChatGPT or any MCP client.

- **Server URL:** `https://api.hoplix.com/mcp` (remote, Streamable HTTP)
- **Authentication:** OAuth 2.1 with dynamic client registration — you sign in with your Hoplix account, the assistant never sees your password
- **Documentation:** https://hoplix.com/en/mcp-integration
- **Official MCP Registry:** `com.hoplix/print-on-demand`
- **Claude Connectors Directory:** [Hoplix Print on Demand](https://claude.ai/directory/hoplix-print-on-demand)

You only need a free Hoplix seller account: [hoplix.com](https://hoplix.com). There is nothing to install or host: this repository contains documentation and configuration only, the server is operated by Hoplix SRL.

## What you can do

- Browse the print-on-demand catalogue — t-shirts, hoodies, mugs, bags and more — with colours, sizes, base costs and production times.
- Create campaigns with your design, public with their own page or private for your own orders. The image is uploaded through a personal Hoplix link, so no public URL is needed.
- Get a quote with total and shipping cost before ordering.
- Place orders with your own unique reference, or **test orders** that are checked and priced but never produced.
- Follow orders with status, shipping code and tracking link, and cancel orders that are not in production yet.

**Nothing is charged from the chat.** Orders are created unpaid and go into production only after you pay them from the Orders page of your Hoplix account (the payment link is also sent by email). The assistant asks for your confirmation before creating campaigns or orders.

## Connect

### Claude (claude.ai, Desktop, mobile)
Add **Hoplix Print on Demand** from the [Connectors Directory](https://claude.ai/directory/hoplix-print-on-demand), or go to *Settings → Connectors → Add custom connector* and paste `https://api.hoplix.com/mcp`.

### Claude Code
```bash
claude mcp add --transport http hoplix https://api.hoplix.com/mcp
```
Then run `/mcp` inside Claude Code and sign in to Hoplix.

Or install it as a plugin from this repository:
```bash
claude plugin marketplace add hoplix/hoplix-print-on-demand-mcp
claude plugin install hoplix@hoplix-print-on-demand-mcp
```

### ChatGPT
Coming soon in the ChatGPT apps directory. Meanwhile, with developer mode enabled, add a connector with the URL `https://api.hoplix.com/mcp` and OAuth.

### Cursor, VS Code, Windsurf and other MCP clients
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
The client opens the Hoplix sign-in page the first time it connects.

## Tools

| Tool | Type | What it does |
|---|---|---|
| `list_products` | read | Search the catalogue |
| `get_product` | read | Colours, sizes, print areas, base cost and production time of a product |
| `list_campaigns` | read | Your campaigns |
| `get_campaign` | read | Details of a campaign |
| `list_orders` | read | Your orders, test orders included |
| `get_order` | read | Details of an order |
| `get_order_status` | read | Status, shipping code and tracking link |
| `check_shipping_address` | read | Validate a shipping address |
| `quote_order` | read | Total and shipping cost, without saving anything |
| `get_design_upload` | read | Status of a design upload |
| `request_design_upload` | write | Personal link (valid 30 minutes) to upload a PNG/JPG design up to 15 MB |
| `create_campaign` | write | Create a campaign with your design |
| `create_order` | write | Create an unpaid order (or a test order) with your own reference |
| `cancel_order` | destructive | Cancel an order that is not in production yet |

## Example prompts

- *Which hoodies can I print on with Hoplix and how much do they cost?*
- *Create a private campaign with my logo on a black t-shirt.*
- *How much does it cost to ship 2 t-shirts from my campaign to Naples, Italy?*
- *Where is my order REF-1042?*

## Privacy and support

- Privacy policy for the MCP integration: https://hoplix.com/en/mcp-privacy
- Disconnect at any time from *Account → Integrations → MCP Integration* on hoplix.com
- Support: support@hoplix.com

## About Hoplix

[Hoplix](https://hoplix.com) is a print-on-demand platform based in Italy: sellers put their designs on t-shirts, hoodies, mugs, bags and many other products, and Hoplix prints and ships every order worldwide, with no minimum quantity. Also available as a REST API: https://hoplix.com/api/v1/documentation

© Hoplix SRL. Documentation released under the MIT License.
