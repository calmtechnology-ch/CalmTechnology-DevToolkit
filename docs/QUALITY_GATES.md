# Quality Gates Specification

## 1. Purpose
Quality Gates are formal, objective checkpoints that prevent premature advances, untested deployments, and unverified releases. Every project progressing through the **CalmTechnology-DevToolkit** must satisfy the applicable Quality Gates.

---

## 2. The Six Quality Gates

```mermaid
flowchart LR
    QG01["QG-01<br>Definition Ready"] --> QG02["QG-02<br>Architecture Ready"]
    QG02 --> QG03["QG-03<br>Build Ready"]
    QG03 --> QG04["QG-04<br>Audit Ready"]
    QG04 --> QG05["QG-05<br>Validation Ready"]
    QG05 --> QG06["QG-06<br>Release Ready"]
```

### QG-01 — Definition Ready
- **Focus**: Requirements Completeness & Scope Clarity.
- **Criteria**:
  - `docs/PROJECT.md` is populated with clear goals and out-of-scope boundaries.
  - All functional requirements (`REQ-F-xxx`) have priorities and testable acceptance criteria.
  - Non-functional requirements (`REQ-NF-xxx`) have quantifiable metrics.
  - Zero application code written during this phase.

### QG-02 — Architecture Ready
- **Focus**: Modular Design & Architectural Integrity.
- **Criteria**:
  - `docs/ARCHITECTURE.md` documents components, interfaces, and data flows.
  - Major technical choices are recorded as ADRs in `docs/DECISIONS.md`.
  - Embedded hardware constraints and memory budgets are documented.
  - Initial test plan `docs/TEST_PLAN.md` is populated with status `NOT_RUN`.

### QG-03 — Build Ready
- **Focus**: Compilation & Toolchain Cleanliness.
- **Criteria**:
  - Code compiles cleanly across all applicable toolchains (GCC, Clang, PlatformIO, etc.).
  - Zero compiler errors; zero unaddressed critical warnings.

### QG-04 — Audit Ready
- **Focus**: Code Quality, Security, and Regression Prevention.
- **Criteria**:
  - Source code audit completed following the 10-step protocol.
  - `docs/AUDIT_REPORT.md` produced.
  - Zero open `CRITICAL` or `HIGH` severity defects.
  - Validated features listed in `docs/PROJECT_STATE.md` remain uncompromised.

### QG-05 — Validation Ready
- **Focus**: Empirical Verification & Test Evidence.
- **Criteria**:
  - 100% of P0 functional requirements verified via passing tests in `docs/TEST_RESULTS.md`.
  - Non-regression tests (`REG-xxx`) executed with zero failures.
  - If embedded target: physical hardware acceptance tests (`MAT-xxx`) executed and documented.
  - Zero tests hallucinated or falsely marked PASS without terminal evidence.

### QG-06 — Release Ready
- **Focus**: Release Transparency & Packaging.
- **Criteria**:
  - `docs/RELEASE_CHECKLIST.md` completed.
  - Version consistency verified across `VERSION`, `CHANGELOG.md`, and build configs.
  - License present; zero committed secrets or API tokens verified.
  - Formal release report `docs/RELEASE_REPORT.md` issued with justified decision (`GO`, `CONDITIONAL_GO`, `NO_GO`, `INSUFFICIENT_EVIDENCE`).

---

## 3. Authorized Evaluation Statuses
Every Quality Gate must receive one of the following formal statuses:
- **`PASS`**: All gate criteria fully satisfied with empirical evidence.
- **`FAIL`**: One or more gate criteria explicitly failed.
- **`BLOCKED`**: Progress halted due to external dependency or missing equipment.
- **`NOT_EVALUATED`**: Gate not yet evaluated for the current version.
- **`NOT_APPLICABLE`**: Gate does not apply to current project type (e.g., PlatformIO build gate for a pure documentation project).
