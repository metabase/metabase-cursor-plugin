# Metabase Cursor Plugin

Connect Cursor to your Metabase instance via MCP.

## What’s included

- Skill: `setup-metabase-mcp` (`plugins/metabase/skills/setup-metabase-mcp/SKILL.md`)
- MCP server config: `plugins/metabase/mcp.json`

Current scope: **skills + MCP config only** (no rules, agents, commands, or hooks yet).

## Configure your Metabase instance

1. Open `plugins/metabase/mcp.json`.
2. Replace `{METABASE_INSTANCE_PLACEHOLDER}` with your Metabase base URL (no trailing slash), for example:
   - Local development: `http://localhost:3000`
   - Metabase Cloud: `https://yourcompany.metabaseapp.com`
   - Self-hosted: `https://metabase.yourcompany.com`
3. Ensure your instance supports Cursor’s built-in Metabase MCP server (requires Metabase v1.60+). The `setup-metabase-mcp` skill includes a version check.
4. Reload Cursor (Command Palette -> `Reload Window`).

## How to test locally

Symlink the `plugins/metabase` folder into your local Cursor plugins directory:

```sh
ln -s ./plugins/metabase ~/.cursor/plugins/local/metabase
```

Then configure `plugins/metabase/mcp.json` as described above and reload Cursor.

## Development / validation

If you’re iterating on this repo, you can run:

```sh
node scripts/validate-template.mjs
```

## Attribution

The `setup-metabase-mcp` skill is adapted from the [Datadog MCP Setup](https://github.com/datadog-labs/cursor-plugin/blob/main/skills/datadog-mcp-setup/SKILL.md).
