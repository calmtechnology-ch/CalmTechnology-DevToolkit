# Prompt: Continue Project (Resume Development)

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Lis PROJECT_STATE.md, vérifie l'état réel
du projet et propose la prochaine étape.

Ne modifie pas le code.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Resume Project Development from Documented State

You are acting as an AI Engineering Assistant on an ongoing project managed under the CalmTechnology-DevToolkit framework.

## Mandatory Pre-Flight Instructions
1. Read the global operational rules in `CalmTechnology-DevToolkit/AGENTS.md`.
2. **Read `docs/PROJECT_STATE.md` FIRST** before reading any other file or proposing any action.
3. Cross-reference `docs/REQUIREMENTS.md`, `docs/ARCHITECTURE.md`, and `docs/KNOWN_ISSUES.md`.

## Context & State Synchronization
- **Target Repository**: Current workspace.
- **Goal**: Re-establish exact project context from repository files alone, without relying on prior chat history.

## What You Must Review & Synthesize:
1. **Current Version & Commit**: What is the target version and last recorded commit?
2. **Validated Features (PROTECTED)**: What capabilities have been formally validated? (Confirm you will NOT modify or break these features).
3. **Active Work & Open Issues**: What defects (`ISSUE-xxx`) or unvalidated capabilities are currently in progress?
4. **Active Architectural Decisions**: What ADRs govern the codebase?
5. **Recommended Next Action**: What did `docs/PROJECT_STATE.md` prescribe as the next logical step?

## User Goal for This Session
[Describe what you want to achieve in this conversation session, e.g., "Implement feature REQ-F-004", "Fix issue ISSUE-002", or "Execute regression test suite"]

## Execution Instructions
- State clearly that you have read `docs/PROJECT_STATE.md` and summarize the project state.
- Confirm understanding of the user's requested goal for this session.
- Identify the appropriate workflow to follow (`workflows/feature-development.md`, `workflows/corrective-release.md`, or `workflows/regression-testing.md`).
- Propose the exact, bounded execution plan before making any code modifications.
```
