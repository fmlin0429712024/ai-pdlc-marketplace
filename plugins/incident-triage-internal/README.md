# Incident Triage Plugin (Internal)

Triage production incidents using AI — classify severity, query historical context, and take post-triage actions.

This is the **internal marketplace** copy of the incident-triage plugin, registered directly in the marketplace repo (not as a git submodule).

## Install

```bash
claude plugin install <path-to-this-directory>
```

## Skills

| Skill | Command | Description |
|-------|---------|-------------|
| **triage-mp** | `/incident-triage-internal:triage-mp` | Classify and respond to any incident alert |

## Agent

| Agent | Launch | Description |
|-------|--------|-------------|
| **oncall** | `claude --agent incident-triage-internal:oncall` | On-call engineer persona for interactive triage |

## Integrations

| Pattern | Tool | Purpose |
|---------|------|---------|
| **CLI tool** | `gws` | Google Sheets — system inventory lookup (team, criticality, escalation) |
| **CLI tool** | `gh` | GitHub — create issues from triage cards |
| **MCP server** | `mcp-server-sqlite` | Incident database — query past incidents, create tickets, look up runbooks |

### Prerequisites

- `gws` CLI installed and authenticated (`gws auth login`)
- `gh` CLI installed and authenticated (`gh auth login`)
- `uvx` available for MCP server (`pip install uv`)

## Domains Covered

- **Security** — SIEM alerts, brute force, unauthorized access, credential compromise
- **Infrastructure** — Disk, CPU, memory, network, certificates
- **Application** — Error rates, latency, crashes, deployment failures
- **Data** — Replication lag, corruption, backup failures
