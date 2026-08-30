# Tsylana

Public Agent Plugin for connecting compatible agents to Tsylana's hosted,
read-only MCP server.

## Overview

The plugin registers `https://mcp.tsylana.com/mcp` over Streamable HTTP with
OAuth authentication. It contains no local runtime, credentials, hosted
implementation, private skills, or customer data.

- **Type**: Remote MCP plugin
- **Runtime**: Compatible Agent Plugins v1 or Codex client

## Structure

- [`plugin.json`](plugin.json): Agent Plugins v1 identity metadata
- [`mcp.json`](mcp.json): portable Streamable HTTP registration
- [`.codex-plugin/`](.codex-plugin/): Codex presentation metadata
- [`.mcp.json`](.mcp.json): Codex HTTP and OAuth resource registration
- [`assets/`](assets/): public plugin branding
- [`AGENTS.md`](AGENTS.md): plugin operating contract

## Quickstart

- **Install with Codex**:

  ```sh
  codex plugin marketplace add https://github.com/tsylana-org/plugins.git
  codex plugin add tsylana@tsylana
  ```

On first connection, the MCP client discovers the authorization server from
the MCP protected-resource metadata and opens the Tsylana sign-in flow hosted
at `auth.tsylana.com`.
