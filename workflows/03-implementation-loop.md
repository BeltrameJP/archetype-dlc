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
- A specific, refined task from Phase 02.
- A functional development environment.
- Testing frameworks configured.

## 🛠️ Execution Steps

### 1. Infrastructure & Environment Setup
Before writing any code, follow **Best Practice 03 (Build & Test Infrastructure)**. Verify that all build/test commands are confirmed and any required `tmp-build-test-guide.md` is initialized.

### 2. Test-Driven or Atomic Setup
Depending on the chosen mode (04a or 04b), prepare your implementation checklist. If using TDD (04a), write your failing unit test now.

### 3. Surgical Implementation
Write the minimum code necessary to make the current test pass or to fulfill the current Acceptance Criterion. Adhere strictly to project styles and patterns.

### 4. Self-Correction & Refactoring
Run the tests. If they fail, analyze the error, backtrack to the implementation, and fix. Refactor for readability and performance once passing.

### 5. Verification & Linting
Run project-wide linters and type-checkers. Ensure no regressions were introduced in related modules.

### 6. Documentation Update
Update inline comments or local READMEs if the implementation changed the internal API or structure.

## ✅ Validation
- The code passes all new and existing tests.
- Linters and type-checkers report zero errors.
- The change is "surgically" limited to the scope of the task.
