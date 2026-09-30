# Forkmate — food diary MCP server

Log what you ate by talking to your AI assistant. Forkmate is a free, hosted
[MCP](https://modelcontextprotocol.io) server that turns Claude, Cursor or any MCP client into a
private food diary: say "two eggs and toast" and it records the meal with its calories and
macros. See your day any time in the web diary at [app.forkmate.ai](https://app.forkmate.ai).

This repository holds the public server manifest and setup instructions. The server is
hosted; there is nothing to install or run.

| | |
|---|---|
| **Endpoint** | `https://mcp.forkmate.ai/` (streamable HTTP) |
| **Auth** | OAuth 2.1 with PKCE and dynamic client registration — sign in when your client asks |
| **Registry name** | `ai.forkmate/forkmate` ([`server.json`](server.json)) |
| **Price** | Free. No paid tier, no trial, no card |
| **Website** | [forkmate.ai](https://forkmate.ai) · [setup guide](https://forkmate.ai/connect/) |

## Connect

**Claude.ai / Claude Desktop** — Settings → Connectors → *Add custom connector* → paste
`https://mcp.forkmate.ai/` → sign in.

**Claude Code**

```sh
claude mcp add --transport http forkmate https://mcp.forkmate.ai/
```

**Cursor** — Settings → MCP → *Add new MCP server* → HTTP → paste the URL → sign in.

**Any other MCP client** — add a remote HTTP server with the URL above and complete the OAuth
sign-in.

Then just tell your assistant what you ate, or ask "how many calories today?".

## Tools

| Tool | What it does |
|---|---|
| `log_meal` | Log what you ate to your diary |
| `update_meal` | Correct an entry already in your diary |
| `delete_meal` | Remove an entry from your diary |
| `get_day` | Read one day's diary with calorie and macro totals |
| `get_range` | Read a date range with per-day totals |
| `get_preferences` | Read your dietary preferences |
| `search_foods` | Search USDA FoodData Central and Open Food Facts |
| `lookup_barcode` | Look up a packaged food by barcode (Open Food Facts) |
| `get_pantry` · `add_pantry_item` · `remove_pantry_item` | Keep a list of foods you have on hand |
| `whoami` | Confirm which account is connected |

Every call is scoped to your own signed-in account. Calorie and macro values are estimates and
are not suitable for insulin dosing or other medical decisions.

## Privacy

Forkmate stores your food diary, which is health-related data. Read the
[privacy policy](https://forkmate.ai/privacy/) and the
[consumer health data policy](https://forkmate.ai/health-data-privacy/). Export and account
deletion are self-serve in the app.

## Support

[hello@forkmate.ai](mailto:hello@forkmate.ai)
