# 02. Architecture & Planning

## 🎯 Objective
Translate structured requirements into a technical roadmap, architectural design, and a granular task list.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)
- [03. Build & Test Infrastructure](../best-practices/03-build-and-test-infrastructure.md)

### 🛠️ Context & Tools
- Finalized requirements from Phase 01.
- Understanding of the target tech stack (if decided).
- Access to project scaffolding tools.

## 🛠️ Execution Steps

### 1. Architectural Design
Define the high-level structure: system components, data flow, API contracts, and database schema.

### 2. Epic Creation
Group requirements into logical "Epics"—broad categories of functionality (e.g., "Authentication System", "Data Visualization Engine").

### 3. Card Breakdown (Task Atomicization)
Break Epics down into "Cards" or "Tasks".
- **Rule:** Each task must be small enough for an agent to execute in 1-3 turns without losing context.
- **Rule:** Each task must have clear "Definition of Done".

### 4. Technical Refinement
For each task, identify potential technical hurdles, required dependencies, and the testing strategy.

### 5. Roadmap Sequencing
Organize tasks into a logical order of execution, respecting dependencies.

## ✅ Validation
- A technical design document exists.
- The task list is granular and contains no ambiguous "mega-tasks".
- The implementation plan is approved by the user.
