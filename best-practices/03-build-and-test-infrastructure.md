# 03. Build & Test Infrastructure

## 🎯 Objective
Ensure a reliable, documented interface for building and testing the project, preventing command-line hallucinations and environment-specific failures.

## 🛑 The "No Blind Guessing" Mandate

You **MUST NOT** attempt to guess build or test commands without evidence. However, you should not force the user to provide exact commands for standard tech stacks. Instead, follow the **"Analyze & Suggest"** protocol.

## 🔄 Proactive Infrastructure Discovery

If the project lacks explicit build/test documentation (e.g., in `README.md` or a specialized file), follow this process:

1.  **Stack Analysis:** Explicitly scan the project root for common configuration files (e.g., `package.json`, `go.mod`, `Cargo.toml`, `requirements.txt`, `pom.xml`, `Makefile`).
2.  **Proactive Suggestion:** Based on the identified files, **propose** a set of standard build and test commands to the user.
    - *Example:* "I've detected a `package.json` file. I suggest using `npm run build` and `npm run test`. Do you approve these, or should I use different commands?"
3.  **Halt & Inquire (Only if Ambiguous):** If no standard files are found or the stack is obscure, stop and ask the user for:
    - The core tech stack and versioning requirements.
    - The exact commands for building and running test suites.
4.  **Targeted Verification:** Perform a surgical read of the configuration files to verify that the suggested scripts actually exist.
5.  **Instruction Persistence:** Ask the user if they would like to store these instructions **permanently** (e.g., `build-instructions.md`, `test-instructions.md`) or as a session-only **temporary** guide (`tmp-build-test-guide.md`).
6.  **Initialize Guide:** Create/Point to the file(s) based on the user's choice, adhering strictly to the [Mandatory Structure](#mandatory-structure).

## 🧠 Memory & Resilience (The Guide)

Whether stored permanently or as a `tmp-build-test-guide.md`, build and test instructions **MUST** follow this 4-part structure to ensure clarity and error recovery:

### 📋 Mandatory Structure:
1.  **Prerequisites:** List all required global tools (versions), environment variables, and local configuration files (e.g., `.env`, `credentials.json`) needed before execution.
2.  **Execution Steps:** The exact, sequential, and numbered commands to be run in the terminal.
3.  **Verification of Success:** Specific, observable indicators that the process completed successfully (e.g., "Exit code 0", "Log output contains 'Build Success'").
4.  **Troubleshooting:** A list of known issues and common errors.

## 🛠️ Directives
- **Informed Suggestions:** Always lead with a suggestion if a standard stack is detected.
- **User Authority:** The user's approval or custom input always overrides your suggestions.
- **Context Preservation:** Always read the `tmp-build-test-guide.md` (or permanent equivalent) at the start of every implementation turn.

## ✅ Validation
- The agent performed a stack scan before asking the user for commands.
- The agent provided proactive suggestions if common config files were found.
- A verified instruction file (Permanent or Temporary) exists and follows the 4-part structure.
