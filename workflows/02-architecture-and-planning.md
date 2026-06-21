# 02. Architecture & Planning

> **Agent prompt:** [`agents/architect.md`](../agents/architect.md) — concise subagent version of this workflow.

## 🎯 Objective
Translate structured requirements into a technical roadmap, architectural design, and a granular task list.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)
- [02. Discovery & Epic Structure](../best-practices/02-discovery-and-epics.md)
- [03. Build & Test Infrastructure](../best-practices/03-build-and-test-infrastructure.md)

### 🛠️ Context & Tools
- Finalized Epics in the chosen `epics/` directory.
- Understanding of the target tech stack (if decided).
- Access to project scaffolding tools.

## 🛠️ Execution Steps

### 1. Architectural Design
Define the high-level structure: system components, data flow, API contracts, and database schema.

### 2. Epic Refinement
Update existing Epics in the `epics/` directory if the technical design reveals new constraints or requirements.

### 3. Card Breakdown & Persistence
Break Epics down into atomic "Cards".
- **Action:** Write each Card as a YAML file into the `cards/` subdirectory of the chosen requirements folder.
- **Rule:** Each task must be small enough for an agent to execute in 1-3 turns without losing context.
- **Rule:** Each task must have clear "Definition of Done" and follow the mandatory Card structure.

### 4. Technical Refinement
For each task, identify potential technical hurdles, required dependencies, and the testing strategy.

### 5. Roadmap Sequencing
Organize tasks into a logical order of execution, respecting dependencies.

## ✅ Validation
- A technical design document exists.
- The task list is granular and stored persistently in the chosen `cards/` directory.
- The implementation plan is approved by the user.
