# Living Project State: CoreS3-RuleBot

> **CRITICAL AGENT INSTRUCTION**: Consult this document FIRST before touching any code.

---

## 1. Project Metadata
- **Project Name**: CoreS3-RuleBot
- **Current Version**: 0.1.0
- **Current Git Branch**: main
- **Last Known Commit Hash**: `f7f57796fa6be68d7230c15d834c63250e5c4318`
- **Active Development Phase**: `VALIDATION` (Pre-Release Evaluation)
- **Last Updated**: 2026-11-25
- **Toolkit Version Used**: CalmTechnology-DevToolkit v0.1.0

---

## 2. Quality Gates Status
| Quality Gate | Title | Current Status | Last Evaluated | Evidence Document / Justification |
|---|---|---|---|---|
| **QG-01** | Definition Ready | **PASS** | 2026-11-20 | `docs/REQUIREMENTS.md` complete and prioritized |
| **QG-02** | Architecture Ready | **PASS** | 2026-11-20 | `docs/ARCHITECTURE.md`, `docs/DECISIONS.md` (`ADR-001` to `ADR-003`) |
| **QG-03** | Build Ready | **NOT_EVALUATED** | 2026-11-25 | Toolchain build unexecuted in toolkit workspace; external build unverified |
| **QG-04** | Audit Ready | **NOT_EVALUATED** | 2026-11-25 | `prompts/EXAMPLE_AUDIT.md` prepared; formal audit report not yet executed |
| **QG-05** | Validation Ready | **BLOCKED** | 2026-11-25 | Host tests unverified (`NOT_RUN`); physical hardware unavailable (`BLOCKED`) |
| **QG-06** | Release Ready | **BLOCKED** | 2026-11-25 | Gate blocked by QG-05; Release Review Decision is `INSUFFICIENT_EVIDENCE` |

---

## 3. Baseline Functional Capabilities (Protected Against Modification)
*The following architectural capabilities are specified in `docs/REQUIREMENTS.md` and implemented in the reference repository. While empirical confirmation remains pending, they are **PROTECTED** by design against opportunistic refactoring:*
1. **French Text Normalizer** (`REQ-F-001`, tests `SYS-001`, `SYS-003`, `SYS-008` pending):
   - Diacritics stripping, case folding, elision normalization.
2. **Deterministic Intent Engine** (`REQ-F-002`, tests `SYS-001`, `SYS-002`, `SYS-005` pending):
   - Greetings, Help, Status, and Unknown fallback.
3. **Typo Tolerance Guard** (`REQ-F-003`, tests `SYS-004`, `REG-001` pending):
   - Levenshtein distance = 1 on keywords >= 4 characters; rejection of "salade".
4. **Negation Protection** (`REQ-F-006`, test `SYS-009` pending):
   - Rejection of action commands preceded by "ne... pas" or "sans modifier".

---

## 4. Pending & Blocked Validations
1. **Host Simulation Test Execution (`SYS-001` to `SYS-010`)**:
   - Status: Specifications established in `docs/TEST_PLAN.md`; execution run pending in target repository.
2. **Physical Hardware Acceptance (`MAT-001`)**:
   - Status: `BLOCKED` — Target physical CoreS3 device currently unavailable in verification environment.
3. **Memory Leak Soak Test on CoreS3 (`MAT-002`)**:
   - Status: `BLOCKED` — Requires physical silicon execution of 100 queries.

---

## 5. Active Defect Registry Summary
- Total Defects Logged: 1 (`ISSUE-001` — Pedagogical Defect Scenario)
- Educational Scenario Status: RESOLVED in pedagogical walkthrough with regression test specification `REG-001`.
- Open Real Defects: 0 confirmed unhandled defects.

---

## 6. Recommended Next Action
> **NEXT IMMEDIATE STEP**: Run clean build and host test runner on CoreS3-RuleBot target repository to empirically verify `SYS-001` to `SYS-010`, conduct formal code audit to generate `docs/AUDIT_REPORT.md` (QG-04), and flash firmware to physical M5Stack CoreS3 hardware for `MAT-001` and `MAT-002` (QG-05) to enable definitive release gate clearance.
