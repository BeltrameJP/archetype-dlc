# 02. Discovery & Epic Structure

## 🎯 Objective
Standardize the gathering of project context and the output of high-fidelity "Epics" to ensure maximum implementation accuracy.

## 🔄 The Discovery Ingestion Loop

Discovery is not a static step. It is a continuous loop of data gathering.

### Directives:
- **Source Synthesis:** Actively request and ingest data from multiple channels:
  - **Topics:** High-level subjects and domains.
  - **Links:** External documentation, API specs, and competitor research.
  - **Truth Sources:** The user's specific project goals and existing codebase.
  - **Conversations:** Direct iterative discussion with the user.
- **Ambiguity Detection:** Identify when sources conflict or lack detail. Pause to clarify before drafting an Epic.

## 📜 Mandatory Epic Structure (YAML)

All refined requirements must be summarized into "Epics" using the following YAML structure. This format ensures that even complex features are broken down into testable, implementation-ready definitions.

### YAML Template:
```yaml
epic:
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

## ✅ Validation
- The ingestion loop has consolidated all provided links and sources.
- Every feature has a corresponding Epic in the mandatory YAML format.
- Acceptance Criteria are specific, binary (true/false), and testable.
