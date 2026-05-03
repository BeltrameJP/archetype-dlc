# 99. Project-Specific Best Practices (Template)

## 🎯 Objective
Define and enforce unique coding standards, architectural constraints, and library preferences specific to this project.

## 🛠️ Preferred Stack & Libraries
*List any specific libraries or tools that MUST be used, and those that should be avoided.*
- **Preferred:** (e.g., Axios for HTTP, Tailwind for CSS)
- **Avoid:** (e.g., Fetch API, Sass modules)

## 🏛️ Architectural Constraints
*Define the high-level structural rules for the project.*
- **Pattern:** (e.g., "Use Atomic Design for components," "Strict Hexagonal Architecture")
- **State Management:** (e.g., "Only use React Context for global state")

## 🔡 Naming & Style Conventions
*Specific naming patterns to be followed by the agent.*
- **Files:** (e.g., "kebab-case for all files")
- **Variables:** (e.g., "Use camelCase for variables, PascalCase for classes")
- **Types:** (e.g., "Always export interfaces with an 'I' prefix")

## 🚦 Logic & Behavioral Rules
*Unique logic constraints or business rules.*
- (e.g., "Every API endpoint must include rate-limiting middleware")
- (e.g., "Never use hardcoded strings for UI; use i18n keys")

## ✅ Verification
- The implementation follows the stack preferences.
- Architectural patterns are preserved.
- Naming conventions match the project standards.
