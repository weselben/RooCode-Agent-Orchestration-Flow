# AGENTS.md

This file provides guidance to agents when working with code in this repository.

## Project Nature

Config-only repo — no build system, no package manager, no runtime code. Contains YAML mode export files for [Roo Code](https://github.com/RooCodeInc/Roo-Code) that define a multi-agent orchestration pipeline.

## Validation & Testing

- No automated tests. Validate by importing `agents/*.yaml` into Roo Code → Settings → Custom Modes → Import
- Verify mode activates correctly and integrates with the full pipeline (all 5 modes)
- YAML syntax must be valid — no linter configured, check manually
- Common failure: `customInstructions` uses YAML block scalars (`>-` or `|-`) — incorrect indentation breaks parsing silently

## Conventional Commits (Required)

Format: `<type>(<scope>): <subject>` — imperative mood, ≤72 chars, no trailing period.
Types: `feat`, `fix`, `docs`, `refactor`, `chore`, `test`, `style`, `perf`, `ci`, `revert`
Breaking: `feat!:` or `BREAKING CHANGE:` footer → major version bump.

## Release Pipeline

Push to `main` with changes under `agents/**` triggers auto semantic versioning + GitHub Release via `.github/workflows/release.yml`. All 5 YAML files are attached as release assets.

## Branch Naming

Prefixes required: `feat/`, `fix/`, `docs/`, `refactor/`, `chore/` (e.g. `feat/add-debug-mode`).

## PR Policy

PRs NOT automatically accepted. Must pass: (1) testing in Roo Code, (2) evaluation for pipeline consistency, (3) implementation review.

## YAML Schema

Each file in `agents/` follows: `customModes` array with `slug`, `name`, `iconName`, `roleDefinition`, `whenToUse`, `description`, `groups` (permissions), `customInstructions`, `source`. All modes share persona name "Forge" — do not change.

## Pipeline Enforcement

Strict order: Ask → Architect → Subtask-Orchestrator. No mode switching — all delegation via `new_task`, all returns via `attempt_completion`. Architect restricted to `.md$` file edits only.

## Key Docs

- `README.md` — Pipeline Mermaid diagrams, mode descriptions, install instructions
- `CONTRIBUTING.md` — Full simulated agent flow walkthrough (lines 124-271), commit conventions, PR process
- `addons/caveman.md` — Caveman token-compression addon setup
- `mcp/searxng.md` — SearXNG MCP server setup (Ask mode web search)
- `mcp/git-mcp-server.md` — Git MCP server setup (Git mode operations)
- `addons/README.md` — Addons directory overview
- `mcp/README.md` — MCP servers directory overview
- `agents/README.md` — Agent modes directory overview

## Directory READMEs

Each major directory (`agents/`, `addons/`, `mcp/`) contains a `README.md` introducing its contents. When adding new files to these directories, update the directory README and the root `README.md` repository structure accordingly.
