# Metabase Cursor Plugin

<img src="./docs/logo.png" alt="Metabase" width="200"></img>

The official Cursor MCP Plugin for [Metabase](https://www.metabase.com/). Developed and maintained by the Metabase Team.

## What’s included

- Skill: `setup-metabase-mcp` (`plugins/metabase/skills/setup-metabase-mcp/SKILL.md`)
- MCP server config: `plugins/metabase/mcp.json`

Current scope: **skills + MCP config only** (no rules, agents, commands, or hooks yet).

## Connecting to your Metabase

After installing the plugin, just ask the AI to set up your Metabase MCP server:

Just type: "Set up my Metabase MCP"

The `setup-metabase-mcp` skill will guide you through the rest. The AI will:

- Ask for your Metabase URL.
- Verify that your Metabase is version 60 or higher.
- Update your plugin's config with your Metabase's URL.

You'll need a valid login to your Metabase.

## How to test the Metabase plugin locally

1. Clone this repo.

2. Copy the `plugins/metabase` directory to you local Cursor plugins directory.

```sh
cp --recursive /path/to/metabase-cursor-plugin/plugins/metabase ~/.cursor/plugins/local/metabase
```

Note the `--recursive` flag; you need to copy directory and its sub-directories because Cursor won't resolve symlinks when loading local plugins.

3. With the plugin installed, ask the AI to "Set up my Metabase MCP".

The `setup-metabase-mcp` skill will guide you through configuring your `mcp.json` at ~/.cursor/plugins/local/metabase/mcp.json`.

4. Once your `mcp.json` is configured, reload Cursor, and you should be good to go.

## Attribution

The `setup-metabase-mcp` skill is adapted from the [Datadog MCP Setup](https://github.com/datadog-labs/cursor-plugin/blob/main/skills/datadog-mcp-setup/SKILL.md).
