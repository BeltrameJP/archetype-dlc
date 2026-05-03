# 01. Feedback Loop & Formatting

## 🎯 Objective
Establish a high-signal communication style, iterative refinement process, and token-efficient formatting standards for all agentic workflows.

## 🔄 The Iterative Feedback Loop (The "Done" Gate)

Agentic planning and design are not one-shot processes. They are collaborative conversations.

### Directives:
- **Discuss & Refine:** Present proposals as drafts. Explain the "Why" and invite critique.
- **The "Done" Gate:** You **MUST NOT** proceed from a planning phase to an execution phase until the user explicitly provides validation.
  - **Validation keywords:** "it's done", "it's good", "approved", "go ahead", "continue".
- **Course Correction:** If the user provides a hint or a correction, prioritize it as a scope adjustment and pivot your plan immediately.

## 📄 Data Formatting (YAML Priority)

Structured data should be clear, human-readable, and context-efficient.

### Directives:
- **YAML over JSON:** Always prefer YAML for structured data, requirements, configurations, and complex lists.
- **Why:** YAML eliminates unnecessary syntax noise (braces, brackets, excess quotes), leading to lower token consumption and better readability for the user.
- **Commenting:** Utilize YAML's support for inline comments to provide context for specific data points when necessary.

## 📊 Flow Visualization (Mermaid.js)

Complex logic and architectures are best understood visually.

### Directives:
- **Mandatory Mermaid:** Use Mermaid.js for illustrating state machines, sequence diagrams, architecture flows, and data relationships.
- **GitHub Compatibility:** Ensure all Mermaid diagrams are wrapped in standard markdown code blocks:
  ```mermaid
  graph TD;
      A-->B;
      B-->C;
  ```
- **Context Efficiency:** Keep diagrams focused on the high-level logic to avoid overwhelming the context with excessively large diagrams.

## ✅ Validation
- Proposals are met with a refinement loop before action.
- Structured data is formatted in clean, commented YAML.
- Complex flows are visualized using Mermaid blocks.
