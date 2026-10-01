# Forkmate — free AI calorie tracker MCP server (Claude, ChatGPT, Cursor)

[![Add to Cursor](https://img.shields.io/badge/Add_to-Cursor-000000?logo=cursor)](https://cursor.com/en/install-mcp?name=forkmate&config=eyJ1cmwiOiJodHRwczovL21jcC5mb3JrbWF0ZS5haS8ifQ==)
[![Install in VS Code](https://img.shields.io/badge/Install_in-VS_Code-0098FF?logo=visualstudiocode)](https://vscode.dev/redirect/mcp/install?name=forkmate&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.forkmate.ai%2F%22%7D)
[![MCP Registry](https://img.shields.io/badge/MCP_Registry-ai.forkmate%2Fforkmate-2ea44f)](https://registry.modelcontextprotocol.io/v0.1/servers?search=ai.forkmate/forkmate)
[![Glama](https://glama.ai/mcp/connectors/ai.forkmate/forkmate/badges/score.svg)](https://glama.ai/mcp/connectors/ai.forkmate/forkmate)

**Forkmate** ([forkmate.ai](https://forkmate.ai)) is a free AI calorie and macro tracker you talk
to. Tell your AI assistant what you ate, and it logs the meal with its calories, protein, carbs and
fat to your private food diary. See the day in the web diary at
[app.forkmate.ai](https://app.forkmate.ai).

It is a hosted, remote [MCP](https://modelcontextprotocol.io) server. There is nothing to install
or run: add one URL to your client and sign in.

| | |
|---|---|
| **Server URL** | `https://mcp.forkmate.ai/` |
| **Transport** | Streamable HTTP |
| **Auth** | OAuth 2.1 with PKCE and dynamic client registration. Your client opens the sign-in when it first calls a tool |
| **Price** | Free. No paid tier, no trial, no card, no ads |
| **Registry name** | `ai.forkmate/forkmate` ([`server.json`](server.json)) |
| **Setup guide** | [forkmate.ai/connect](https://forkmate.ai/connect/) |

## Connect your AI

### Claude (claude.ai and Claude Desktop)

Settings → Connectors → **Add custom connector** → paste `https://mcp.forkmate.ai/` → sign in.

### Claude Code

```sh
claude mcp add --transport http forkmate https://mcp.forkmate.ai/
```

### ChatGPT

On a plan that offers developer mode, turn it on in ChatGPT's settings, create a developer-mode app with the
URL `https://mcp.forkmate.ai/`, choose OAuth, and sign in.

### Cursor

Click **Add to Cursor** above, or add this to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "forkmate": { "url": "https://mcp.forkmate.ai/" }
  }
}
```

### VS Code (GitHub Copilot)

Click **Install in VS Code** above, or add this to `.vscode/mcp.json`:

```json
{
  "servers": {
    "forkmate": { "type": "http", "url": "https://mcp.forkmate.ai/" }
  }
}
```

### Windsurf

Add this to `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "forkmate": { "serverUrl": "https://mcp.forkmate.ai/" }
  }
}
```

### Cline

MCP Servers → Remote Servers → name `forkmate`, URL `https://mcp.forkmate.ai/`, transport
Streamable HTTP. AI agents installing it can follow [`llms-install.md`](llms-install.md).

### Gemini CLI

Add this to `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "forkmate": { "httpUrl": "https://mcp.forkmate.ai/" }
  }
}
```

### Any other MCP client

Add a remote HTTP MCP server with the URL `https://mcp.forkmate.ai/` and complete the sign-in.

Then tell your assistant what you ate ("two eggs and toast for breakfast"), or ask "how many
calories today?".

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

## Prompts

`log-meal` · `log-photo` · `today-so-far` · `hit-protein` · `week-review` · `import-myfitnesspal`

Your client shows these as ready-made starting points.

## Coming from MyFitnessPal?

Export your MyFitnessPal data for free and bring your history across:
[forkmate.ai/migrate-from-myfitnesspal](https://forkmate.ai/migrate-from-myfitnesspal/).

## Privacy

Every call is scoped to your own signed-in account. Forkmate stores your food diary, which is
health-related data. Read the [privacy policy](https://forkmate.ai/privacy/) and the
[consumer health data policy](https://forkmate.ai/health-data-privacy/). Export and account
deletion are self-serve in the app.

Calorie and macro values are estimates. They are not suitable for insulin dosing or any other
medical decision.

## About this repository

This repository holds the public server manifest and setup instructions. The server itself is
hosted at `mcp.forkmate.ai`; its source is not public.

Made by Shawn Azar. Support: [hello@forkmate.ai](mailto:hello@forkmate.ai).
