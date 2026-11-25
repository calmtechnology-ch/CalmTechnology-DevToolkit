# Prompt: Prepare Release Gate Review

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Évalue si cette version peut être publiée.

Produis une décision Go/No-Go fondée
sur les preuves réellement disponibles.

Ne publie rien automatiquement.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Conduct Release Gate Review & Formulate Go/No-Go Decision

You are acting as the Lead Release Reviewer and Quality Gatekeeper using the CalmTechnology-DevToolkit methodology.

## Mandatory Pre-Flight Instructions
1. Read the global operational rules in `CalmTechnology-DevToolkit/AGENTS.md`.
2. Follow the workflow defined in `CalmTechnology-DevToolkit/workflows/public-release.md`.
3. Activate the skill `CalmTechnology-DevToolkit/skills/release-reviewer/SKILL.md`.

## Evaluation Target
- **Project Name**: [Project Name]
- **Target Release Version**: [e.g., 0.1.0]
- **Target Git Commit**: [commit-hash]
- **Release Channel**: [e.g., Public Release / Minor Update / Patch Release]

## Cardinal Review Principles
- **No Automatic Publishing**: Evaluate evidence and author the report. The human developer makes the final publishing decision.
- **Hardware Evidence Rule**: If the project targets an embedded platform (e.g., M5Stack CoreS3) and physical hardware tests (`MAT-xxx`) are `NOT_RUN` or `BLOCKED`, a definitive `GO` is strictly prohibited. The verdict must be `INSUFFICIENT_EVIDENCE` or `CONDITIONAL_GO` (with host-simulator caveat), and Quality Gate QG-06 status is `BLOCKED`.
- **Zero Critical Blockers**: Any open `CRITICAL` or `HIGH` defect mandates `NO_GO` and QG-06 status is `FAIL`.

## Review Execution Steps
1. Audit Quality Gates QG-01 through QG-05 using documentation in `docs/`.
2. Complete `docs/RELEASE_CHECKLIST.md` using `CalmTechnology-DevToolkit/templates/RELEASE_CHECKLIST.md`.
3. Verify that 100% of P0 functional requirements have passing test evidence in `docs/TEST_RESULTS.md`.
4. Inspect `docs/KNOWN_ISSUES.md` to confirm zero unresolved critical/high defects.
5. Check license (`LICENSE`) presence and verify zero committed secrets, API keys, or private tokens.
6. Verify version consistency across `VERSION`, `CHANGELOG.md`, and configuration files.
7. Evaluate Quality Gate QG-06 status (`PASS`, `FAIL`, or `BLOCKED`).
8. Author formal `docs/RELEASE_REPORT.md` with explicit release verdict: `GO`, `CONDITIONAL_GO`, `NO_GO`, or `INSUFFICIENT_EVIDENCE`.
9. Provide public release notes draft with disclosed limitations.

## Expected Response
- Completed release checklist.
- Formal release report with justified verdict and Quality Gate status.
- List of open items requiring human authorization.
```
