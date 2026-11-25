# Prompt: Generate Development Prompt

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Prépare la prochaine évolution suivante :

[Description]

Préserve les fonctionnalités validées.
Produis le plan et le prompt de réalisation.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Generate Scoped Development Prompt for AI Assistant

You are acting as the Lead Task Architect using the Prompt Generator skill (`CalmTechnology-DevToolkit/skills/prompt-generator/SKILL.md`).

## Inputs
- **Project Name**: [Project Name]
- **Target Version**: [e.g., 0.1.0]
- **Target Requirement**: [e.g., REQ-F-003: Text Tokenization]
- **Target Component**: [e.g., src/tokenizer.cpp]
- **Applicable Profile**: [e.g., CalmTechnology-DevToolkit/profiles/cores3.md]

## Execution Instructions
Generate a comprehensive, self-contained development prompt formatted in Markdown that can be given to an AI assistant to execute this specific task with zero ambiguity.

The generated prompt MUST contain all of the following mandatory sections:
1. **Header & Context**: Project name, target version, objective, relevant requirement IDs.
2. **Mandatory Pre-Flight**: Read `docs/PROJECT_STATE.md` and actual source code before editing.
3. **Modification Boundaries**:
   - Explicit list of files permitted for creation or modification.
   - Explicit list of files strictly forbidden from modification.
4. **Preserved Features Safeguard**: Explicit enumeration of previously validated features that must NOT be broken or refactored.
5. **Technical Constraints**: Memory budgets, non-blocking requirements, profile specifics.
6. **Acceptance Criteria**: Exact quantifiable conditions for success.
7. **Verification & Tests**: Specific compilation commands and test execution commands (`UNIT-xxx`, `SYS-xxx`).
8. **Documentation Updates**: Mandatory updates to `docs/PROJECT_STATE.md` and `docs/TEST_RESULTS.md`.
9. **Final Report Format**: Standardized reporting template summarizing work done and remaining steps.

## Deliverable
Output the complete, production-ready markdown prompt file ready to be saved into `prompts/` or directly executed.
```
