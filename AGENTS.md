# AGENTS.md — Global Operational Rules for AI Assistants

This document governs the behavior, decision-making, and execution protocols for any AI agent or assistant operating on projects using the **CalmTechnology-DevToolkit**.

---

## 1. Core Operating Philosophy

1. **Evidence-Based Engineering**: Code generation is only one facet of engineering. Every claim must be grounded in verified files, actual builds, and empirical tests.
2. **Deterministic State Tracking**: Project context must not depend on conversation memory. The repository and its documentation represent the single source of truth.
3. **Calm and Predictable Interactions**: Changes must be intentional, scoped, documented, and traceable. No surprise refactorings, no unrequested feature additions.

---

## 2. Mandatory Rules of Engagement

### Rule 1 — Read Before Action
- **Mandatory Pre-Flight**: If `docs/PROJECT_STATE.md` exists in the target project, the agent **MUST** read it before suggesting or performing any modifications.
- **Inspect Actual Code**: Never infer the implementation from `README.md` or high-level descriptions. Read the actual source files, build scripts, and tests.
- **Missing Information**: If a file is missing or unreadable, explicitly state that it cannot be accessed. Never fabricate its contents.

### Rule 2 — Strict Scope Compliance
- Modify **only** the files and components authorized by the user prompt or active workflow.
- In corrective phases, focus strictly on the targeted defect. Never introduce opportunistic new features or major refactorings during a bugfix.
- If an architectural change is discovered to be necessary, present it as a decision proposal before executing it.

### Rule 3 — Active Feature Preservation & Regression Prevention
- Features marked as **Validated** in `PROJECT_STATE.md` or `TEST_RESULTS.md` are protected.
- Never modify existing working code without explicit architectural justification and a corresponding regression test plan.
- Before concluding any task, verify that previously validated behavior has not been degraded.

### Rule 4 — Zero Fabrication of Test Results
- **NEVER** declare a feature operational simply because compilation succeeded.
- **NEVER** mark an unexecuted test as `PASS`. If a test has not been executed, its status is strictly `NOT_RUN`.
- **Hardware & Environment Distinctions**: Always differentiate:
  1. Static compilation.
  2. Host simulation / unit tests.
  3. Real hardware execution (e.g., M5Stack CoreS3, ESP32).
- When recording user feedback or external test reports, record them as *user-reported*, without claiming direct autonomous observation.

### Rule 5 — Explicit State and Version Management
- When a task completes, update `PROJECT_STATE.md` and related documents (`REQUIREMENTS.md`, `TEST_RESULTS.md`, `KNOWN_ISSUES.md`).
- Clearly mark the date, target version, known issues, validated features, and recommended next action.
- Distinguish obsolete decisions from active decisions using Architecture Decision Records (`DECISIONS.md`).

### Rule 6 — Transparent Reporting
- At the end of every turn or task, explicitly list:
  1. What was accomplished.
  2. What was intentionally omitted or left pending.
  3. Decisions requiring user approval.
  4. The next recommended step according to the active workflow.

---

## 3. Toolkit Navigation Map

When assisting a developer, select the appropriate skill and workflow based on the task:

| Lifecycle Phase | Relevant Skill | Active Workflow | Primary Documents |
|---|---|---|---|
| Project Initialization | `skills/project-definition` | `workflows/new-project.md` | `PROJECT.md`, `REQUIREMENTS.md` |
| System Design | `skills/software-architect` | `workflows/new-project.md` | `ARCHITECTURE.md`, `DECISIONS.md` |
| Embedded Hardware Alignment | `skills/embedded-engineer` | `profiles/cores3.md`, `esp32.md` | `ARCHITECTURE.md`, `PROJECT_STATE.md` |
| UI & Interaction Design | `skills/ui-designer` | `profiles/web-application.md`, etc. | Component specs, interaction states |
| Prompt Formulation | `skills/prompt-generator` | `workflows/feature-development.md` | Scoped development prompts |
| Source Code Audit | `skills/code-auditor` | `workflows/code-audit.md` | `AUDIT_REPORT.md`, `KNOWN_ISSUES.md` |
| Verification & Testing | `skills/test-engineer` | `workflows/regression-testing.md` | `TEST_PLAN.md`, `TEST_RESULTS.md` |
| Release Preparation | `skills/release-reviewer` | `workflows/public-release.md` | `RELEASE_CHECKLIST.md`, `RELEASE_REPORT.md` |

---

## 4. Manual Fallback Procedure

If the AI environment does not automatically execute skills via tools or subagents:
1. Provide the agent with the exact path to the required `SKILL.md` (e.g., `skills/embedded-engineer/SKILL.md`).
2. Instruct the agent: *"Adopt the role and follow the execution procedure defined in this skill file."*
3. Provide the active project documents from `docs/`.
4. Enforce output formatting according to the skill's `Expected outputs` section.
