# Prompt: Record Empirical Test Results

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Enregistre les résultats de tests suivants :

[Résultats]

Actualise les documents concernés.
Ne modifie pas le code.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Record Empirical Test Execution Results and Evidence

You are acting as the Lead Test and Validation Engineer using the CalmTechnology-DevToolkit methodology.

## Mandatory Pre-Flight Instructions
1. Read the global operational rules in `CalmTechnology-DevToolkit/AGENTS.md`.
2. Follow the workflow defined in `CalmTechnology-DevToolkit/workflows/regression-testing.md`.
3. Activate the skill `CalmTechnology-DevToolkit/skills/test-engineer/SKILL.md`.

## CRITICAL RULES FOR TEST EVIDENCE
- **Authorized Test Execution Statuses**: Strictly assign one of: `NOT_RUN`, `PASS`, `FAIL`, `BLOCKED`, or `NOT_APPLICABLE`.
- **Evidence Provenance Classification**: Always record provenance: `DIRECTLY_VERIFIED`, `USER_REPORTED`, `EXTERNAL_REPORTED`, `ILLUSTRATIVE`, `UNVERIFIED`.
- **NEVER Mark an Unexecuted Test as PASS**: If a test was not run, its status is strictly `NOT_RUN`. If prevented by missing equipment, status is `BLOCKED`.
- **Zero Fabrication**: Never invent console outputs, test durations, or passing assertions.
- **Hardware vs. Host**: Clearly distinguish between host simulation tests (`SYS-xxx`) and physical target hardware tests (`MAT-xxx`).
- **User-Reported Data**: If test results are supplied by the user rather than automated scripts, record them as `USER_REPORTED`. Never claim direct autonomous AI verification.

## Test Execution Details
- **Software Version**: [e.g., 0.1.0]
- **Target Commit Hash**: [commit-hash]
- **Execution Date**: YYYY-MM-DD
- **Test Operator**: [Developer Name / Automated Suite]
- **Execution Environment**: [e.g., Host PC Simulator / M5Stack CoreS3 Hardware]

## Test Data to Record
[Paste the raw console logs, test command outputs, or manual observation notes here]

## Execution Instructions
1. Open or create `docs/TEST_RESULTS.md` using `CalmTechnology-DevToolkit/templates/TEST_RESULTS.md`.
2. Update the status of each executed test: `PASS`, `FAIL`, `BLOCKED`, `NOT_RUN`, or `NOT_APPLICABLE`.
3. Preserve the exact terminal outputs or serial monitor captures as empirical evidence.
4. If any test failed:
   - Log the defect in `docs/KNOWN_ISSUES.md` (`ISSUE-xxx`).
   - Flag Quality Gate QG-05 as `FAIL`.
5. If hardware tests cannot be executed due to missing board:
   - Mark hardware tests as `BLOCKED`.
   - Gate QG-05 status is `BLOCKED`.
6. If all mandatory tests passed with verified evidence:
   - Update `docs/PROJECT_STATE.md` with newly validated features.
   - Flag Quality Gate QG-05 as `PASS`.

## Expected Response
- Summary table of executed tests with statuses and evidence provenance.
- Updated `docs/TEST_RESULTS.md` content.
- Evaluation of Quality Gate QG-05 (`PASS`, `FAIL`, or `BLOCKED`).
```
