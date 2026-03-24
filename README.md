# Metabase Cursor Plugin

The official Cursor MCP Plugin for [Metabase ](https://www.metabase.com/). Developed and maintained by the Metabase Team.

## What’s included

- Skill: `setup-metabase-mcp` (`plugins/metabase/skills/setup-metabase-mcp/SKILL.md`)
- MCP server config: `plugins/metabase/mcp.json`

Current scope: **skills + MCP config only** (no rules, agents, commands, or hooks yet).

## Connecting to your Metabase

After installing the plugin, just ask the AI to set up your Metabase MCP server:

> "Set up my Metabase MCP"

The `setup-metabase-mcp` skill will guide you through the rest — it will ask for your instance URL, verify the version, and update the config for you.

## How to test locally

Copy the `plugins/metabase` folder into your local Cursor plugins directory:

```sh
cp -R /path/to/metabase-cursor-plugin/plugins/metabase ~/.cursor/plugins/local/metabase
```

> **Note:** Symlinks do not work — Cursor does not resolve them when loading local plugins. Use `cp -R` instead.

Then configure `~/.cursor/plugins/local/metabase/mcp.json` as described above and reload Cursor.

## Development / validation

If you’re iterating on this repo, you can run:

```sh
node scripts/validate-template.mjs
```

## Attribution

The `setup-metabase-mcp` skill is adapted from the [Datadog MCP Setup](https://github.com/datadog-labs/cursor-plugin/blob/main/skills/datadog-mcp-setup/SKILL.md).
