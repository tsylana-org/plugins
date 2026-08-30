# Tsylana Plugin Agents

## Overview

This plugin owns public metadata and assets for the hosted Tsylana MCP server.
It contains no local runtime or skills.

## Structure

- [`plugin.json`](plugin.json): Agent Plugins v1 identity metadata
- [`mcp.json`](mcp.json): portable Streamable HTTP registration
- [`.codex-plugin/`](.codex-plugin/): Codex presentation metadata
- [`.mcp.json`](.mcp.json): Codex HTTP and OAuth resource registration
- [`assets/`](assets/): public plugin branding
- [`README.md`](README.md): human-facing plugin overview and installation guidance

## Tech Stack

- **Plugin formats**: Agent Plugins v1 and Codex compatibility metadata
- **Protocol**: Model Context Protocol over Streamable HTTP
- **Authentication**: OAuth

## Commands

- JSON: `jq empty plugin.json mcp.json .codex-plugin/plugin.json .mcp.json`
- Identity: `jq -e '.name == "tsylana" and .version == "0.0.0"' plugin.json`
- Portable MCP: `jq -e '.mcpServers.tsylana.type == "streamable-http" and .mcpServers.tsylana.url == "https://mcp.tsylana.com/mcp"' mcp.json`
- Codex OAuth resource: `jq -e '.mcpServers.tsylana.oauth_resource == "https://mcp.tsylana.com/mcp"' .mcp.json`

## Verification

- Run every metadata check and confirm referenced assets exist.
- Validate portable and Codex metadata independently.

## Guardrails

- Keep the plugin public, read-only, and remote-only.
- Keep `mcp.tsylana.com` as the protected resource; discover authorization at `auth.tsylana.com` through MCP OAuth metadata.
- Never add tokens, client secrets, private skills, customer data, or hosted connector source.
