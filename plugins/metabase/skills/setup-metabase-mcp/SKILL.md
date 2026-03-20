---
name: setup-metabase-mcp
description: Read these instructions before using Metabase MCP tools. Setup is needed to connect to Metabase instances via the built-in MCP server.
---

Read these mandatory configuration steps for using the Metabase MCP server before querying data, dashboards, questions, and related resources.

**Location**: The MCP configuration file resides at `../../mcp.json` relative to this document.

**Important Requirement**: The configuration contains a placeholder `{METABASE_INSTANCE_PLACEHOLDER}` that must be replaced with the user's Metabase instance URL before proceeding.

## Valid Instance URL Formats

- Local development: `http://localhost:3000`
- Metabase Cloud: `https://yourcompany.metabaseapp.com`
- Self-hosted: `https://metabase.yourcompany.com`

## Required Actions

1. Check `../../mcp.json` for the placeholder `{METABASE_INSTANCE_PLACEHOLDER}`

2. If the placeholder is already replaced with a real URL, proceed with Metabase MCP usage — no further setup needed

3. If the placeholder still exists, **stop all other exploration immediately** and ask the user for their Metabase instance URL. Do not search for tool schemas, read other files, or do anything else first.

   **Never mention `{METABASE_INSTANCE_PLACEHOLDER}` or any placeholder to the user**. Simply say the MCP needs their Metabase URL to connect. Ask only for the URL and wait for their response.

4. Once the user provides the URL, run **exactly this command and no other** — do not try alternative endpoints or approaches:

   ```bash
   curl -s <INSTANCE_URL>/api/session/properties | grep -o '"tag":"[^"]*"'
   ```

   This returns something like `"tag":"v1.60.0"`. Extract the major version number (e.g. `60` from `v1.60.0`). If it is below 60, tell the user they need to upgrade and stop — do not update `mcp.json`.

5. Replace the placeholder in `../../mcp.json` with the user's instance URL. Strip any trailing slash before saving — do not mention this to the user.

6. Only after updating the file, tell the user they need to reload the window.

   Use the user's current OS to show the right shortcut: open the Command Palette (⌘⇧P on Mac or Ctrl+Shift+P on Windows/Linux) and run **"Reload Window"**. Ask them to confirm once reloaded before continuing.

7. Proceed with using the Metabase MCP

**Important**: Do not attempt to access MCP tools or schemas until the instance URL is properly configured and the window has been reloaded. Never reveal `{METABASE_INSTANCE_PLACEHOLDER}` or any internal placeholder names to the user.
