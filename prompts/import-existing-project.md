# Prompt: Import Existing Project

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Examine ce projet existant et initialise
sa documentation à partir du code réel.

Ne modifie aucun fichier source.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Import and Reconstruct Existing Codebase State

You are acting as the Lead Software Auditor and Systems Architect using the CalmTechnology-DevToolkit methodology.

## Mandatory Pre-Flight Instructions
1. Read the global operational rules in `CalmTechnology-DevToolkit/AGENTS.md`.
2. Follow the workflow defined in `CalmTechnology-DevToolkit/workflows/existing-project.md`.
3. Activate the skill `CalmTechnology-DevToolkit/skills/code-auditor/SKILL.md`.

## CRITICAL CARDINAL RULE
**DO NOT MODIFY ANY SOURCE CODE DURING THIS IMPORT PROCESS.**
Your sole objective is observation, audit, and reconstruction of project truth.

## Execution Instructions
1. **Examine Repository Structure**: Map all source files, headers, build files (`platformio.ini`, `CMakeLists.txt`, `package.json`, etc.), and existing documentation.
2. **Identify Real Version and Commit**:
   - Determine current version and commit hash from Git or package metadata.
   - Note if uncommitted local changes exist.
3. **Inspect Real Source Code**:
   - Read the implementation files. Distinguish between features actually implemented in code versus claims in README files.
   - Check what automated tests exist and whether they can be executed.
4. **Reconstruct Baseline Documentation in `docs/`**:
   - Create `docs/` if absent.
   - Author `docs/PROJECT.md` capturing the real architecture and platforms.
   - Author `docs/REQUIREMENTS.md` reverse-engineering baseline requirements (`REQ-F-xxx`) representing existing features.
   - Author `docs/ARCHITECTURE.md` documenting module boundaries and data flows.
   - Author `docs/DECISIONS.md` capturing historical architectural choices as ADRs.
   - Author `docs/KNOWN_ISSUES.md` cataloging bugs, gaps, and technical debt discovered during inspection.
   - Author `docs/TEST_PLAN.md` and `docs/TEST_RESULTS.md` listing existing tests initialized to `NOT_RUN` (unless verified during this session).
5. **Establish `docs/PROJECT_STATE.md`**:
   - Clearly list **Validated Features** (proven to work).
   - Clearly list **Unvalidated Features** (claimed but unverified).
   - Formulate a single, concrete, prioritized **Recommended Next Action**.

## Expected Response
- Executive summary of the codebase's true status.
- Summary of reconstructed documents created in `docs/`.
- Clear list of blind spots, missing tests, and unverified assumptions.
- Recommended immediate next engineering step.
```
