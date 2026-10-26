# Agents

## Overview

This repository is Tsylana's public plugin marketplace. Keep repository work
limited to public distribution metadata, documentation, assets, and explicitly
public plugin code.

## Structure

- [`plugins/`](plugins/): public plugin bundles:
  - [`tsylana/`](plugins/tsylana/): hosted Tsylana MCP integration
- [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json): public
  plugin catalog
- [`ARCHITECTURE.md`](ARCHITECTURE.md): distribution, runtime, and security
  boundaries
- [`README.md`](README.md): human-facing repository overview
- [`CONTRIBUTING.md`](CONTRIBUTING.md): contribution, Git and style conventions

## Checks

Run `rumdl check .` from the repository root.

To format affected files, use `rumdl check --fix <paths>`, inspect the diff, and
rerun the check.

For metadata changes, verify catalog paths, matching manifest identities, and
the shared release version.

## Work Tracking

- **Project:**
  [Tsylana Apps & APIs](https://github.com/orgs/tsylana-org/projects/5)

## Guardrails

- Treat marketplace and plugin metadata as a public supply-chain surface.
- Never add credentials, tokens, private skills, customer data, or hosted
  service source.
- Keep `mcp.tsylana.com` as the protected MCP resource and discover
  authorization through its OAuth metadata.
- Let the [release workflow](.github/workflows/release.yml) manage versions
  through [release-please-config.json](release-please-config.json).
- Publishing to an external marketplace or directory requires explicit human
  approval.
