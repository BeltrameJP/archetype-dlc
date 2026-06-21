# 03. Implementation Loop

> **Agent prompt:** [`agents/implementer.md`](../agents/implementer.md) — concise subagent version of this workflow.

## 🎯 Objective
Execute individual tasks through a rigorous, self-correcting development cycle.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)
- [03. Build & Test Infrastructure](../best-practices/03-build-and-test-infrastructure.md)

### 🟡 Implementation Choice (Select One)
- [04a. TDD Implementation](../best-practices/04a-tdd-implementation.md) - **Recommended** for behavioral correctness.
- [04b. Standard Implementation](../best-practices/04b-standard-implementation.md) - For non-TDD projects or simple tasks.

### 🛠️ Context & Tools
- The requirements folder (e.g., `.archetype/cards/`) containing the project roadmap.
- A functional development environment.
- Testing frameworks configured.

## 🛠️ Execution Steps

### 1. Active Card & Workflow Selection
Never assume which task is next or which Git patterns to follow.
- **Action:** List the pending Cards from the requirements directory.
- **Action:** Ask the user: *"Which Card (ID or Title) should I start working on now?"*
- **Action:** Read the selected Card YAML file.
- **Action:** Check for the existence of `[chosen-root]/git-workflow.md`. If found, read it to understand the required branching and commit patterns.

### 2. Git Branch Creation
If a Git Workflow is defined:
- **Action:** Create a new feature branch from the base branch (e.g., `main`) following the project's naming pattern (e.g., `feature/CARD-001-login-ui`).
- **Action:** Verify you are on the correct branch before proceeding.

### 3. Infrastructure & Environment Setup
Before writing any code, follow **Best Practice 03 (Build & Test Infrastructure)**. Verify that all build/test commands are confirmed and any required `tmp-build-test-guide.md` is initialized.

### 4. Test-Driven or Atomic Setup
Depending on the chosen mode (04a or 04b), prepare your implementation checklist. If using TDD (04a), write your failing unit test now based on the selected Card's criteria.

### 5. Surgical Implementation
Write the minimum code necessary to make the current test pass or to fulfill the current Card's Acceptance Criteria. Adhere strictly to project styles, patterns, the `.agents/project-rules.md` (in the requirements root), and the Git commit standards once finished.

### 6. Self-Correction & Refactoring
Run the tests. If they fail, analyze the error, backtrack to the implementation, and fix. Refactor for readability and performance once passing.

### 7. Verification & Linting
Run project-wide linters and type-checkers. Ensure no regressions were introduced in related modules.

### 8. Commits & Status Update
- **Action:** If a Git Workflow is defined, commit the changes using the defined commit standards and templates.
- **Action:** Update the status of the Card YAML file (e.g., change `status` to `done`).
- **Action:** Update inline comments or local READMEs if the implementation changed the internal API or structure.

### 9. Rule Extraction & Evolution
Reflect on the implementation to improve the project's long-term standards.
- **Action:** Analyze the stylistic and architectural choices made during this task.
- **Action:** If a repeatable pattern was established or a specific pitfall was avoided (e.g., avoiding wildcard imports, standardizing error handling), **suggest** an update to `.agents/project-rules.md` in the requirements root.
- **Action:** Ask the user: *"Should I formalize this pattern as a project rule?"*

### 10. Transition to Review (Mandatory Gate)
Maintain structural integrity by ensuring every task is validated before moving forward.
- **Mandate:** You **MUST NOT** propose, ask about, or initiate work on a second Card until the current implementation has been formally reviewed.
- **Action:** Ask the user: *"The implementation and status update are complete. Would you like me to initiate the **Validation & Review (Phase 04)** for this card now (e.g., via a sub-agent or in this session)?"*

## ✅ Validation
- The agent explicitly asked for the Card before starting work.
- The code passes all new and existing tests.
- Linters and type-checkers report zero errors.
- The agent reflected on and suggested improvements to the project's custom best practices.
- **Strict Sequence:** The agent stopped after implementation and requested a Phase 04 review instead of suggesting a new task.
