# Tsylana Plugins

Public Agent Plugins and Codex marketplace metadata for Tsylana.

## Overview

This repository distributes public Tsylana plugins. The current
[`tsylana`](plugins/tsylana/README.md) plugin connects compatible agents to
Tsylana's hosted, read-only MCP server using client-managed OAuth.

## Structure

- [`plugins/`](plugins/): public plugin bundles:
  - [`tsylana/`](plugins/tsylana/): hosted Tsylana MCP integration
- [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json): public
  plugin catalog
- [`.github/workflows/`](.github/workflows/): repository checks and release
  automation
- [`ARCHITECTURE.md`](ARCHITECTURE.md): distribution, runtime, and security
  boundaries
- [`AGENTS.md`](AGENTS.md): repository operating contract

## Getting Started

### Prerequisites

Use a Codex CLI installation with plugin support.

### How to Use

After this repository is published, add the marketplace and install the plugin:

```sh
codex plugin marketplace add \
  https://github.com/tsylana-org/plugins.git --ref main
codex plugin add tsylana@tsylana
```

The first connection opens the Tsylana OAuth flow. The MCP resource and
authorization server are separate: `mcp.tsylana.com` serves MCP requests and
advertises the authorization server hosted at `auth.tsylana.com`.

## Contributing

Please read the [CONTRIBUTING](CONTRIBUTING.md) guide for details on how to
contribute. Pull requests, bug reports, and feature requests are welcome!

## License

This project is licensed under the terms of the [LICENSE](LICENSE).
