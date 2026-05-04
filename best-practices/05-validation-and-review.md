# 05. Validation & Review

## 🎯 Objective
Establish a rigorous, objective, and constructive standard for evaluating code quality and its alignment with project goals.

## ⚖️ Quality Mandates

### 1. Epic & Criteria Alignment
- **Requirement:** Every piece of code and every unit/integration test must map directly back to the Acceptance Criteria and the overarching Epic Goal.
- **Verification:** Confirm that happy paths, edge cases, and failure modes identified in Phase 01 and 02 are fully covered and passing.

### 2. Readability & "No Leetcoding"
Code must be written for humans to read, not for computers to process at peak theoretical efficiency at the cost of clarity.
- **High-Level Priority:** Always prefer high-level, modern standard library functions and idioms (e.g., using `map`, `filter`, `reduce`, or standard async/await patterns).
- **No Leetcoding:** Avoid overly clever, convoluted, or obscure solutions that prioritize "minimal characters" or "bitwise tricks" over legibility. If a complex optimization is required, it must be accompanied by exhaustive documentation and rationale.

### 3. Project Standards & Conventions
- **Validation:** Ensure the implementation adheres strictly to the conventions and style guides identified during the "Convention Audit" in Phase 03.
- **Custom Rule Enforcement:** The agent **MUST** read the project's custom rules file (e.g., `project-rules.md` in the requirements root) and verify that the implementation complies with all project-specific constraints.
- **Git Workflow Compliance:** If a Git Life Cycle is established (e.g., `git-workflow.md` in the requirements root), ensure that branching and commits follow the defined standards.
- **Architectural Drift:** Flag any implementation that deviates from the approved technical design without a documented justification.

## 🤖 Validation Infrastructure (CI/CD)

To enable automated reviews by agents within CI/CD pipelines, a `validation-instructions.md` (or equivalent) should be established.

### 📋 Mandatory Structure:
1.  **Context Retrieval:** Explicitly define where the pipeline agent can find the source of truth for the changes (e.g., "Epic is in `[chosen-root]/epics/`, Card is in `[chosen-root]/cards/`, and Project Rules are in `[chosen-root]/project-rules.md`").
2.  **Tooling Integration:** List the exact commands for linting, static analysis (SAST), and security scanning.
3.  **Review Mandates:** Reiterate the "No Leetcoding" and "High-Level Function" priorities for the automated reviewer.
4.  **Verification of Failure:** Define how the agent should report a failed review (e.g., "Exit code 1," "GitHub comment," "YAML summary").

## 💬 The Review Protocol

Reviews are a collaborative tool for improvement. They must be technical, objective, and helpful.

### 🛑 Impersonal Feedback
- **Mandate:** Reviews must be strictly about the **CODE**, never the author.
- **Prohibited:** Personal language, condescending tones, or non-constructive criticism (e.g., "This is bad").
- **Example:** Instead of "You wrote this poorly," use "This function exceeds the complexity limit defined in [Standard X]."

### 💡 The Alternative Rule
- **Mandate:** If you flag a piece of code for rejection or improvement, you **MUST** suggest a concrete, better alternative.
- **Requirement:** Explain *why* the alternative is superior (e.g., "The suggested alternative uses native API methods which improve readability and reduce external dependencies").

### 🛑 Pure Review State (Read-Only Mandate)
- **Mandate:** During this phase, you are in a **READ-ONLY** state.
- **Strictly Prohibited:** You MUST NOT implement any of the suggested alternatives yourself, even if asked. You MUST NOT ask the user "Would you like me to fix this?", "Should we proceed?", or "What is the next step?".
- **Terminal Action:** Output the review summary (the rejection, the technical reason, and the concrete alternative) and immediately **STOP**. The review is the final output of this turn.

## ✅ Validation
- The review is purely read-only (no implementation or "next step" prompts).
- Code fulfills 100% of Acceptance Criteria.
- Feedback is impersonal and technical.
- Every rejection includes a suggested alternative.
- No "leetcoding" or unnecessary complexity is present.
