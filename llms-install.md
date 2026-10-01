# Installing Forkmate (for AI agents)

Forkmate is a hosted remote MCP server. There is no package to install, no build step, and no API
key.

1. Add a remote MCP server named `forkmate` with the URL `https://mcp.forkmate.ai/` and the
   Streamable HTTP transport. For Cline, the entry in `cline_mcp_settings.json` is:

   ```json
   {
     "mcpServers": {
       "forkmate": {
         "type": "streamableHttp",
         "url": "https://mcp.forkmate.ai/"
       }
     }
   }
   ```

2. Connect. `initialize` and `tools/list` work without signing in.
3. The first tool call returns `401` with a `WWW-Authenticate` header pointing at
   `https://mcp.forkmate.ai/.well-known/oauth-protected-resource`. The client then runs OAuth 2.1
   with PKCE and dynamic client registration. The user signs in or creates a free account in their
   browser.
4. Before the first meal is saved, the user gives a one-time consent in the web app for Forkmate to
   process their health data. If `log_meal` replies with a consent link, pass it to the user.
5. Verify with `whoami`, which returns the connected account id.

No environment variables or secrets are needed.
