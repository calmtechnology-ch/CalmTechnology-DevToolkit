# Living Project State: [Project Name]

> **CRITICAL AGENT INSTRUCTION**: This document represents the definitive current state of the project. Any AI assistant or developer must consult this file **FIRST** before suggesting, modifying, or deleting any code.

---

## 1. Project Metadata
- **Project Name**: [Project Name]
- **Current Version**: 0.1.0
- **Current Git Branch**: main
- **Last Known Commit Hash**: [commit-hash]
- **Active Development Phase**: [DEFINITION | ARCHITECTURE | IMPLEMENTATION | AUDIT | VALIDATION | RELEASE_READY]
- **Last Updated**: YYYY-MM-DD
- **Toolkit Version Used**: CalmTechnology-DevToolkit v0.1.0

---

## 2. Executive Status & Quality Gates
| Quality Gate | Title | Current Status | Last Evaluated | Evidence Document |
|---|---|---|---|---|
| **QG-01** | Definition Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | YYYY-MM-DD | `docs/REQUIREMENTS.md` |
| **QG-02** | Architecture Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | YYYY-MM-DD | `docs/ARCHITECTURE.md` |
| **QG-03** | Build Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | YYYY-MM-DD | Build console log |
| **QG-04** | Audit Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | YYYY-MM-DD | `docs/AUDIT_REPORT.md` |
| **QG-05** | Validation Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | YYYY-MM-DD | `docs/TEST_RESULTS.md` |
| **QG-06** | Release Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | YYYY-MM-DD | `docs/RELEASE_REPORT.md` |

---

## 3. Validated Features (Protected Against Modification)
*The following features have been implemented, audited, and empirically verified by passing test suites. They are **PROTECTED**. Do NOT modify or refactor the code paths supporting these features without an explicit user prompt and an approved non-regression plan.*

1. **[Feature 1 Name]** (Verified via `SYS-001`, `MAT-001` on commit [hash]):
   - Implemented in: `[file path]`
   - Behavior: [Description of verified behavior]
2. **[Feature 2 Name]** (Verified via `SYS-002` on commit [hash]):
   - Implemented in: `[file path]`
   - Behavior: [Description of verified behavior]

---

## 4. Unvalidated Features & In-Progress Work
*The following capabilities are implemented or partially implemented but have NOT yet passed full empirical verification.*

1. **[Capability A]**: [Status: Code written, pending hardware test `MAT-003`]
2. **[Capability B]**: [Status: Draft implementation in branch `feature/xxx`]

---

## 5. Active Known Issues & Blockers
*Summary of active defects from `docs/KNOWN_ISSUES.md`.*

| Issue ID | Severity | Status | Brief Description | Blocker For |
|---|---|---|---|---|
| `[ISSUE-001]` | [CRITICAL / HIGH / MED / LOW] | [OPEN / INVESTIGATING] | [Brief summary of defect] | [e.g., Gate QG-04] |

---

## 6. Recent Test Campaign Summary
- **Total Tests Cataloged**: [Count]
- **Passed**: [Count]
- **Failed**: [Count]
- **Blocked**: [Count]
- **Not Run**: [Count]
- **Not Applicable**: [Count]
- **Hardware Verified**: [YES / NO / PARTIAL]

---

## 7. Active Architectural Decisions
- `ADR-001`: [Title] (Status: ACCEPTED)
- `ADR-002`: [Title] (Status: ACCEPTED)

---

## 8. Protected Files & Directories
*Files that must NOT be touched without explicit user directive:*
- `[e.g., src/engine_core.cpp]` (Core stable engine)
- `[e.g., platformio.ini]` (Verified hardware configuration)

---

## 9. Recommended Next Action
> **NEXT IMMEDIATE STEP**: [Specify the single most logical, high-priority engineering task according to the active workflow, e.g., "Run hardware test suite MAT-001 to MAT-010 on physical CoreS3 device to complete Quality Gate QG-05."]
