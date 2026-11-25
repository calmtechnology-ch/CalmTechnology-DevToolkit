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
| Quality Gate | Title | Current Status | Last Evaluated | Evidence Document |
|---|---|---|---|---|
| **QG-01** | Definition Ready | **PASS** | 2026-11-20 | `docs/REQUIREMENTS.md` |
| **QG-02** | Architecture Ready | **PASS** | 2026-11-20 | `docs/ARCHITECTURE.md`, `docs/DECISIONS.md` |
| **QG-03** | Build Ready | **PASS** | 2026-11-22 | Compiler logs (GCC C++17 & PlatformIO) |
| **QG-04** | Audit Ready | **PASS** | 2026-11-23 | `prompts/EXAMPLE_AUDIT.md` (0 Critical/High issues) |
| **QG-05** | Validation Ready | **IN_PROGRESS** | 2026-11-25 | Host tests PASS; hardware tests PENDING |
| **QG-06** | Release Ready | **INSUFFICIENT_EVIDENCE** | 2026-11-25 | `reports/EXAMPLE_RELEASE_REVIEW.md` |

---

## 3. Validated Features (Protected Against Modification)
*The following capabilities have been audited and verified via host automated test suites. Do NOT modify without an approved non-regression plan:*
1. **French Text Normalizer** (Verified via `SYS-001`, `SYS-003`, `SYS-008`):
   - Diacritics stripping, case folding, elision normalization.
2. **Deterministic Intent Engine** (Verified via `SYS-001`, `SYS-002`, `SYS-005`):
   - Greetings, Help, Status, and Unknown fallback.
3. **Typo Tolerance Guard** (Verified via `SYS-004`, `REG-001`):
   - Levenshtein distance = 1 on keywords >= 4 characters; rejection of "salade".
4. **Negation Protection**:
   - Rejection of action commands preceded by "ne... pas" or "sans modifier".

---

## 4. Pending / In-Progress Validations
1. **Physical Hardware Acceptance (`MAT-001`)**:
   - Status: Firmware compiles; pending flash and test on physical CoreS3 device.
2. **Memory Leak Soak Test on CoreS3 (`MAT-002`)**:
   - Status: Pending execution of 100 queries on physical hardware.

---

## 5. Active Defect Registry Summary
- Total Defects Logged: 1 (`ISSUE-001`)
- Resolved: 1 (`ISSUE-001` resolved with regression test `REG-001`)
- Open Defects: 0

---

## 6. Recommended Next Action
> **NEXT IMMEDIATE STEP**: Flash target firmware to physical M5Stack CoreS3 hardware and execute test procedures `MAT-001` (LCD & touch validation) and `MAT-002` (memory stability across 100 requests) to satisfy Quality Gate QG-05 and enable definitive release sign-off.
