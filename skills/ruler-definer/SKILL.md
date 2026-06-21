---
name: ruler-definer
description: Creates or updates .agents/project-rules.md by interviewing the user about their project's coding standards, library preferences, and architectural constraints.
level: 1
---

# Ruler-Definer Skill

## When to load

Load this skill when the user says:
- "I want to set up / update project rules"
- "Run the ruler-definer"
- "Define constraints for this project"
- "Configure our coding standards"

## What it does

This skill delegates to the `ruler-definer` subagent which:
1. Checks if `.agents/project-rules.md` exists
2. Interviews the user section by section (stack, constraints, naming, logic rules, verification)
3. Writes the populated YAML to `.agents/project-rules.md`
4. Reports the result

## Invocation

```
task subagent_type: "ruler-definer", prompt: "Run the ruler-definer workflow for this project"
```
