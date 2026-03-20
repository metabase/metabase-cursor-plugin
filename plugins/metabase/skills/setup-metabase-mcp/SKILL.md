---
name: setup-metabase-mcp
description: Read these instructions before using Metabase MCP tools. Setup is needed to connect to Metabase instances via the built-in MCP server.
---

The configuration for the Metabase MCP lives at `../../mcp.json`. By default, the `url` field contains `{METABASE_INSTANCE_PLACEHOLDER}` which must be replaced with the user's actual Metabase instance URL.

## Setup

1. Read the `mcp.json` file at `../../mcp.json`, relative to this SKILL.md file.

2. Ask the user for their Metabase instance URL.

   Give these examples to help them identify it:
   - Local development: `http://localhost:3000`
   - Metabase Cloud: `https://yourcompany.metabaseapp.com`
   - Self-hosted: `https://metabase.yourcompany.com`

   If `{METABASE_INSTANCE_PLACEHOLDER}` is not in the file, skip the remaining steps and proceed with using the Metabase MCP.

   Do not read other files or inspect MCP tool schemas while `{METABASE_INSTANCE_PLACEHOLDER}` is still present. The MCP will not work until it is replaced.

3. Once the user provides their URL, check whether their Metabase instance supports the built-in MCP server (requires v1.60+):

   ```bash
   curl -s <METABASE_INSTANCE_URL>/api/session/properties | grep -o '"tag":"[^"]*"'
   ```

   If `jq` is available:

   ```bash
   curl -s <METABASE_INSTANCE_URL>/api/session/properties | jq .version.tag
   ```

   This endpoint requires no authentication. It returns a version tag like `v1.60.0` or `v0.58.3`. Extract the major version number (e.g. `60` from `v1.60.0`).

4. **If major version < 60:**

   Tell the user:

   > Your Metabase instance is running **Metabase XX**, which does not include the built-in MCP server. The built-in MCP server requires **Metabase 60 or later**. Please upgrade your Metabase instance and run this setup again.

   Do not update `mcp.json`.

5. **If major version >= 60:**

   Update `../../mcp.json` by replacing `{METABASE_INSTANCE_PLACEHOLDER}` with the user's instance URL (without a trailing slash).

6. Let the user know the file has been updated and ask them to reload Cursor by opening the Command Palette (⌘⇧P on Mac, Ctrl+Shift+P on Windows/Linux) and running **"Reload Window"**.
