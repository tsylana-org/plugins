# Agents

## Overview

This repository is Tsylana's public plugin marketplace. Keep repository work
limited to public distribution metadata, documentation, assets, and explicitly
public plugin code.

## Structure

- [`plugins/`](plugins/): public plugin bundles:
  - [`tsylana/`](plugins/tsylana/): hosted Tsylana MCP integration; follow its local `AGENTS.md`
- [`ARCHITECTURE.md`](ARCHITECTURE.md): distribution, runtime, and security boundaries
- [`README.md`](README.md): human-facing repository overview

## Commands

- Catalog: `jq empty .agents/plugins/marketplace.json`
- Plugin: `jq empty plugins/tsylana/plugin.json plugins/tsylana/mcp.json plugins/tsylana/.codex-plugin/plugin.json plugins/tsylana/.mcp.json`

## Verification

- Confirm catalog paths and plugin metadata references exist.
- Follow the plugin's local verification guidance.

## Guardrails

- Treat marketplace and plugin metadata as a public supply-chain surface.
- Never add credentials, tokens, private skills, customer data, or hosted service source.
- Keep `mcp.tsylana.com` as the protected MCP resource and discover authorization through its OAuth metadata.
- Publishing to an external marketplace or directory requires explicit human approval.
