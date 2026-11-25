# Release Evaluation Report: [Project Name]

## 1. Executive Summary & Verdict
- **Project Name**: [Project Name]
- **Target Release Version**: 0.1.0
- **Evaluated Commit Hash**: [commit-hash]
- **Evaluation Date**: YYYY-MM-DD
- **Lead Reviewer**: [Skill: `release-reviewer`]

### Formal Release Decision
> ### **VERDICT: [GO | CONDITIONAL_GO | NO_GO | INSUFFICIENT_EVIDENCE]**

#### Decision Justification
*State clearly the empirical reasons for this verdict, referencing Quality Gates, test coverage, defect counts, and hardware verification status.*

---

## 2. Quality Gates Status Summary
| Gate | Name | Evaluation | Primary Evidence |
|---|---|---|---|
| **QG-01** | Definition Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | `docs/REQUIREMENTS.md` |
| **QG-02** | Architecture Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | `docs/ARCHITECTURE.md`, `docs/DECISIONS.md` |
| **QG-03** | Build Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | Clean compiler logs |
| **QG-04** | Audit Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | `docs/AUDIT_REPORT.md` (0 Critical/High issues) |
| **QG-05** | Validation Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | `docs/TEST_RESULTS.md` |
| **QG-06** | Release Ready | [PASS / FAIL / BLOCKED / NOT_EVALUATED / NOT_APPLICABLE] | `docs/RELEASE_CHECKLIST.md` |

---

## 3. Test Coverage & Empirical Evidence Summary
- **Total Test Cases**: [Total]
- **Passed**: [Count]
- **Failed**: [Count]
- **Blocked**: [Count]
- **Not Run**: [Count]
- **Not Applicable**: [Count]
- **Evidence Provenance**: [DIRECTLY_VERIFIED / USER_REPORTED / EXTERNAL_REPORTED / ILLUSTRATIVE / UNVERIFIED]
- **Hardware Acceptance Tests (`MAT-xxx`)**: [VERIFIED ON REAL HARDWARE / NOT_RUN / BLOCKED / SIMULATED ONLY]

> *Note: For embedded releases, absence of physical hardware validation strictly prohibits a definitive `GO` verdict.*

---

## 4. Defect Registry & Known Limitations
*List of open issues and transparent limitations disclosed to end users:*
1. `[ISSUE-xxx]`: [Description, severity, and approved workaround].
2. [Platform Limitation]: [e.g., WiFi reconnection timeout is 10s].

---

## 5. Draft Public Release Notes
*The following draft is prepared for publication upon human authorization:*

### [Project Name] v0.1.0
#### Highlights
- [Highlight 1]
- [Highlight 2]

#### Validated Capabilities
- [Capability 1]
- [Capability 2]

#### Known Limitations & Workarounds
- [Disclosed issue or boundary]

---

## 6. Action Items & Developer Next Steps
- [ ] [e.g., Human developer executes hardware verification on CoreS3 board].
- [ ] [e.g., Human developer signs git tag `v0.1.0`].
- [ ] [e.g., Human developer publishes GitHub release].
