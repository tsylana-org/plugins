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
- [`README.md`](README.md): human-facing plugin overview and installation
  guidance

## Tech Stack

- **Plugin formats**: Agent Plugins v1 and Codex compatibility metadata
- **Protocol**: Model Context Protocol over Streamable HTTP
- **Authentication**: OAuth

## Checks

For connection changes, check both client registrations against the hosted
endpoint and OAuth resource.

## Guardrails

- Keep the plugin public, read-only, and remote-only.
- Keep `mcp.tsylana.com` as the protected resource; discover authorization at
  `auth.tsylana.com` through MCP OAuth metadata.
- Never add tokens, client secrets, private skills, customer data, or hosted
  connector source.
