# Engineering Workflows Catalog

This directory contains the 7 standardized development workflows of the **CalmTechnology-DevToolkit**. Each workflow defines an end-to-end lifecycle process with clear entry criteria, sequential phases, quality gates, and exit criteria.

---

## Workflow Matrix

| Workflow File | Target Scenario | Primary Skills Involved | Key Deliverables |
|---|---|---|---|
| [`new-project.md`](new-project.md) | Starting a project from idea to MVP. | `project-definition`, `software-architect`, `embedded-engineer`, `test-engineer` | `PROJECT.md`, `REQUIREMENTS.md`, `ARCHITECTURE.md`, `DECISIONS.md`, `PROJECT_STATE.md` |
| [`existing-project.md`](existing-project.md) | Importing an un-documented or brownfield codebase. | `code-auditor`, `project-definition`, `software-architect` | Reconstructed `PROJECT_STATE.md`, `REQUIREMENTS.md`, gap analysis |
| [`feature-development.md`](feature-development.md) | Adding a new capability to an existing system. | `project-definition`, `software-architect`, `prompt-generator`, `test-engineer` | Scoped prompt, implementation, updated test matrix |
| [`code-audit.md`](code-audit.md) | Comprehensive code inspection and debt audit. | `code-auditor`, `embedded-engineer`, `release-reviewer` | `AUDIT_REPORT.md`, updated `KNOWN_ISSUES.md` |
| [`corrective-release.md`](corrective-release.md) | Diagnosing and fixing a reported defect. | `code-auditor`, `prompt-generator`, `test-engineer` | `CORRECTIVE_PLAN.md`, targeted fix, `REG-xxx` tests |
| [`regression-testing.md`](regression-testing.md) | Comprehensive non-regression campaign. | `test-engineer`, `embedded-engineer` | `TEST_RESULTS.md`, non-regression confirmation |
| [`public-release.md`](public-release.md) | Formal Go/No-Go release gate evaluation. | `release-reviewer`, `test-engineer` | `RELEASE_CHECKLIST.md`, `RELEASE_REPORT.md` |

---

## Quality Gate Integration

Workflows systematically transition projects through the 6 Quality Gates defined in [`docs/QUALITY_GATES.md`](../docs/QUALITY_GATES.md):
- **QG-01 (Definition Ready)**: Requirements and acceptance criteria formal.
- **QG-02 (Architecture Ready)**: Component boundaries, interfaces, and ADRs documented.
- **QG-03 (Build Ready)**: Clean compilation across applicable platforms.
- **QG-04 (Audit Ready)**: Source code inspected, no unhandled defects.
- **QG-05 (Validation Ready)**: Test suite and hardware acceptance executed.
- **QG-06 (Release Ready)**: Final release criteria satisfied or limitations documented.
