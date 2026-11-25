# Empirical Test Results: [Project Name]

> **EVIDENCE NOTICE**: This document records **empirical evidence** from actual test runs.
> - **Authorized Test Statuses**: `NOT_RUN`, `PASS`, `FAIL`, `BLOCKED`, `NOT_APPLICABLE`.
> - **Evidence Provenance Categories**: `DIRECTLY_VERIFIED`, `USER_REPORTED`, `EXTERNAL_REPORTED`, `ILLUSTRATIVE`, `UNVERIFIED`.
> - An unexecuted test must NEVER be marked as `PASS`. If execution was not undertaken, status is strictly `NOT_RUN`. If prevented by missing equipment, status is `BLOCKED`. User-reported outcomes must be explicitly designated with provenance `USER_REPORTED`.

---

## 1. Test Run Metadata
- **Target Software Version**: 0.1.0
- **Git Commit Hash**: [commit-hash]
- **Execution Date**: YYYY-MM-DD
- **Test Operator**: [Developer Name / Automated CI]
- **Execution Environment**: [e.g., Windows 11 Host / Ubuntu Linux / Physical M5Stack CoreS3]
- **Overall Evidence Provenance**: [DIRECTLY_VERIFIED / USER_REPORTED / EXTERNAL_REPORTED / ILLUSTRATIVE / UNVERIFIED]

---

## 2. Test Execution Summary Matrix

| Test ID | Tier | Target Req / Issue | Execution Status | Duration / Latency | Evidence Provenance | Notes / Operator |
|---|---|---|---|---|---|---|
| `SYS-001` | SYS | `REQ-F-001` | NOT_RUN | — | UNVERIFIED | — |
| `SYS-002` | SYS | `REQ-F-002` | NOT_RUN | — | UNVERIFIED | — |
| `MAT-001` | MAT | `REQ-NF-001` | NOT_RUN | — | UNVERIFIED | Pending physical hardware |
| `REG-001` | REG | `ISSUE-001` | NOT_RUN | — | UNVERIFIED | — |

---

## 3. Detailed Execution Logs & Empirical Evidence

### Test `SYS-001`: [Test Title]
- **Execution Timestamp**: YYYY-MM-DD HH:MM:SS
- **Execution Status**: [PASS / FAIL / BLOCKED / NOT_RUN / NOT_APPLICABLE]
- **Evidence Provenance**: [DIRECTLY_VERIFIED / USER_REPORTED / EXTERNAL_REPORTED / ILLUSTRATIVE / UNVERIFIED]
- **Command Executed**:
  ```bash
  [command line used to run test]
  ```
- **Observed Terminal Output**:
  ```text
  [Paste raw console output here]
  ```
- **Evaluation**: [Analysis of observed output against expected criteria]

---

### Test `MAT-001`: [Hardware Test Title]
- **Execution Timestamp**: YYYY-MM-DD HH:MM:SS
- **Target Device**: Physical M5Stack CoreS3
- **Execution Status**: [PASS / FAIL / BLOCKED / NOT_RUN / NOT_APPLICABLE]
- **Evidence Provenance**: [DIRECTLY_VERIFIED / USER_REPORTED / EXTERNAL_REPORTED / ILLUSTRATIVE / UNVERIFIED]
- **Serial Console Capture**:
  ```text
  [Paste serial monitor log here]
  ```
- **Physical Observation**: [LCD display rendering, touch response, LED behavior]
- **Evidence Verification**: [Verified by operator on physical device]
