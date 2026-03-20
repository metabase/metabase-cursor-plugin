---
name: setup-metabase-mcp
description: Read these instructions before using Metabase MCP tools. Setup is needed to connect to Metabase instances via the built-in MCP server.
---

Read these mandatory configuration steps for using the Metabase MCP server before querying data, dashboards, questions, and related resources.

## Key Configuration Steps

**Location**: The MCP configuration file resides at `../../mcp.json` relative to this document.

**Important Requirement**: The configuration contains a placeholder `{METABASE_INSTANCE_PLACEHOLDER}` that must be replaced with the user's Metabase instance URL before proceeding.

## Valid Instance URL Formats

- Local development: `http://localhost:3000`
- Metabase Cloud: `https://yourcompany.metabaseapp.com`
- Self-hosted: `https://metabase.yourcompany.com`

## Required Actions

1. Check `../../mcp.json` for the placeholder `{METABASE_INSTANCE_PLACEHOLDER}`
2. If the placeholder is already replaced with a real URL, proceed with Metabase MCP usage — no further setup needed
3. If the placeholder still exists, ask the user for their Metabase instance URL (do not mention the placeholder — just tell them the MCP needs their Metabase URL to connect)
4. Verify the instance supports the built-in MCP server (requires Metabase 60+):
   ```bash
   curl -s <INSTANCE_URL>/api/session/properties | grep -o '"tag":"[^"]*"'
   ```
   If the major version is below 60, inform the user they need to upgrade and do not update `mcp.json`
5. Replace the placeholder in `../../mcp.json` with the user's instance URL (no trailing slash)
6. Instruct the user to reload their window via Command Palette (⌘⇧P on Mac; Ctrl+Shift+P on Windows/Linux)

**Important**: Do not attempt to access MCP tools or schemas until the instance URL is properly configured.
