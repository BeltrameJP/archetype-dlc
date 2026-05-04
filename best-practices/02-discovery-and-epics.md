# 02. Discovery & Epic Structure

## 🎯 Objective
Standardize the gathering of project context and the output of high-fidelity "Epics" to ensure maximum implementation accuracy.

## 🔄 The Discovery Ingestion Loop

Discovery is not a static step. It is a continuous loop of data gathering that **must** align with the project's [VISION.md](../workflows/00-bootstrap-and-setup.md#2-vision--goals-definition).

### Directives:
- **Vision Alignment:** Before drafting any Epics, ensure the requirements align with the project's Mission and Core Objectives.
- **Source Synthesis:** Actively request and ingest data from multiple channels:
  - **Topics:** High-level subjects and domains.
  - **Links:** External documentation, API specs, and competitor research.
  - **Truth Sources:** The user's specific project goals and existing codebase.
  - **Conversations:** Direct iterative discussion with the user.
- **Ambiguity Detection:** Identify when sources conflict or lack detail. Pause to clarify before drafting an Epic.

## 📂 Project Storage Structure

To ensure requirements are persistent for the Implementation Loop and accessible to CI/CD agents, all Epics and Cards must be stored physically in the target project repository.

### Directives:
- **Root Directory:** Choose a dedicated folder in the project root to store requirements (e.g., `.archetype/`, `docs/requirements/`, or similar). 
- **User Preference:** Ask the user for their preferred folder name before creating the directory.
- **Subdirectories:** 
  - `epics/` within the chosen root for high-level requirements.
  - `cards/` within the chosen root for atomic implementation tasks.
- **File Format:** All files **MUST** be written in pure YAML format for token efficiency and readability.
- **Naming Convention:**
  - Epics: `EPIC-[ID]-[Title-Slug].yaml` (e.g., `EPIC-001-authentication.yaml`).
  - Cards: `CARD-[ID]-[Title-Slug].yaml` (e.g., `CARD-001-login-form.yaml`).

## 📜 Mandatory Epic Structure (YAML)

All refined requirements must be summarized into "Epics" using the mandatory structure.

- **Template:** [templates/epic.yaml](../templates/epic.yaml)

## 📇 Mandatory Card Structure (YAML)

Epics are broken down into atomic "Cards". Each card must be self-contained and provide enough context for an implementation agent to execute without reading the entire Epic.

- **Template:** [templates/card.yaml](../templates/card.yaml)

## ✅ Validation
- The ingestion loop has consolidated all provided links and sources.
- Every feature has a corresponding Epic and set of Cards in the mandatory YAML format.
- Epics and Cards are stored in the chosen requirements directory of the target project.
- Acceptance Criteria are specific, binary (true/false), and testable.
