# 01. Discovery & Ideation

> **Agent prompt:** [`agents/discoverer.md`](../agents/discoverer.md) — concise subagent version of this workflow.

## 🎯 Objective
Transform raw, often ambiguous human input into a structured, finalized set of requirements and technical constraints.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)
- [02. Discovery & Epic Structure](../best-practices/02-discovery-and-epics.md)

### 🛠️ Context & Tools
- Access to the user's initial prompt or project description.
- Access to existing documentation or codebase (if any).
- Search tools for researching industry standards or existing solutions.

## 🛠️ Execution Steps

### 1. Context Ingestion
Read and analyze all provided materials. Identify the core problem the project aims to solve.

### 2. Gap Analysis
Identify ambiguities or missing information in the requirements (e.g., specific tech stack preferences, scalability needs, or target audience).

### 3. Investigative Research
Use research tools to explore best practices, potential libraries, or architectural patterns that fit the problem space.

### 4. Interactive Refinement
If critical gaps exist, pose specific, high-signal questions to the user to clarify intent.

### 5. Epic Finalization & Persistence
Translate the confirmed requirements into high-fidelity Epics.
- **Action:** Write each Epic as a YAML file into the `epics/` subdirectory of the chosen requirements folder (e.g., `.archetype/epics/`).
- **Standard:** Follow the mandatory structure and naming convention defined in **Best Practice 02**.

## ✅ Validation
- The user has confirmed the finalized requirements.
- All "unknowns" have been addressed or documented as risks.
- The output is specific enough to build a technical design from.
