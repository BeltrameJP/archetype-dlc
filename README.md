# archetype-dlc (v0.2)

**archetype-dlc** is a language-agnostic repository of step-by-step agentic workflows and behavioral modes. In this context, **DLC** stands for **Development Life Cycle**—providing AI agents with the structural blueprints and patterns they need to build projects with consistency, safety, and efficiency.

> **Status:** v0.2 — Subagent architecture with session memory system. Each DLC phase is now a standalone agent definition, and cross-session state is recoverable.

## 🚀 Concept

Agents perform best when they have a clear behavioral archetype to follow. This repository provides:
- **Workflows:** Step-by-step logic for the entire Development Life Cycle.
- **Best Practices:** Language-free guidelines on context management, security, session continuity, and architectural integrity.
- **Subagents:** Pre-built, model-agnostic agent definitions per DLC phase — ready to delegate via `task` (opencode) or use as focused prompts (Claude, Gemini, Cursor).
- **Session Memory:** A recoverable state file (`.agents/memory.md`) that lets any AI agent pick up exactly where it left off across sessions.
- **Templates:** Standardized YAML templates for Epics, Cards, Rules, and Workflows.

## 📂 Structure

- `/agents`: Pre-built, provider-agnostic agent definitions — one per DLC phase. Any AI tool can read them.
- `/workflows`: Modular step-by-step guides for the entire Development Life Cycle (00–06).
- `/best-practices`: Universal guidelines for agentic development (Mandates, Vision, Infrastructure, Session Memory).
- `/templates`: Standardized YAML/Markdown templates for Epics, Cards, Rules, Memory, and Workflows.

## 🤖 How to Start (Agent Entrypoint)

You do not need to read these documents manually. **archetype-dlc** is designed to be consumed and executed by AI agents (e.g., Gemini CLI, Cursor, Claude, GitHub Copilot).

To begin a new project or onboard an existing one, provide your agent with access to this repository and issue the following prompt:

> "Please read the `workflows/00-bootstrap-and-setup.md` file from the **archetype-dlc** repository. Execute the **Bootstrap phase (Phase 00)** for this project."

Once initiated, the agent will guide you through the 7-step Development Life Cycle, starting with project initialization and vision alignment.

## 🧩 DLC Subagents

Each DLC phase has a pre-built, model-agnostic agent definition in [`agents/`](agents/). These are standalone prompts tailored to that phase — usable by any AI tool (opencode, Claude, Gemini, Cursor).

| Agent | Phase | Permission Boundary | File |
|---|---|---|---|
| `plan` | Planning Gate | edit: deny | [`agents/plan.md`](agents/plan.md) |
| `bootstrapper` | 00 Bootstrap | edit: allow, bash: ask | [`agents/bootstrapper.md`](agents/bootstrapper.md) |
| `discoverer` | 01 Discovery | edit: allow, webfetch | [`agents/discoverer.md`](agents/discoverer.md) |
| `architect` | 02 Architecture | edit: allow | [`agents/architect.md`](agents/architect.md) |
| `implementer` | 03 Implementation | full | [`agents/implementer.md`](agents/implementer.md) |
| `reviewer` | 04 Validation | edit: deny | [`agents/reviewer.md`](agents/reviewer.md) |
| `qa-engineer` | 05 QA | bash: allow | [`agents/qa-engineer.md`](agents/qa-engineer.md) |
| `releaser` | 06 Release | full | [`agents/releaser.md`](agents/releaser.md) |

**opencode** users delegate via `task subagent_type: "bootstrapper"`.  
**Claude/Gemini/Cursor** users read the file directly and follow its instructions.

## 💾 Session Memory

Every project bootstrapped with archetype-dlc gets a `[chosen-root]/.agents/memory.md` file — the canonical cross-session state. On every session:

1. **Start** — Agent reads memory, reports current phase and active card.
2. **During** — Agent records key decisions, updates next steps, transitions phase status.
3. **End** — Agent writes `last_session` timestamp.

The `.agents/memory.md` file is gitignored — each developer maintains their own state. See [`best-practices/06-session-memory.md`](best-practices/06-session-memory.md) for the full protocol.

## 🤖 Agent Compatibility

archetype-dlc is designed to run on any agent that can read files and execute terminal commands. Agents with more capabilities unlock more of the framework.

| Agent | Native instruction file | Native init command | File I/O | Shell / Terminal | Git ops | Sub-agents |
|---|---|---|---|---|---|---|
| **Claude Code** | `CLAUDE.md` | `/init` | ✅ | ✅ | ✅ | ✅ |
| **Gemini CLI** | `GEMINI.md` | `gemini init` | ✅ | ✅ | ✅ | Partial |
| **opencode** | `OPENCODE.md` | `opencode.json` (manual, gitignored) | ✅ | ✅ | ✅ | ✅ |
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

Agent-specific files (`CLAUDE.md`, `GEMINI.md`, `opencode.json`, `.cursor/rules/`, etc.) and runtime state (`.agents/memory.md`) are listed in `.gitignore` and excluded from version control. This is intentional:

- **archetype-dlc is agent-agnostic.** Committing files specific to one tool would contradict the framework's core design.
- **They are generated, not authored.** Each developer runs the Bootstrap phase with their own agent, which produces the instruction file suited to that tool.
- **They are personal to the developer's environment.** Two developers using different agents on the same project each need their own file — there is no single correct version to commit.
- **Session state is per-developer.** Each developer's `.agents/memory.md` tracks their own progress and decisions; committing it would cause conflicts and confusion.

## ⚖️ License

This project is licensed under the [MIT License](LICENSE).
