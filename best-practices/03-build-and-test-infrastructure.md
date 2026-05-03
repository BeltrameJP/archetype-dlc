# 03. Build & Test Infrastructure

## 🎯 Objective
Ensure a reliable, documented interface for building and testing the project, preventing command-line hallucinations and environment-specific failures.

## 🛑 The "No Guessing" Mandate

You **MUST NOT** attempt to guess build or test commands. Before executing Phase 02 (Architecture) or Phase 04 (Implementation), you must have a confirmed "Source of Truth" for the project's infrastructure.

## 🔄 User-Guided Discovery

If the project lacks explicit build/test documentation (e.g., in `README.md` or a specialized file), follow this process:

1.  **Identify Existing Assets:** First, ask the user if dedicated build/test instruction files already exist and, if so, to point to their locations.
2.  **Halt & Inquire (If Missing):** If no files exist, stop all execution and ask the user for the following:
    - The core tech stack and versioning requirements.
    - The location of the primary configuration files (e.g., `package.json`, `Cargo.toml`, `.env`).
    - The exact commands for building and running specific test suites (Unit, Integration, E2E).
3.  **Targeted Verification:** Only after receiving user input, perform a surgical read of the identified configuration files to verify arguments and scripts.
4.  **Instruction Persistence Choice:** If the agent gathered the data in step 2, ask the user if they would like to store these instructions **permanently** in the repository (e.g., `build-instructions.md`, `test-instructions.md`) or as a session-only **temporary** guide (`tmp-build-test-guide.md`).
5.  **Initialize Guide:** Create/Point to the file(s) based on the user's choice, adhering strictly to the [Mandatory Structure](#mandatory-structure).

## 🧠 Memory & Resilience (The Guide)

Whether stored permanently or as a `tmp-build-test-guide.md`, build and test instructions **MUST** follow this 4-part structure to ensure clarity and error recovery:

### 📋 Mandatory Structure:
1.  **Prerequisites:** List all required global tools (versions), environment variables, and local configuration files (e.g., `.env`, `credentials.json`) needed before execution.
2.  **Execution Steps:** The exact, sequential, and numbered commands to be run in the terminal.
3.  **Verification of Success:** Specific, observable indicators that the process completed successfully (e.g., "Exit code 0", "Presence of `dist/` folder", "Log output contains 'Build Success'").
4.  **Troubleshooting:** A list of known issues, common error messages, and their corresponding resolutions.

### YAML Metadata Template (Optional):
```yaml
infrastructure_guide:
  type: "build | test"
  prerequisites:
    - "Tool X version Y"
    - "Env var Z"
  steps:
    - "command 1"
  success_indicators:
    - "Condition A"
  common_errors:
    - error: "Message B"
      fix: "Action C"
```

## 🛠️ Directives
- **Infrastructure First:** This guide must be established **before** any architectural planning or code implementation.
- **Context Preservation:** Always read the `tmp-build-test-guide.md` at the start of every turn during Phase 02 and Phase 03.
- **User Authority:** The user's input regarding commands overrides any "standard" library behavior you might expect.

## ✅ Validation
- A `tmp-build-test-guide.md` or equivalent project-native documentation exists.
- Commands listed in the guide have been confirmed by the user.
- The guide is used to drive the TDD/Atomic implementation loops.
on loops.
