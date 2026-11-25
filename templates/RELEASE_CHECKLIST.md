# Release Verification Checklist: [Project Name]

## 1. Release Candidate Metadata
- **Project Name**: [Project Name]
- **Release Version**: 0.1.0
- **Git Branch**: main
- **Commit Hash**: [commit-hash]
- **Review Date**: YYYY-MM-DD
- **Lead Reviewer**: [Release Reviewer]

---

## 2. Quality Gate Verification Matrix

### QG-01: Definition Ready
- [ ] `docs/PROJECT.md` is populated and current.
- [ ] All functional requirements (`REQ-F-xxx`) have priorities and acceptance criteria.
- [ ] Out-of-scope capabilities are explicitly documented.
- **Status**: [PASS / FAIL / BLOCKED]

### QG-02: Architecture Ready
- [ ] `docs/ARCHITECTURE.md` documents components, interfaces, and data flows.
- [ ] All significant technical choices are recorded as ADRs in `docs/DECISIONS.md`.
- [ ] Hardware constraints and memory budgets are documented.
- **Status**: [PASS / FAIL / BLOCKED]

### QG-03: Build Ready
- [ ] Clean build passes across all target environments (e.g., host simulator, PlatformIO).
- [ ] Zero compiler errors; zero unaddressed critical warnings.
- **Status**: [PASS / FAIL / BLOCKED]

### QG-04: Audit Ready
- [ ] Source code audit completed following the 10-step protocol.
- [ ] `docs/AUDIT_REPORT.md` is populated with zero open `CRITICAL` or `HIGH` issues.
- [ ] All discovered defects are cataloged in `docs/KNOWN_ISSUES.md`.
- **Status**: [PASS / FAIL / BLOCKED]

### QG-05: Validation Ready
- [ ] 100% of P0 functional requirements have passing tests in `docs/TEST_RESULTS.md`.
- [ ] Regression tests (`REG-xxx`) executed with zero failures.
- [ ] Physical hardware tests (`MAT-xxx`) executed on real board (or explicitly marked `NOT_RUN` with reason).
- **Status**: [PASS / FAIL / BLOCKED]

### QG-06: Release Ready
- [ ] Version number is consistent across `VERSION`, `CHANGELOG.md`, and build configs.
- [ ] License file (`LICENSE`) is present and valid.
- [ ] Zero committed secrets, private API keys, or credentials verified.
- [ ] Known issues and operational limitations are documented in release notes.
- **Status**: [PASS / FAIL / BLOCKED]

---

## 3. Release Readiness Evaluation
- **Overall Quality Gate Status**: [ALL PASS / PENDING HARDWARE / BLOCKED]
- **Recommended Verdict**: [GO / CONDITIONAL_GO / NO_GO / INSUFFICIENT_EVIDENCE]
