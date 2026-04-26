<div align="center">

# 🔌 MCP Servers

**Model Context Protocol servers for the RooForge pipeline**

[![Servers: 2](https://img.shields.io/badge/servers-2-blue)](.)
[![Protocol: MCP](https://img.shields.io/badge/protocol-MCP-green)](https://modelcontextprotocol.io)

*Extend mode capabilities · Structured tool access · One doc per server*

</div>

---

## Overview

MCP servers extend mode capabilities by exposing structured tools (search, git operations, file access) through the Model Context Protocol. This directory contains one document per MCP server — each covers setup, configuration, and usage within the orchestration pipeline.

## Servers

| Server | File | Required By | Purpose |
|--------|------|-------------|---------|
| SearXNG | [`searxng.md`](searxng.md) | Ask Mode | Privacy-respecting meta-search for web intelligence |
| Git MCP | [`git-mcp-server.md`](git-mcp-server.md) | Git Mode | Structured git operations via MCP |

## Quick Start

1. **SearXNG** — [`searxng.md`](searxng.md) — Set up privacy-first web search for Ask mode. No API keys required; self-hosted SearXNG instance + bunx runtime.
2. **Git MCP** — [`git-mcp-server.md`](git-mcp-server.md) — Configure structured git access for Git mode. Supports full version-control workflows via MCP tools.

<div align="center">

*[⬆ Back to README](../README.md)*

</div>
