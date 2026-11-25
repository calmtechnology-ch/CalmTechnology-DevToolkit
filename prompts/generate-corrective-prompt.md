# Prompt: Generate Corrective Prompt

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Prépare une correction ciblée pour :

[Description de l'anomalie]

Préserve les fonctionnalités validées.
N'ajoute aucune fonctionnalité.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Generate Precision Corrective Prompt for Confirmed Defect

You are acting as the Lead Task Architect using the Prompt Generator skill (`CalmTechnology-DevToolkit/skills/prompt-generator/SKILL.md`).

## Defect Inputs
- **Defect Identifier**: `[e.g., ISSUE-001]`
- **Severity**: `[e.g., HIGH]`
- **Target File(s)**: `[e.g., src/text_utils.cpp]`
- **Reported Behavior**: [Describe the erroneous behavior]
- **Reproduction Procedure**: [Provide exact steps to reproduce]
- **Root Cause Analysis**: [Provide confirmed or suspected cause]
- **Target Regression Test**: `[e.g., REG-001]`

## Execution Instructions
Generate a comprehensive, self-contained corrective prompt formatted in Markdown that will direct an AI assistant to fix this bug with laser focus and zero regressions.

The generated prompt MUST contain:
1. **Header & Context**: Issue ID, target version, target patch version (e.g., 0.1.0 -> 0.1.1).
2. **Defect Details**: Observed vs. expected behavior, reproduction command, terminal error evidence.
3. **Root Cause Locus**: Exact file, function, and line range causing the bug.
4. **Strict Scope Boundaries**:
   - Files allowed for modification (confined strictly to defect locus).
   - Files strictly forbidden from modification.
   - Absolute prohibition against opportunistic refactoring or new feature generation.
5. **Preserved Features Safeguard**: Explicit list of validated features that must NOT be broken.
6. **Reproduction & Regression Tests**:
   - Command to run reproduction test `REG-xxx` (must fail before fix, pass after).
   - Command to run full regression test suite (must pass with zero regressions).
7. **Documentation Updates**:
   - Update `docs/KNOWN_ISSUES.md`: mark issue as RESOLVED.
   - Update `docs/PROJECT_STATE.md`: bump version, update commit, update metrics.
8. **Final Report Format**: Standard summary format.

## Deliverable
Output the complete markdown prompt file ready to be saved into `prompts/` or directly executed.
```
