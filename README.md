# Ana plugin for Claude Code

Ask Ana natural-language questions about your organization's data from inside
Claude Code. The plugin registers your org's Ana server as a remote MCP server
over OAuth, so every query is scoped to your organization automatically.

## What you get

- The `ana` MCP tool: ask Ana anything about your connected data sources.
- Convenience slash commands for common workflows:
  - `/ana:kpi-breakdown <metric> by <dimension> [over <period>]`
  - `/ana:period-compare <metric> <period A> vs <period B>`
  - `/ana:anomaly-check <metric> [over <window>]`
  - `/ana:explore-source <connector name>`

## Install

```
/plugin marketplace add TextQLLabs/ana-claude-plugin
/plugin install ana@textql
```

Then authenticate: run `/mcp`, select `ana`, and a browser window opens for you
to sign in through your organization's identity provider. Claude Code stores the
token (and auto-refreshes it). No client ID or secret to configure.

That's it. The plugin defaults to TextQL Cloud (`https://app.textql.com/mcp`), so
cloud users need no further setup.

## Self-hosted / non-cloud deployments

If your org runs its own TextQL deployment (or uses a region other than the
default cloud), point the plugin at your own host by setting `ANA_MCP_URL` in the
environment **before** launching Claude Code:

```bash
export ANA_MCP_URL="https://your-textql-host/mcp"
claude
```

Your MCP endpoint is your TextQL web host with `/mcp` appended, the same host
you open the TextQL app at. Cloud users can ignore this.

## Org-wide rollout (admins)

To enable Ana for everyone without each user installing it, push a
managed-settings.json via your MDM that pre-registers the marketplace and enables
the plugin:

```json
{
  "extraKnownMarketplaces": {
    "textql": {
      "source": { "source": "github", "repo": "TextQLLabs/ana-claude-plugin" }
    }
  },
  "enabledPlugins": { "ana@textql": true }
}
```

For self-hosted deployments, also set `ANA_MCP_URL` for your users (via the same
MDM profile or shell environment).

## Notes

- Access is org-scoped: the OAuth token carries your org and member identity, so
  you only ever see your own organization's data.
- The `ana` tool respects the same connector access controls as the Ana web app,
  so you can only query sources you have permission to use.
