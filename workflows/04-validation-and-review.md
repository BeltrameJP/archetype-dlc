# 04. Validation & Review

> **Agent prompt:** [`agents/reviewer.md`](../agents/reviewer.md) — concise subagent version of this workflow.

## 🎯 Objective
Verify the quality, security, and project alignment of implemented changes. This phase can be executed as a one-time **Manual Agentic Review** or as a **CI/CD Infrastructure Setup** for automated pipelines.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)
- [05. Validation & Review](../best-practices/05-validation-and-review.md)

### 🛠️ Context & Tools
- Active Epics, Cards, and **Project-Specific Rules (`project-rules.md`)**.
- Access to the target repository.
- Knowledge of the CI/CD environment (if setting up infrastructure).

## 🛠️ Execution Steps

### Choice 1: Manual Agentic Review
Follow this path if you are an agent performing a peer review of a recently completed task.
1.  **Context Ingestion:** Read the active Epic, Card, `project-rules.md`, and `git-workflow.md` (located in the requirements root).
2.  **Code Inspection:** Analyze the changes against the Acceptance Criteria and Project Rules.
3.  **Strict Review Output:** Output the review summary according to the [Review Protocol](../best-practices/05-validation-and-review.md#the-review-protocol).
4.  **Pull Request Draft:** If a Git Workflow is defined and the review is positive, generate a draft for the Pull Request based on the project's PR template.
5.  **User Approval for PR:** Ask the user: *"The review is complete. Would you like me to create the Pull Request now using the drafted template?"*
6.  **🛑 STOP:** Do NOT implement fixes. Do NOT ask for next steps beyond the PR creation. Stop immediately after the review or PR creation.

---

### Choice 2: CI/CD Infrastructure Setup
Follow this path to establish the technical set required for automated pipeline reviews.
1.  **Discussion:** Ask the user if they wish to create a persistent `validation-instructions.md`.
2.  **Context Linking:** Define how the pipeline agent will retrieve the Epic, Card, and `project-rules.md`.
3.  **Tooling Integration:** Define commands for linters, security scans, and test execution.
4.  **Instruction File Generation:** Draft the `validation-instructions.md` following the mandatory structure.
5.  **Final Approval:** Present the plan to the user and wait for explicit approval.

## ✅ Validation
- (Review) The agent provided a technical review and stopped without proposing implementation.
- (Setup) A `validation-instructions.md` exists and is verified by the user.
- The review/setup accounts for the project's custom rules (`project-rules.md`).
