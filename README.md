# Synta MCP Codex Plugin

This plugin bundles the Synta MCP for Codex, which enables Codex to build, validate, & debug n8n workflows with deep knowledge of the platform's complete node library, allowing smart workflow-creation real-time error checking & expert troubleshooting assistance.

## What This Plugin Includes

- `SKILL.MD`: reusable instructions for building and repairing n8n workflows with Synta MCP
- `.mcp.json`: MCP server definition for `https://mcp.synta.io/mcp`
- `.codex-plugin/plugin.json`: Codex plugin manifest

## Install In Codex

Codex plugins are installed from the plugin directory in the app or CLI. In the CLI, open the plugin list with:

```bash
codex
/plugins
```

For this local plugin, use the local plugin layout described by the Codex plugin manifest and marketplace conventions.

### Option 1: Home-Local Install

Recommended when you want this plugin available across projects on your machine.

1. Create the local plugins folders if they do not exist:

```bash
mkdir -p ~/.agents/plugins ~/.codex/plugins
```

2. Copy this plugin into your local plugins directory so the folder name matches the manifest name:

```bash
cp -R /path/to/codex/plugin/n8n-mcp-codex-plugin-synta ~/.codex/plugins/n8n-mcp-codex-plugin-synta
```

3. Create or update `~/.agents/plugins/marketplace.json` with an entry for this plugin:

```json
{
  "name": "local-plugins",
  "interface": {
    "displayName": "Local Plugins"
  },
  "plugins": [
    {
      "name": "n8n-mcp-synta-codex",
      "source": {
        "source": "local",
        "path": "./plugins/n8n-mcp-codex-plugin-synta"
      },
      "policy": {
        "installation": "AVAILABLE",
        "authentication": "ON_INSTALL"
      },
      "category": "Productivity"
    }
  ]
}
```

4. Restart Codex.

5. Open the plugin directory with `/plugins`, find `Synta MCP`, and install it.

### Option 2: Repo-Local Install

Useful if you want to keep the plugin alongside a specific repo instead of your home directory.

1. Place the plugin at:

```text
<repo-root>/plugins/n8n-mcp-codex-plugin-synta
```

2. Create or update:

```text
<repo-root>/.agents/plugins/marketplace.json
```

3. Add the same plugin entry as above, keeping the source path as:

```json
"path": "./plugins/n8n-mcp-codex-plugin-synta"
```

4. Restart Codex, then install it from `/plugins`.

## Use The Plugin

After installation, start a new Codex thread and either:

- Describe the outcome you want, for example: `Build an n8n workflow that syncs Typeform submissions to HubSpot`
- Invoke the plugin or skill explicitly with `@`

Example prompts:

- `Use Synta MCP to create an n8n workflow that watches Gmail and posts new support emails to Slack`
- `@synta-n8n-assistant fix the expression errors in this n8n workflow`

## Disable Or Uninstall

To disable the plugin without uninstalling it, set it to disabled in `~/.codex/config.toml` and restart Codex:

```toml
[plugins."n8n-mcp-codex-plugin-synta"]
enabled = false
```

To remove it completely, uninstall it from the Codex plugin browser.
