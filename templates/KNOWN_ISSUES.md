# Known Issues & Defect Registry: [Project Name]

This document is the official registry of all confirmed defects, edge case vulnerabilities, and technical anomalies.

---

## Issue Summary Matrix

| Issue ID | Severity | Status | Version Found | Target Fix Version | Associated Regression Test | Summary |
|---|---|---|---|---|---|---|
| `ISSUE-001` | [CRITICAL/HIGH/MED/LOW] | [OPEN/RESOLVED] | 0.1.0 | 0.1.1 | `REG-001` | [Brief title] |
| `ISSUE-002` | [CRITICAL/HIGH/MED/LOW] | [OPEN/RESOLVED] | 0.1.0 | 0.1.1 | `REG-002` | [Brief title] |

---

## Detailed Issue Cards

### `ISSUE-001`: [Issue Title]
- **Stable Identifier**: `ISSUE-001`
- **Severity**: `[CRITICAL | HIGH | MEDIUM | LOW | INFORMATION]`
- **Status**: `[OPEN | UNDER_INVESTIGATION | FIX_PROPOSED | RESOLVED | WONT_FIX]`
- **Version Detected**: 0.1.0
- **Reported Date**: YYYY-MM-DD
- **Reporter**: [Name / Skill: `code-auditor`]
- **Affected File(s)**: `[src/file.cpp]`, function `[function_name()]`, line `[line #]`

#### 1. Description of Defect
*What is the incorrect or unexpected behavior?*

#### 2. Exact Reproduction Procedure
1. [Step 1: Input or setup]
2. [Step 2: Action performed]
3. [Step 3: Trigger condition]

#### 3. Empirical Evidence
- **Observed Behavior**: [Exact error message, stack trace, or incorrect output]
  ```text
  [Paste error log or assertion failure here]
  ```
- **Expected Behavior**: [What should have happened according to requirements]

#### 4. Root Cause Analysis
*What specific line of code or logic defect causes this behavior?*

#### 5. Impact & Consequence
*What is the risk to users, hardware, or other system modules if left uncorrected?*

#### 6. Remediation & Targeted Fix
*What code change resolves the defect without introducing side effects?*

#### 7. Non-Regression Test
- **Regression Test ID**: `REG-001`
- **Verification Criteria**: [Criterion to mark issue as RESOLVED]
