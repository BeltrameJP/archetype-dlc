# 04. Validation & Review Setup

## 🎯 Objective
Establish the technical infrastructure and instruction set required for automated, high-fidelity code reviews within CI/CD pipelines.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)
- [05. Validation & Review](../best-practices/05-validation-and-review.md)

### 🛠️ Context & Tools
- Active Epics and Cards from Phase 01 and 02.
- Knowledge of the project's CI/CD environment (e.g., GitHub Actions, GitLab CI).
- List of preferred static analysis and security tools.

## 🛠️ Execution Steps

### 1. The CI/CD Setup Discussion
Initiate a feedback loop with the user. Ask if they wish to create a persistent `validation-instructions.md` file (or equivalent) for their CI/CD pipeline.

### 2. Context Linking
Collaborate with the user to define the "Source of Truth" for the pipeline agent.
- **Requirement:** Define how the agent will retrieve the Epic and Card data without the current terminal history.
- **Decision:** Will the data be stored in a specific folder, retrieved via API, or passed as environment variables?

### 3. Tooling Integration
Define the exact commands and flags for the pipeline's static analysis phase.
- **Linters:** (e.g., `eslint`, `pylint`).
- **Security Scans:** (e.g., `snyk`, `bandit`).
- **Test Execution:** Pointers to the verified commands in Best Practice 03.

### 4. Instruction File Generation
Draft the `validation-instructions.md` (or a session-local `tmp-validation-guide.md`) following the [Mandatory Structure](../best-practices/05-validation-and-review.md#mandatory-structure).

### 5. Final Approval ("The Done Gate")
Present the infrastructure plan and instruction file to the user. Do not finalize until receiving explicit approval.

## ✅ Validation
- A `validation-instructions.md` (or equivalent) exists and is verified by the user.
- The path to the Epic and Card context is clearly defined and accessible.
- The review commands are technical, objective, and match the project's environment.
