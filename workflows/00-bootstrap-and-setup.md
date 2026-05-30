# 00. Bootstrap & Setup

## 🎯 Objective
Initialize an existing repository with the Archetype standards, making it "Agent-Ready" by establishing persistent requirements storage, behavioral guardrails, and environment documentation.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)

### 🛠️ Context & Tools
- An existing project repository.
- Access to global `archetype-dlc` repository content.

## 🛠️ Execution Steps

### 1. Pre-flight Idempotency Check
Before creating any files, the agent must check if an Archetype setup already exists.
- **Scan:** Search for `ARCHETYPE.md` or a requirements root directory (e.g., `.archetype/`).
- **If Found:** Halt and inform the user. Ask for a decision:
  - **Update:** Keep existing `VISION.md`, Epics, and Cards. Only overwrite the local `best-practices/` with the latest global versions. Proceed to Step 4.
  - **Hard Reset:** Delete the existing requirements folder and `ARCHETYPE.md`, then proceed from Step 2.
  - **Abort:** Exit the workflow without making changes.

### 2. Requirements Folder Initialization
Ask the user for their preferred folder name to store requirements (default: `.archetype/`).
- **Action:** Create the chosen root folder.
- **Action:** Create `epics/`, `cards/`, and `best-practices/` subdirectories within that root.

### 3. Vision & Goals Definition
Conduct a "Vision Interview" with the user to establish the project's long-term direction.
- **Source Material Discovery:** Before interviewing, scan the project root for existing agent instruction files using this lookup table:

  | Agent | File(s) to scan |
  |---|---|
  | Claude Code | `CLAUDE.md` |
  | Gemini CLI | `GEMINI.md` |
  | Cursor | `.cursor/rules/*.mdc`, `.cursorrules` |
  | GitHub Copilot | `.github/copilot-instructions.md` |
  | Generic | `rules.md`, `RULES.md`, `AGENTS.md` |
- **The Fast-Track Offer:** If found, ask: *"I've found existing instruction files (`[filename]`). Would you like me to use these as a base to pre-fill the `VISION.md` and `project-rules.md`?"*
- **Action:** If the user agrees, ingest the material to draft pre-filled files. Otherwise, ask about the project's mission, core objectives, and target audience.
- **Action:** Create a `VISION.md` file in the root of the chosen requirements folder (e.g., `[chosen-root]/VISION.md`).
- **Standard Structure:**
  - **Mission Statement:** A concise "Why this project exists."
  - **Core Objectives:** Measurable outcomes for success.
  - **Target Audience:** Who the users are.
  - **Non-Goals:** Boundaries of the project to prevent scope creep.

### 4. Localize Core Mandates (Direct Copy)
To ensure the project is self-contained and resilient:
- **Action:** Copy the content of `best-practices/00-core-mandates.md` and `best-practices/01-feedback-and-formatting.md` from the global `archetype-dlc` repo.
- **Action:** Copy `templates/project-rules.yaml` and save it as `[chosen-root]/project-rules.md`.
- **Action:** Save the mandates into the local `[chosen-root]/best-practices/` directory.
- **The Custom Rules Prompt:** Notify the user: *"I've initialized `project-rules.md`. Do you have any specific project rules or preferred libraries you want to add now, or should we leave it as a template for later?"*

### 5. Infrastructure & Environment Setup
Execute the logic from **Best Practice 03 (Build & Test Infrastructure)**.
- **Action:** Scan the root directory for standard configuration files.
- **Action:** Propose standard build and test commands based on the detected stack.
- **Action:** Create verified, structured instruction files (Permanent or Temporary as per user choice) following the 4-part mandatory structure.

### 6. Validation Setup
Execute the logic from **Best Practice 05 (Validation & Review)**.
- **Action:** Ask the user if they wish to initialize `validation-instructions.md` for CI/CD automation.

### 7. Git Life Cycle Setup
Establish a standardized Git workflow for branches, commits, and Pull Requests.
- **Proactive Offer:** Propose initializing a `git-workflow.md` file based on the default template (`templates/git-workflow.yaml`).
- **Action:** Copy the template and save it as `[chosen-root]/git-workflow.md`.
- **Customization:** Ask the user if they want to modify the branch naming pattern or commit standards now, or leave them as defaults.

### 8. Agent Instruction File Creation
Generate the native instruction file for the active agent. This file is read automatically at the start of every future session on this project and must point back to the localized mandates, VISION, and Cards.

**Note:** This file is gitignored by archetype-dlc convention. It is generated per-agent and per-developer and must never be committed to the repository.

#### Step 1 — Use the agent's native initialization command (preferred)

Each agent has its own project initialization mechanism. Use it first — it produces a richer, more tailored file than manual creation:

| Agent | Native initialization |
|---|---|
| Claude Code | Run `/init` — auto-generates `CLAUDE.md` from the codebase |
| Gemini CLI | Run `gemini init` in the project root |
| Cursor | Use "Generate Cursor Rules" from the Cursor interface |
| GitHub Copilot | No native init command — proceed to Step 2 |

After running the native init, **enrich the generated file** by appending the mandatory content from Step 2.

#### Step 2 — Mandatory content (add to the generated file, or create manually if no native init exists)

The instruction file must contain at minimum:
1. A one-line description of the project.
2. A directive to read `[chosen-root]/best-practices/00-core-mandates.md` before acting.
3. A pointer to `[chosen-root]/VISION.md` for project context.
4. The path to `[chosen-root]/cards/` for the active task list.
5. Agent-specific Approval Gate instruction (e.g., for Claude Code: use `/plan` mode; for Gemini CLI: present a written plan and wait for explicit approval before any `write_file` or shell call).

**Fallback — target file if no native init exists:**

| Agent | File | Location |
|---|---|---|
| Claude Code | `CLAUDE.md` | Project root |
| Gemini CLI | `GEMINI.md` | Project root |
| Cursor | `archetype.mdc` | `.cursor/rules/` |
| GitHub Copilot | `copilot-instructions.md` | `.github/` |
| Generic | `AGENTS.md` | Project root |

- **Action:** Ask the user if there are any agent-specific behaviors or tool restrictions they want to enforce (e.g., "never run destructive git commands without approval").

### 9. Project Indexing
Create a root `ARCHETYPE.md` file in the project to serve as a manifest.
- **Action:** Include a brief overview of the 6-phase Development Life Cycle.
- **Action:** Provide relative links to the local requirements folder, instruction files, vision, git workflow, and mandates.

## ✅ Validation
- The agent explicitly checked for existing setups before proceeding.
- If a setup was found, the user's choice (Update/Reset) was confirmed and executed.
- The chosen requirements directory structure exists.
- A `VISION.md` file is created (or preserved) and approved.
- Core mandates are localized in the project.
- `build-instructions.md` and `test-instructions.md` follow the mandatory 4-part structure.
- The agent-native instruction file (`CLAUDE.md`, `GEMINI.md`, etc.) is present and points to the localized mandates and VISION.md.
- A root `ARCHETYPE.md` manifest is present and correctly linked.
