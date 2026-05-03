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

All refined requirements must be summarized into "Epics" using the following YAML structure.

### YAML Template:
```yaml
epic:
  id: "EPIC-001"
  title: "Example: Authentication System"
  user_story: |
    As a [user type], 
    I want [action/capability] 
    so that [specific benefit/value].
  goal: "The overarching business or technical objective of this epic."
  feature_details:
    - "Functional requirement 1"
    - "UI/UX expectation or interaction detail"
  tech_details:
    - "Required libraries or frameworks"
    - "Architectural constraints or patterns to follow"
    - "Security considerations"
  acceptance_criteria: # !! MOST CRITICAL FIELD - MUST BE EXHAUSTIVE !!
    - "Condition 1: [Input] results in [Output/Behavior] (e.g., Valid credentials return JWT)"
    - "Condition 2: [Edge Case] is handled by [Action] (e.g., SQL injection characters in login field are sanitized)"
    - "Condition 3: [Failure Mode] triggers [Error] (e.g., 3 failed attempts lock account for 5 mins)"
    - "All criteria must be translated into failing tests before implementation (TDD)."
  attachments:
    - name: "Logic Flow"
      link: "Link to Mermaid diagram or local file"
    - name: "Reference Doc"
      link: "External URL"
```

## 📇 Mandatory Card Structure (YAML)

Epics are broken down into atomic "Cards". Each card must be self-contained and provide enough context for an implementation agent to execute without reading the entire Epic.

### YAML Template:
```yaml
card:
  id: "CARD-001"
  epic_id: "EPIC-001" # Reference to the parent Epic
  title: "Description of the atomic task"
  description: |
    Detailed explanation of what needs to be implemented.
    Includes business logic, patterns to follow, and architectural constraints.
  dependencies:
    - "CARD-000" # List IDs of cards that must be completed first
  acceptance_criteria: # Inherited or specialized from the Epic
    - "Condition 1: [Behavior]"
    - "Condition 2: [Result]"
  status: "todo | in-progress | done" # Initial state is usually todo
```

## ✅ Validation
- The ingestion loop has consolidated all provided links and sources.
- Every feature has a corresponding Epic and set of Cards in the mandatory YAML format.
- Epics and Cards are stored in the chosen requirements directory of the target project.
- Acceptance Criteria are specific, binary (true/false), and testable.
