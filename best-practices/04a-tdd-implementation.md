# 04a. TDD Implementation

## 🎯 Objective
Enforce a strict Test-Driven Development (TDD) cycle to ensure behavioral correctness, minimize hallucination, and create a verifiable codebase.

## 🔄 The TDD Cycle (Red, Green, Refactor)

You **MUST** follow this sequence for every individual requirement or Acceptance Criterion:

1.  **RED:** Write a failing test that defines the expected behavior. The test should be based directly on one or more Acceptance Criteria from the Epic.
2.  **GREEN:** Write the absolute minimum code required to make the test pass. **Do not** write code for future requirements or "just-in-case" functionality.
3.  **REFACTOR:** Once the test passes, refactor the code for readability, performance, and adherence to project standards, ensuring the test remains green.

## 🧠 Memory & Resilience (The Checklist)

To ensure consistency across restarts or context window resets:

1.  **Initialize Checklist:** Before writing any code, create a temporary file named `tmp-test-checklist.md`.
2.  **Map Criteria:** Extract every Acceptance Criterion from the Epic and list it as a checklist item.
3.  **Plan Tests:** Next to each criterion, name the test file/function that will verify it.
4.  **Track Progress & Plan:** 
    - Before writing code for a criterion, add a brief **Implementation Plan** summary to the checklist item.
    - **Approval Gate:** You **MUST** present this plan to the user and wait for explicit approval before writing any implementation code.
    - Check off items ONLY when they reach the "Green" (passing) state.

## 🚀 Code Generation Directives

To ensure the generated code is high-quality and natively integrated:

- **Architectural Alignment:** Before generation, perform a "Convention Audit." 
  1. **Ask for Guidance:** First, ask the user if there is a specific convention file, style guide, or instructions (e.g., `CONTRIBUTING.md`, `STYLE.md`, `GEMINI.md`) that defines the project's coding standards.
  2. **Analyze Headlines:** Analyze the project's headlines: folder structure, naming conventions, design patterns, and business logic abstractions. 
  3. **Seamless Integration:** Your code must be indistinguishable from the existing codebase.
- **Surgical Updates:** Only modify the minimum amount of code required. Avoid "cleanups" or refactoring of unrelated logic unless explicitly requested.
- **Principle Adherence:** Strictly follow project-specific principles (e.g., SOLID, DRY, or local performance mandates) identified during Phase 02.
- **Epistemic Rigor:** Reinforce the "No Assumptions" mandate. If the implementation of a specific criterion reveals any ambiguity or requires a design decision not previously discussed, you **MUST** halt and ask for clarification before generating any code.

### ⚖️ Generation Phase Rules
1. **NO HARDCODED LOGIC:** Only execute what's written in the approved implementation plan.
2. **FOLLOW PLAN EXACTLY:** Do not deviate from the step sequence or skip logic.
3. **UPDATE CHECKBOXES:** Mark `[x]` in the `tmp-test-checklist.md` immediately after completing each individual step.
4. **STORY TRACEABILITY:** Mark the corresponding Acceptance Criterion as `[x]` only when the full functionality is implemented and verified "Green".
5. **RESPECT DEPENDENCIES:** Only implement a task when its technical or logical dependencies are fully satisfied.

- **Post-Generation Summary:** Immediately after a successful generation (reaching the "Green" state), provide a minimal YAML summary to the user.
  ```yaml
  generation_summary:
    brief: "Concise description of the technical change."
    requirements_fulfilled:
      - "Criterion 1 from checklist"
      - "Criterion 2 from checklist"
  ```

## 🛠️ Directives
- **Surgical Execution:** Your changes must be tightly scoped to the current test.
- **Fail First:** If you implement code before writing a test, you have failed this mandate.
- **Context Preservation:** Always read the `tmp-test-checklist.md` at the start of every turn during Phase 03.

## ✅ Validation
- A `tmp-test-checklist.md` exists and is up-to-date.
- Every checkmark in the checklist corresponds to a passing test in the codebase.
- No "extra" code exists that isn't covered by a test.
