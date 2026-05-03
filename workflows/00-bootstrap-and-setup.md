# 00. Bootstrap & Setup

## 🎯 Objective
Initialize an existing repository with the Archetype standards, making it "Agent-Ready" by establishing persistent requirements storage, behavioral guardrails, and environment documentation.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)

### 🛠️ Context & Tools
- An existing project repository.
- Access to global `archetype-dlc` repository content.

## 🛠️ Execution Steps

### 1. Pre-flight Idempotency Check
Before creating any files, the agent must check if an Archetype setup already exists.
- **Scan:** Search for `ARCHETYPE.md` or a requirements root directory (e.g., `.archetype/`).
- **If Found:** Halt and inform the user. Ask for a decision:
  - **Update:** Keep existing `VISION.md`, Epics, and Cards. Only overwrite the local `best-practices/` with the latest global versions. Proceed to Step 4.
  - **Hard Reset:** Delete the existing requirements folder and `ARCHETYPE.md`, then proceed from Step 2.
  - **Abort:** Exit the workflow without making changes.

### 2. Requirements Folder Initialization
Ask the user for their preferred folder name to store requirements (default: `.archetype/`).
- **Action:** Create the chosen root folder.
- **Action:** Create `epics/`, `cards/`, and `best-practices/` subdirectories within that root.

### 3. Vision & Goals Definition
Conduct a "Vision Interview" with the user to establish the project's long-term direction.
- **Action:** Ask about the project's mission, core objectives, and target audience.
- **Action:** Create a `VISION.md` file in the root of the chosen requirements folder (e.g., `[chosen-root]/VISION.md`).
- **Standard Structure:**
  - **Mission Statement:** A concise "Why this project exists."
  - **Core Objectives:** Measurable outcomes for success.
  - **Target Audience:** Who the users are.
  - **Non-Goals:** Boundaries of the project to prevent scope creep.

### 4. Localize Core Mandates (Direct Copy)
To ensure the project is self-contained and resilient:
- **Action:** Copy the content of `best-practices/00-core-mandates.md` and `best-practices/01-feedback-and-formatting.md` from the global `archetype-dlc` repo.
- **Action:** Copy `best-practices/99-custom-rules-template.md` and save it as `[chosen-root]/best-practices/99-project-rules.md`.
- **Action:** Save them into the local `[chosen-root]/best-practices/` directory.
- **The Custom Rules Prompt:** Notify the user: *"I've initialized `99-project-rules.md`. Do you have any specific project rules or preferred libraries you want to add now, or should we leave it as a template for later?"*

### 5. Infrastructure & Environment Setup
Execute the logic from **Best Practice 03 (Build & Test Infrastructure)**.
- **Action:** Ask the user if `build-instructions.md` and `test-instructions.md` exist.
- **Action:** Create verified, structured instruction files (Permanent or Temporary as per user choice).

### 6. Validation Setup
Execute the logic from **Best Practice 05 (Validation & Review)**.
- **Action:** Ask the user if they wish to initialize `validation-instructions.md` for CI/CD automation.

### 7. Project Indexing
Create a root `ARCHETYPE.md` file in the project to serve as a manifest.
- **Action:** Include a brief overview of the 6-phase Development Life Cycle.
- **Action:** Provide relative links to the local requirements folder, instruction files, vision, and mandates.

## ✅ Validation
- The agent explicitly checked for existing setups before proceeding.
- If a setup was found, the user's choice (Update/Reset) was confirmed and executed.
- The chosen requirements directory structure exists.
- A `VISION.md` file is created (or preserved) and approved.
- Core mandates are localized in the project.
- `build-instructions.md` and `test-instructions.md` follow the mandatory 4-part structure.
- A root `ARCHETYPE.md` manifest is present and correctly linked.
