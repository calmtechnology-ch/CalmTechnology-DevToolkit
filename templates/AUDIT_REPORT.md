# Source Code Audit Report: [Project Name]

## 1. Audit Metadata
- **Project Name**: [Project Name]
- **Target Software Version**: 0.1.0
- **Audited Git Branch**: main
- **Audited Commit Hash**: [commit-hash]
- **Audit Date**: YYYY-MM-DD
- **Lead Auditor**: [Name / Skill: `code-auditor`]
- **Scope of Audit**: [Full codebase / Targeted modules]

---

## 2. Executive Summary
*Provide a 2-paragraph summary of the overall code health, compliance with documented requirements, architecture discipline, and key findings.*

- **Overall Health Verdict**: [EXCELLENT | ACCEPTABLE | AT_RISK | CRITICAL_DEFECTS]
- **Quality Gate QG-04 (Audit Ready)**: [PASS | FAIL | BLOCKED]
- **Total Findings**:
  - `CRITICAL`: 0
  - `HIGH`: 0
  - `MEDIUM`: 0
  - `LOW`: 0
  - `INFORMATION`: 0

---

## 3. Findings Matrix

| Finding ID | Severity | File & Location | Requirement Impact | Brief Summary | Remediation Status |
|---|---|---|---|---|---|
| `AUD-001` | [CRITICAL/HIGH/MED/LOW] | `[file:line]` | `[REQ-xxx]` | [Brief description] | [OPEN / FIXED] |
| `AUD-002` | [CRITICAL/HIGH/MED/LOW] | `[file:line]` | `[REQ-xxx]` | [Brief description] | [OPEN / FIXED] |

---

## 4. Detailed Audit Findings

### `AUD-001`: [Finding Title]
- **Stable Finding ID**: `AUD-001`
- **Severity**: `[CRITICAL | HIGH | MEDIUM | LOW | INFORMATION]`
- **Epistemic Classification**: `[CONFIRMED_DEFECT | POTENTIAL_RISK | HYPOTHESIS | MISSING_INFO]`
- **Target File**: `[src/example.cpp]`
- **Target Function**: `[process_data()]`
- **Line Reference**: Line [XX] - Line [YY]

#### Description
*Detailed description of the code anomaly or risk.*

#### Concrete Evidence
```cpp
// Code snippet showing the issue
```

#### Potential Consequence & Impact
*What happens at runtime under normal or edge conditions?*

#### Recommended Remediation
*Specific, minimal code change proposed to resolve the finding.*

#### Verification Test
- **Proposed Test**: `[TEST-ID]`

---

## 5. Architectural & Security Observations
- **Modularity & Layering**: [Are HAL, core logic, and UI cleanly decoupled?]
- **Concurrency & Thread Safety**: [Are FreeRTOS queues/mutexes utilized properly?]
- **Dynamic Memory & Heap Health**: [Are allocations bounded? Risk of heap fragmentation?]
- **Secrets & Credentials**: [Confirm complete absence of hardcoded API keys or passwords.]
