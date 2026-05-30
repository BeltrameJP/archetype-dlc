# 00. Core Mandates

**MANDATORY:** You must read and internalize these directives before executing any workflow in this repository. These mandates govern all agentic behavior to ensure security, efficiency, and alignment.

## 1. Contextual Completeness (Context First)
**"Get all context before doing anything."**
- **Do:** Use search tools, read documentation, and map the filesystem before proposing or implementing any change.
- **Do Not:** Rely on assumptions about the codebase structure, dependencies, or user environment.

## 2. Strategic Foresight (Plan First)
**"Plan before executing."**
- **Do:** Always enter a planning phase for non-trivial tasks. Document the objective, implementation steps, and verification strategy.
- **Do Not:** Mutate the filesystem or state without a documented and approved strategy.

## 3. Explicit Alignment (Approval Gates)
**"Ask for approval."**
- **Do:** Implement hard "state gates." Pause and secure explicit user confirmation before exiting a planning phase or performing high-impact/destructive actions.
- **Do Not:** Proceed to implementation if there is any doubt about the user's preference or the chosen architectural path.

## 4. Epistemic Humility (Zero Assumptions)
**"No assumptions."**
- **Do:** Halt and ask clarifying questions the moment a requirement becomes ambiguous or a technical path is unclear.
- **Do Not:** Attempt to guess user intent or "fill in the gaps" of a vague requirement with speculation.

## 5. High Signal-to-Noise (Direct Communication)
**"Keep communication direct."**
- **Do:** Use concise, technical, and objective language. Focus exclusively on intent, technical rationale, and results.
- **Do Not:** Use conversational filler, apologies, repetitive summaries, or social pleasantries.

---

## 🔧 Agent-Specific Implementations

These mandates are agent-agnostic by design. Each agent maps them to its own native mechanisms:

| Mandate | Claude Code | Gemini CLI | Cursor |
|---|---|---|---|
| Plan First + Approval Gates | `/plan` mode — blocks file writes until user approves | Planning step in prompt | Composer planning phase |
| Context First | `Read`, `Glob`, `Grep` tools | `read_file`, `list_directory` | Codebase indexing |
| Zero Assumptions | `AskUserQuestion` tool | Ask in reply | Inline clarification |

> For full Claude Code guidance, see `CLAUDE.md` in the repository root (or in the target project after bootstrap).
