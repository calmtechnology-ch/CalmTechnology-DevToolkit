# Corrective Action Plan: [Project Name]

## 1. Defect Identification
- **Target Defect ID**: `ISSUE-xxx`
- **Severity**: `[CRITICAL | HIGH | MEDIUM | LOW]`
- **Target Software Version**: 0.1.0
- **Corrective Patch Version**: 0.1.1
- **Date**: YYYY-MM-DD
- **Author**: [Lead Engineer / Prompt Generator]

---

## 2. Problem Statement & Reproduction
- **Observed Defect**: [Describe the erroneous behavior]
- **Reproduction Procedure**:
  1. [Step 1]
  2. [Step 2]
  3. [Step 3]
- **Empirical Evidence**: [Log output, assertion failure, or crash dump]

---

## 3. Root Cause Analysis
- **Defect Locus**: File `[path]`, function `[name]`, line `[line #]`.
- **Root Cause Mechanism**: [Explain the exact logical or memory flaw causing the failure].

---

## 4. Scope of Correction & Minimal Modification Locus
*To prevent introducing new bugs, modifications must be confined to the minimal necessary code paths.*

- **Allowed Files for Modification**:
  - `[file 1 path]`
  - `[file 2 path]`
- **Forbidden Files (Strictly Protected)**:
  - `[file 3 path]`
  - All unrelated core engine modules.
- **Forbidden Actions**:
  - NO new feature additions.
  - NO opportunistic refactoring of working code paths.

---

## 5. Non-Regression Safeguard Plan
- **Protected Validated Features**:
  1. [Feature 1]: Verified via `SYS-001`.
  2. [Feature 2]: Verified via `SYS-002`.
- **Regression Test Suite**:
  - Dedicated reproduction test: `REG-xxx`.
  - Full regression test run: all `SYS-xxx` and `MAT-xxx` tests.

---

## 6. Execution & Verification Steps
1. Apply targeted patch in allowed files.
2. Verify clean compilation (Quality Gate QG-03).
3. Execute `REG-xxx`: must PASS.
4. Execute full regression suite: zero failures.
5. Update `docs/KNOWN_ISSUES.md` and `docs/PROJECT_STATE.md`.
