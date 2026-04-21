# AI-PDLC Marketplace

Plugin catalog for Claude Code and Cowork. This repo is the **discovery layer** — it indexes plugins so users can browse and install them. Each plugin lives in its own repo.

## Available Plugins

| Plugin | Category | Version | Description |
|--------|----------|---------|-------------|
| [incident-triage](https://github.com/fmlin0429712024/incident-triage-plugin) | operations | 0.2.0 | Triage production incidents — external (git submodule) |
| [incident-triage-internal](plugins/incident-triage-internal/) | operations | 0.2.0 | Triage production incidents — internal (marketplace-bundled) |

## How It Works

- **This repo** contains `marketplace.json` — a catalog pointing to plugin source repos
- **Plugin repos** contain the actual `.claude-plugin/plugin.json`, skills, agents, and MCP configs
- Users install plugins from their source repos, not from this catalog

## Adding a Plugin

Add an entry to `.claude-plugin/marketplace.json` under the `plugins` array:

```json
{
  "name": "your-plugin",
  "description": "What it does",
  "version": "0.1.0",
  "source": {
    "source": "github",
    "repo": "fmlin0429712024/your-plugin-repo"
  },
  "author": { "name": "Your Name" },
  "category": "category",
  "keywords": ["relevant", "keywords"]
}
```

## Architecture

```
marketplace.json (this repo)
  ├── external plugins (git submodules)
  │     └── external_plugins/incident-triage → github.com/fmlin0429712024/incident-triage-plugin
  └── internal plugins (committed directly)
        └── plugins/incident-triage-internal/
```

Follows the same pattern as Anthropic's [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) repo.
