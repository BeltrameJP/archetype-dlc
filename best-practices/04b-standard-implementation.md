# 04b. Standard Implementation

## 🎯 Objective
Execute feature implementation based on structured requirements, emphasizing atomic progress and post-implementation verification.

## 🔄 Atomic Implementation Loop

For users who prefer standard development over TDD, follow this atomic loop:

1.  **Select Criterion:** Choose a single Acceptance Criterion from the Epic to implement.
2.  **Surgical Implementation:** Write the code to fulfill that specific criterion. Adhere to existing patterns and avoid over-engineering.
3.  **Validation:** Immediately verify the change. This can be via manual testing, running existing test suites, or writing a post-implementation test.
4.  **Repeat:** Move to the next criterion only once the current one is verified.

## 🧠 Memory & Resilience (The Checklist)

To ensure consistency across restarts or context window resets:

1.  **Initialize Checklist:** Before writing any code, create a temporary file named `tmp-implementation-checklist.md`.
2.  **Map Criteria:** List all Acceptance Criteria from the Epic as checklist items.
3.  **Track Progress & Plan:** 
    - Before writing code for a criterion, add a brief **Implementation Plan** summary to the checklist item.
    - **Approval Gate:** You **MUST** present this plan to the user and wait for explicit approval before writing any implementation code.
    - Check off items ONLY after they have been implemented and verified.

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
3. **UPDATE CHECKBOXES:** Mark `[x]` in the `tmp-implementation-checklist.md` immediately after completing each individual step.
4. **STORY TRACEABILITY:** Mark the corresponding Acceptance Criterion as `[x]` only when the full functionality is implemented and verified.
5. **RESPECT DEPENDENCIES:** Only implement a task when its technical or logical dependencies are fully satisfied.

- **Post-Generation Summary:** Immediately after a successful generation, provide a minimal YAML summary to the user.
  ```yaml
  generation_summary:
    brief: "Concise description of the technical change."
    requirements_fulfilled:
      - "Criterion 1 from checklist"
      - "Criterion 2 from checklist"
  ```

## 🛠️ Directives
- **Criterion Focus:** Never implement multiple Acceptance Criteria in a single turn. Focus on one at a time to maintain high signal and low error rates.
- **Verification Mandate:** Code is not considered "Done" until its behavior has been empirically verified.
- **Context Preservation:** Always read the `tmp-implementation-checklist.md` at the start of every turn during Phase 03.

## ✅ Validation
- A `tmp-implementation-checklist.md` exists and is up-to-date.
- Every checkmark corresponds to a verified feature in the codebase.
