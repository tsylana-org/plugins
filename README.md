# Tsylana Plugins

Public Agent Plugins and Codex marketplace metadata for Tsylana.

## Overview

This repository distributes public Tsylana plugins. The current
[`tsylana`](plugins/tsylana/README.md) plugin connects compatible agents to
Tsylana's hosted, read-only MCP server using client-managed OAuth.

## Structure

- [`plugins/`](plugins/): public plugin bundles:
  - [`tsylana/`](plugins/tsylana/): hosted Tsylana MCP integration
- [`ARCHITECTURE.md`](ARCHITECTURE.md): distribution, runtime, and security
  boundaries
- [`AGENTS.md`](AGENTS.md): repository operating contract

## Getting Started

After this repository is published, add the marketplace and install the plugin:

```sh
codex plugin marketplace add \
  https://github.com/tsylana-org/plugins.git --ref main
codex plugin add tsylana@tsylana
```

The first connection opens the Tsylana OAuth flow. The MCP resource and
authorization server are separate: `mcp.tsylana.com` serves MCP requests and
advertises the authorization server hosted at `auth.tsylana.com`.

## Releases

Release Please opens or updates a release PR for releasable changes on `main`. A
maintainer reviews and merges that PR; the next release run creates the `vX.Y.Z`
tag and GitHub Release. One version covers both plugin manifests.

[`release-please-config.json`](release-please-config.json) owns the version-file
mappings. Ordinary changes do not manually bump versions. This follows the same
release process as
[Plugins Private](https://github.com/tsylana-org/plugins-private).

The workflow uses `GITHUB_TOKEN` and requires Actions permission to create PRs.
That token does not trigger follow-on workflows for bot-created release PRs.
Before merging one, manually run the `build` workflow against its branch and
complete the plugin metadata checks.

## Contributing

Please read the [CONTRIBUTING](CONTRIBUTING.md) guide for workflow and
contribution expectations.

## License

This project is licensed under the terms of the [LICENSE](LICENSE).
