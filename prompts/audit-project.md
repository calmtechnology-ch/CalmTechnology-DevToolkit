# Prompt: Audit Project Source Code

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Audite la version actuelle de ce projet.
Identifie les anomalies et les risques
à partir du code réel.

Ne modifie pas le code.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Execute Source Code Quality & Security Audit

You are acting as the Lead Software Quality and Security Auditor using the CalmTechnology-DevToolkit methodology.

## Mandatory Pre-Flight Instructions
1. Read the global operational rules in `CalmTechnology-DevToolkit/AGENTS.md`.
2. Follow the workflow defined in `CalmTechnology-DevToolkit/workflows/code-audit.md`.
3. Activate the skill `CalmTechnology-DevToolkit/skills/code-auditor/SKILL.md`.

## Epistemic Rigor & Constraints
- **Examine Real Code Only**: Read the actual implementation files. Never audit a file based on file names, summaries, or README claims.
- **Classification Standards**: Every finding must be classified as:
  - `CRITICAL`: Crash, memory corruption, severe security vulnerability, TWDT reset.
  - `HIGH`: Broken core requirement, failure in main execution path, regression on validated feature.
  - `MEDIUM`: Edge case failure, unhandled error, memory leak under stress.
  - `LOW`: Style divergence, minor warning, non-critical comment omission.
  - `INFORMATION`: Missing information or uninspected file.
- **Epistemic Clarity**: Strictly distinguish between Confirmed Defects, Potential Risks, Hypotheses, and Missing Information.

## 10-Step Execution Protocol
1. Record target version, Git branch, and commit hash.
2. Examine the file tree and identify active source modules.
3. Read the complete implementation of all active files.
4. Compare actual code against `docs/REQUIREMENTS.md`.
5. Identify inconsistencies, type mismatches, and dead code.
6. Evaluate regression risks against features listed in `docs/PROJECT_STATE.md`.
7. Inspect error handling, buffer bounds, null pointers, and watchdog feeding.
8. Inspect third-party dependencies, configuration files, and license compliance.
9. Control test suites to ensure assertions are meaningful.
10. Author `docs/AUDIT_REPORT.md` using `CalmTechnology-DevToolkit/templates/AUDIT_REPORT.md` and log newly discovered issues into `docs/KNOWN_ISSUES.md`.

## Expected Response
- Executive summary of code audit findings.
- Finding matrix table with IDs, severities, and locations.
- Formal evaluation of Quality Gate QG-04 (Audit Ready: PASS, FAIL, or BLOCKED).
```
