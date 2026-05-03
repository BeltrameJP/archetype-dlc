# 03. Implementation Loop

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

### 1. Active Card Selection
Never assume which task is next. The agent must synchronize with the user.
- **Action:** List the pending Cards from the requirements directory.
- **Action:** Ask the user: *"Which Card (ID or Title) should I start working on now?"*
- **Action:** Once confirmed, read the selected Card YAML file thoroughly to ingest its Acceptance Criteria and dependencies.

### 2. Infrastructure & Environment Setup
Before writing any code, follow **Best Practice 03 (Build & Test Infrastructure)**. Verify that all build/test commands are confirmed and any required `tmp-build-test-guide.md` is initialized.

### 3. Test-Driven or Atomic Setup
Depending on the chosen mode (04a or 04b), prepare your implementation checklist. If using TDD (04a), write your failing unit test now based on the selected Card's criteria.

### 4. Surgical Implementation
Write the minimum code necessary to make the current test pass or to fulfill the current Card's Acceptance Criteria. Adhere strictly to project styles, patterns, and the `99-project-rules.md` (if present).

### 5. Self-Correction & Refactoring
Run the tests. If they fail, analyze the error, backtrack to the implementation, and fix. Refactor for readability and performance once passing.

### 6. Verification & Linting
Run project-wide linters and type-checkers. Ensure no regressions were introduced in related modules.

### 7. Documentation & Status Update
- **Action:** Update the status of the Card YAML file (e.g., change `status` to `done`).
- **Action:** Update inline comments or local READMEs if the implementation changed the internal API or structure.

### 8. Rule Extraction & Evolution
Reflect on the implementation to improve the project's long-term standards.
- **Action:** Analyze the stylistic and architectural choices made during this task.
- **Action:** If a repeatable pattern was established or a specific pitfall was avoided (e.g., avoiding wildcard imports, standardizing error handling), **suggest** an update to `99-project-rules.md`.
- **Action:** Ask the user: *"Should I formalize this pattern as a project rule?"*

### 9. Transition to Review (Mandatory Gate)
Maintain structural integrity by ensuring every task is validated before moving forward.
- **Mandate:** You **MUST NOT** propose, ask about, or initiate work on a second Card until the current implementation has been formally reviewed.
- **Action:** Ask the user: *"The implementation and status update are complete. Would you like me to initiate the **Validation & Review (Phase 04)** for this card now (e.g., via a sub-agent or in this session)?"*

## ✅ Validation
- The agent explicitly asked for the Card before starting work.
- The code passes all new and existing tests.
- Linters and type-checkers report zero errors.
- The agent reflected on and suggested improvements to the project's custom best practices.
- **Strict Sequence:** The agent stopped after implementation and requested a Phase 04 review instead of suggesting a new task.
