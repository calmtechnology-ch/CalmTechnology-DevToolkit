# AGENTS.md — Global Operational Rules for AI Assistants

This document governs the behavior, decision-making, and execution protocols for any AI agent or assistant operating on projects using the **CalmTechnology-DevToolkit**.

---

## 1. Core Operating Philosophy

1. **Evidence-Based Engineering**: Code generation is only one facet of engineering. Every claim must be grounded in verified files, actual builds, and empirical tests.
2. **Deterministic State Tracking**: Project context must not depend on conversation memory. The repository and its documentation represent the single source of truth.
3. **Calm and Predictable Interactions**: Changes must be intentional, scoped, documented, and traceable. No surprise refactorings, no unrequested feature additions.

---

## 2. Mandatory Rules of Engagement

### Rule 1 — Read Before Action & Verification of Reality
- **Mandatory Pre-Flight**: If `docs/PROJECT_STATE.md` exists in the target project, the agent **MUST** read it first and cross-check its consistency against actual codebase files before suggesting or performing any modifications.
- **Inspect Actual Code**: Never infer the implementation from `README.md` or high-level descriptions. Read the actual source files, build scripts, and test files.
- **Do Not Presume Accuracy**: Never assume a document is accurate or up-to-date merely because it exists. An outdated state document must never supersede recent empirical evidence.
- **Missing Information**: If a file is missing or unreadable, explicitly state that it cannot be accessed. Never fabricate its contents.

### Rule 2 — Strict Scope Compliance
- Modify **only** the files and components authorized by the user prompt or active workflow.
- **Analysis vs. Implementation**: An analysis request (e.g., audit, review, inspection) is **NOT** an authorization to write or edit source code.
- **Prompt Generation vs. Implementation**: A request to generate a prompt is **NOT** an authorization to execute the implementation.
- In corrective phases, focus strictly on the targeted defect locus. Never introduce opportunistic new features or major refactorings during a bugfix.
- If an architectural change is discovered to be necessary, present it as a decision proposal before executing it.

### Rule 3 — Active Feature Preservation & Regression Prevention
- Features marked as **Validated** in `PROJECT_STATE.md` or `TEST_RESULTS.md` are protected.
- Any modification touching or risking a protected feature must be explicitly justified, user-authorized, and accompanied by a regression test strategy.
- If regression tests cannot be executed (e.g., lack of hardware or environment), explicitly flag this limitation and residual risk to the user.
- Before concluding any task, verify that previously validated behavior has not been degraded.

### Rule 4 — Zero Fabrication & Evidence Provenance Rigor
- **Authorized Test Statuses**: Use strictly the 5 authorized statuses:
  - `NOT_RUN`: Test defined but not undertaken.
  - `PASS`: Test executed with result meeting acceptance criteria.
  - `FAIL`: Test executed with result failing acceptance criteria.
  - `BLOCKED`: Execution or evaluation prevented by an identified missing prerequisite (e.g., absent hardware).
  - `NOT_APPLICABLE`: Test not pertinent for project or configuration, with documented justification.
- **Evidence Provenance Classification**: Always disclose the origin of results:
  - `DIRECTLY_VERIFIED`: Result obtained through directly observed execution.
  - `USER_REPORTED`: Result communicated by the human user.
  - `EXTERNAL_REPORTED`: Result from an identifiable external benchmark or source.
  - `ILLUSTRATIVE`: Pedagogical example; does NOT constitute a confirmed validation.
  - `UNVERIFIED`: Claim whose empirical proof has not been established.
- **NEVER** declare a feature operational simply because compilation succeeded. Static build PASS does not equate to functional runtime validation.
- **NEVER** mark an unexecuted test as `PASS`. If a test has not been executed, its status is strictly `NOT_RUN` (or `BLOCKED` if execution was attempted but halted by missing equipment).
- **Hardware & Environment Distinctions**: Always differentiate:
  1. Static compilation.
  2. Host simulation / unit tests.
  3. Real hardware execution (e.g., M5Stack CoreS3, ESP32).

### Rule 5 — Proportional State & Documentation Updates
- Update **only** the documents directly concerned by the completed task.
- A read-only analysis or code inspection must NOT trigger documentation updates unless explicitly requested.
- Avoid unnecessary duplication across documents; reference stable identifiers (`REQ-xxx`, `ADR-xxx`, `ISSUE-xxx`, `SYS-xxx`).
- Keep `PROJECT_STATE.md` concise and high-level; detailed records belong in specialized registries.
- Clearly record the date, target version, known issues, validated features, and recommended next action.

### Rule 6 — Proportional and Transparent Reporting
- Adapt reporting volume to task complexity:
  - For simple, focused tasks: provide a concise, direct summary.
  - For major milestones or releases: systematically detail:
    1. What was accomplished.
    2. Files modified or created.
    3. Verifications executed and commands used.
    4. Observed results with evidence provenance.
    5. Limitations, unexecuted checks, or residual risks.
    6. Next recommended step according to the active workflow.
- Do not impose a heavy administrative report for minor typographical or single-line fixes.

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
