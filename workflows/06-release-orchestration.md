# 06. Release Orchestration

> **Agent prompt:** [`agents/releaser.md`](../agents/releaser.md) — concise subagent version of this workflow.

## 🎯 Objective
Safely transition the verified code to the production environment and document the release.

## 📋 Pre-requisites
### 🔴 Mandatory Best Practices
- [00. Core Mandates](../best-practices/00-core-mandates.md)
- [01. Feedback Loop & Formatting](../best-practices/01-feedback-and-formatting.md)

### 🛠️ Context & Tools
- Verified build from Phase 05.
- Release permissions/keys.
- Access to versioning tools.

## 🛠️ Execution Steps

### 1. Versioning
Apply Semantic Versioning (SemVer). Update `package.json`, `VERSION` files, or Git tags accordingly.

### 2. Changelog Generation
Automatically generate or curate a `CHANGELOG.md` highlighting new features, bug fixes, and breaking changes.

### 3. Production Deployment
Trigger the production deployment pipeline. Monitor logs and health checks during the rollout.

### 4. Post-Release Verification
Run a final smoke test in production to confirm availability and critical functionality.

### 5. Cleanup
Delete merged feature branches and archive old release artifacts if necessary.

## ✅ Validation
- The production environment is healthy.
- The new version is correctly tagged in Git.
- The CHANGELOG reflects the actual changes in this release.
