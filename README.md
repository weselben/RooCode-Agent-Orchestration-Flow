<div align="center">

# 🎯 RooForge

**A structured multi-agent orchestration system for [Roo Code](https://github.com/RooCodeInc/Roo-Code)**

A hierarchical pipeline of specialized AI modes - from strategic planning to atomic execution.

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/weselben/RooForge?include_prereleases)](../../releases/latest)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

</div>

---

## 📋 Overview

This project provides a curated set of **custom mode export files** that define a disciplined, multi-layered agent orchestration workflow for Roo Code. Each mode is a specialist with a clearly defined role, and together they form a strict pipeline that ensures every task is properly researched, planned, decomposed, executed, and committed.

## 🔄 The Pipeline

```mermaid
flowchart TD
    User["👤 User Request"] --> Orchestrator
    Orchestrator["🎯 Orchestrator<br/><i>Strategic planning & task bounding</i>"] --> Ask
    Ask["🔍 Ask<br/><i>Intel acquisition & research</i>"] --> Architect
    Architect["🏗️ Architect<br/><i>Technical design & blueprints</i>"] --> Orchestrator
    Orchestrator --> SubtaskOrchestrator
    SubtaskOrchestrator["⚙️ Subtask Orchestrator<br/><i>Atomic task decomposition</i>"] --> Code
    SubtaskOrchestrator --> Debug["🪲 Debug"]
    SubtaskOrchestrator --> Git
    Code["💻 Code<br/><i>Implementation</i>"] --> SubtaskOrchestrator
    Debug --> SubtaskOrchestrator
    Git["📦 Git<br/><i>Conventional commits & version control</i>"] --> SubtaskOrchestrator

    style Orchestrator fill:#4A90D9,color:#fff,stroke:#2C5F8A
    style Ask fill:#7B68EE,color:#fff,stroke:#4B3F8A
    style Architect fill:#E67E22,color:#fff,stroke:#A05A15
    style SubtaskOrchestrator fill:#27AE60,color:#fff,stroke:#1A7A42
    style Code fill:#8E44AD,color:#fff,stroke:#5B2D6E
    style Debug fill:#C0392B,color:#fff,stroke:#8A2520
    style Git fill:#F39C12,color:#fff,stroke:#B8750E
```

### Pipeline Phases

| Phase | Mode | Purpose |
|-------|------|---------|
| **1 - Intel** | Ask | Eliminate unknowns via web research & codebase analysis |
| **2 - Design** | Architect | Produce a detailed technical blueprint |
| **3 - Plan** | Orchestrator | Decompose blueprint into bounded task groups |
| **4 - Execute** | Subtask Orchestrator | Break task groups into atomic subtasks |
| **5 - Implement** | Code / Debug | Write or fix code |
| **6 - Commit** | Git | Validate, stage, and commit with conventional messages |

## 🤖 Modes

| Mode | File | Description |
|------|------|-------------|
| **Orchestrator** | [`agents/orchestrator-export.yaml`](agents/orchestrator-export.yaml) | Strategic entry point. Performs high-level task bounding, enforces the pipeline, and delegates to specialized modes. |
| **Ask** | [`agents/ask-export.yaml`](agents/ask-export.yaml) | Intelligence specialist. Performs web research, codebase analysis, and generates "State of Intel" reports. |
| **Architect** | [`agents/architect-export.yaml`](agents/architect-export.yaml) | Technical leader. Creates detailed blueprints, system designs, and structured plans from gathered intelligence. |
| **Subtask Orchestrator** | [`agents/subtask-orchestrator-export.yaml`](agents/subtask-orchestrator-export.yaml) | Execution manager. Decomposes task groups into the smallest atomic units and delegates to implementation specialists. |
| **Git** | [`agents/git-export.yaml`](agents/git-export.yaml) | Version control specialist. Handles conventional commits, branch management, and repository integrity. |

## 🧩 Mode Interaction Flow

```mermaid
flowchart TD
    U["👤 User"] -->|"Submit request"| O1["🎯 Orchestrator<br/><i>Evaluate ambiguity</i>"]
    O1 -->|"Phase 1 - Gather intel"| A["🔍 Ask<br/><i>Web research & codebase analysis</i>"]
    A -->|"State of Intel report"| O2["🎯 Orchestrator<br/><i>Assemble Master Context</i>"]
    O2 -->|"Phase 2 - Design blueprint"| AR["🏗️ Architect<br/><i>Technical reasoning & planning</i>"]
    AR -->|"Technical blueprint"| O3["🎯 Orchestrator<br/><i>Decompose into TG-1, TG-2...</i>"]
    O3 -->|"Phase 4 - Execute task group"| SO["⚙️ Subtask Orchestrator<br/><i>Atomic decomposition</i>"]
    SO -->|"Implement / Fix"| C["💻 Code / Debug<br/><i>Write or fix code</i>"]
    C -->|"Result"| SO
    SO -->|"Commit changes"| G["📦 Git<br/><i>Conventional commit</i>"]
    G -->|"Commit hash"| SO
    SO -->|"Task group result"| O4["🎯 Orchestrator<br/><i>Evaluate & next group</i>"]
    O4 -->|"All groups done"| U2["👤 User<br/><i>Final result</i>"]

    style U fill:#95A5A6,color:#fff,stroke:#7F8C8D
    style U2 fill:#95A5A6,color:#fff,stroke:#7F8C8D
    style O1 fill:#4A90D9,color:#fff,stroke:#2C5F8A
    style O2 fill:#4A90D9,color:#fff,stroke:#2C5F8A
    style O3 fill:#4A90D9,color:#fff,stroke:#2C5F8A
    style O4 fill:#4A90D9,color:#fff,stroke:#2C5F8A
    style A fill:#7B68EE,color:#fff,stroke:#4B3F8A
    style AR fill:#E67E22,color:#fff,stroke:#A05A15
    style SO fill:#27AE60,color:#fff,stroke:#1A7A42
    style C fill:#8E44AD,color:#fff,stroke:#5B2D6E
    style G fill:#F39C12,color:#fff,stroke:#B8750E
```

## 🚀 Installation

1. **Download** the export YAML files from the [latest release](../../releases/latest).
2. Open **Roo Code** in VS Code.
3. Navigate to **Roo Code Settings → Custom Modes**.
4. Click **Import** and select the downloaded `.yaml` file(s).
5. The modes will appear in your mode selector.

> **Tip:** Import all five modes for the full orchestration pipeline experience.

## 🔄 Automated Releases

This repository uses **automated semantic versioning** powered by [Conventional Commits](https://www.conventionalcommits.org/):

```mermaid
flowchart LR
    P["Push to main"] --> W["GitHub Actions Workflow"]
    W --> V["Compute next version<br/>from commit messages"]
    V --> T["Create git tag<br/>(e.g. v1.2.3)"]
    T --> R["Publish GitHub Release<br/>with YAML assets"]
```

### Commit Convention

| Prefix | Version Bump | Example |
|--------|-------------|---------|
| `feat:` | **Minor** | `feat: add debug mode export` |
| `fix:` | **Patch** | `fix: correct orchestrator role definition` |
| `feat!:` or `BREAKING CHANGE` | **Major** | `feat!: redesign pipeline architecture` |
| `docs:` | None | `docs: update README` |
| `chore:` | None | `chore: update workflow` |
| `refactor:` | None | `refactor: simplify subtask logic` |
| `test:` | None | `test: add validation for exports` |

## 🧪 Optional Addons

### Caveman - Token-Efficient Communication

An optional [Caveman](https://github.com/JuliusBrussee/caveman) addon that enforces ultra-terse communication across the entire orchestration stack. Cuts ~65% of output tokens while keeping full technical accuracy.

**Quick install:**
```bash
npx skills add JuliusBrussee/caveman
# Select "Roo Code" when prompted
```

For full setup instructions, Global Custom Instructions block, compression levels, and the experimental cavereason mode - see the complete guide at **[`addons/caveman.md`](addons/caveman.md)**.

## 🔌 MCP Servers

The orchestration pipeline requires two MCP (Model Context Protocol) servers for full functionality. These servers extend the capabilities of specific modes in the pipeline.

| Server | File | Required By | Purpose |
|--------|------|-------------|---------|
| **SearXNG** | [`mcp/searxng.md`](mcp/searxng.md) | Ask | Web search & URL reading |
| **Git MCP** | [`mcp/git-mcp-server.md`](mcp/git-mcp-server.md) | Git | Git operations (CLI fallback) |

> 💡 See each server's documentation for full setup instructions, configuration details, and usage examples.

## 📁 Repository Structure

```
.
├── .github/
│   ├── workflows/
│   │   └── release.yml              # Auto-versioning & release workflow
│   └── ISSUE_TEMPLATE/              # Bug reports, features, questions
├── agents/
│   ├── README.md                    # Agent modes directory overview
│   ├── orchestrator-export.yaml     # Orchestrator mode
│   ├── subtask-orchestrator-export.yaml  # Subtask Orchestrator mode
│   ├── architect-export.yaml        # Architect mode
│   ├── ask-export.yaml              # Ask (research) mode
│   └── git-export.yaml              # Git mode
├── addons/
│   ├── README.md                    # Addons directory overview
│   └── caveman.md                   # Caveman addon setup guide
├── mcp/
│   ├── README.md                    # MCP servers directory overview
│   ├── searxng.md                   # SearXNG MCP server setup (Ask mode)
│   └── git-mcp-server.md            # Git MCP server setup (Git mode)
├── CONTRIBUTING.md                  # Contribution guidelines
├── LICENSE                          # Apache License 2.0
└── README.md                        # This file
```

## 🤝 Contributing

We welcome community involvement! However, please note that **pull requests are not automatically accepted**. All contributions go through an evaluation process.

See [**CONTRIBUTING.md**](CONTRIBUTING.md) for full details on:
- Our PR evaluation process
- Conventional Commits (extended) requirements
- Feature branch workflow
- Testing expectations

## 📄 License

Licensed under the [Apache License 2.0](LICENSE).

```
Copyright 2026 weselben

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## ⭐ Acknowledgments

- Built for [Roo Code](https://github.com/RooCodeInc/Roo-Code) - an AI-powered coding assistant for VS Code.
- Inspired by hierarchical task decomposition and multi-agent orchestration patterns.
- [Caveman](https://github.com/JuliusBrussee/caveman) by JuliusBrussee - token-efficient communication skill for AI agents.

---

<div align="center">

**[⬆ Back to top](#-rooforge)**

</div>
