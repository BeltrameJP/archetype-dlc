# archetype-dlc (v0.1)

**archetype-dlc** is a language-agnostic repository of step-by-step agentic workflows and behavioral modes. In this context, **DLC** stands for **Development Life Cycle**—providing AI agents with the structural blueprints and patterns they need to build projects with consistency, safety, and efficiency.

> **Status:** v0.1 (Experimental / Testing phase). This framework is currently being battle-tested in real-world projects.

## 🚀 Concept

Agents perform best when they have a clear behavioral archetype to follow. This repository provides:
- **Workflows:** Step-by-step logic for the entire Development Life Cycle.
- **Best Practices:** Language-free guidelines on context management, security, and architectural integrity.
- **Patterns:** Repeatable modes of behavior for complex engineering tasks.

## 📂 Structure

- `/workflows`: Modular step-by-step guides for project initialization (Bootstrap), discovery, and implementation.
- `/best-practices`: Universal guidelines for agentic development (Mandates, Vision, Infrastructure).
- `/templates`: Standardized YAML templates for Epics, Cards, Rules, and Workflows.

## 🤖 How to Start (Agent Entrypoint)

You do not need to read these documents manually. **archetype-dlc** is designed to be consumed and executed by AI agents (e.g., Gemini CLI, Cursor, Claude, GitHub Copilot).

To begin a new project or onboard an existing one, provide your agent with access to this repository and issue the following prompt:

> "Please read the `workflows/00-bootstrap-and-setup.md` file from the **archetype-dlc** repository. Execute the **Bootstrap phase (Phase 00)** for this project."

Once initiated, the agent will guide you through the 7-step Development Life Cycle, starting with project initialization and vision alignment.

## 🤖 Agent Compatibility

archetype-dlc is designed to run on any agent that can read files and execute terminal commands. Agents with more capabilities unlock more of the framework.

| Agent | Native instruction file | Native init command | File I/O | Shell / Terminal | Git ops | Sub-agents |
|---|---|---|---|---|---|---|
| **Claude Code** | `CLAUDE.md` | `/init` | ✅ | ✅ | ✅ | ✅ |
| **Gemini CLI** | `GEMINI.md` | `gemini init` | ✅ | ✅ | ✅ | Partial |
| **Cursor** | `.cursor/rules/*.mdc` | Generate Cursor Rules | ✅ | Context-dependent | Partial | ❌ |
| **GitHub Copilot** | `.github/copilot-instructions.md` | Manual | ✅ | ❌ | ❌ | ❌ |

**Minimum required capabilities per phase:**

| Phase | Min. required |
|---|---|
| 00 Bootstrap | File I/O |
| 01–02 Discovery & Architecture | File I/O |
| 03 Implementation Loop | File I/O + Shell (to run tests/linters) |
| 04–05 Validation & QA | File I/O + Shell |
| 06 Release | File I/O + Shell + Git |

> Agents without shell access (e.g., GitHub Copilot) can participate in Phases 00–02 but will require a human to execute terminal commands in Phases 03–06.

### Why agent instruction files are not committed

Agent instruction files (`CLAUDE.md`, `GEMINI.md`, `.cursor/rules/`, etc.) are listed in `.gitignore` and excluded from this repository. This is intentional:

- **archetype-dlc is agent-agnostic.** Committing files specific to one tool would contradict the framework's core design.
- **They are generated, not authored.** Each developer runs the Bootstrap phase with their own agent, which produces the instruction file suited to that tool.
- **They are personal to the developer's environment.** Two developers using different agents on the same project each need their own file — there is no single correct version to commit.

## ⚖️ License

This project is licensed under the [MIT License](LICENSE).
