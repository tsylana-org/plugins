# Architecture

Tsylana Plugins is the public distribution boundary for agent-facing plugin
metadata. Hosted services remain in their owning repositories.

## 1. High-Level System Overview

```mermaid
flowchart LR
  catalog["Marketplace catalog"] --> plugin["Tsylana plugin metadata"]
  plugin --> client["Compatible MCP client"]
  client --> mcp["mcp.tsylana.com/mcp"]
  mcp --> auth["auth.tsylana.com"]
```

## 2. Core Components

### 2.1. Marketplace Catalog

- **Technology**: Codex marketplace metadata
- **Responsibility**: expose public repository-local plugin bundles
- **Key interactions**: resolves the Tsylana plugin and its presentation metadata

### 2.2. Tsylana Plugin

- **Technology**: Agent Plugins v1 and Codex compatibility metadata
- **Responsibility**: configure compatible clients for the hosted, read-only MCP server
- **Key interactions**: registers Streamable HTTP and client-managed OAuth without bundling a local runtime

### 2.3. Hosted Service Boundary

The hosted MCP, product behavior, account services, and infrastructure remain
in their owning repositories. This repository references those services and
does not copy their implementation.

## 3. Data Stores

This repository owns no runtime data store.

## 4. Technologies

- **Plugin formats**: Agent Plugins v1 and Codex plugin metadata
- **Protocol**: Model Context Protocol over Streamable HTTP
- **Authentication**: OAuth discovered from protected-resource metadata

## 5. Deployment & Infrastructure

The repository distributes metadata and assets only. Publishing to an external
marketplace or directory is a separate, explicitly approved operation.

## 6. Security Considerations

- Everything committed here must be safe for public distribution.
- `mcp.tsylana.com` is the protected resource; `auth.tsylana.com` is its authorization server.
- Tokens and client secrets must never be stored in plugin metadata.

## 7. Development & Testing Environment

Validate the marketplace catalog and portable and Codex metadata independently
with `jq`, then confirm every referenced path exists.

## 8. References

- [Tsylana plugin](plugins/tsylana/README.md)
