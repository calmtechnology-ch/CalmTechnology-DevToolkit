# Engineering Skills Catalog

This directory contains the 8 specialized engineering skills of the **CalmTechnology-DevToolkit**. Each skill defines a disciplined role, actionable procedures, decision rules, constraints, and quality checklists.

---

## Skill Architecture

Every skill follows the standardized 12-section schema documented in [docs/SKILL_FORMAT.md](../docs/SKILL_FORMAT.md):
1. **Role**: Professional persona and core responsibility.
2. **Objectives**: What the skill aims to accomplish.
3. **When to use**: Triggers and lifecycle contexts.
4. **Required inputs**: Essential documents and information.
5. **Optional inputs**: Contextual or supplementary information.
6. **Constraints**: Methodological boundaries (e.g., zero hallucination, scope isolation).
7. **Execution procedure**: Step-by-step operational instructions.
8. **Decision rules**: Heuristics for resolving ambiguities and trade-offs.
9. **Expected outputs**: Primary documents and deliverables produced.
10. **Quality checklist**: Self-verification gate before declaring completion.
11. **Failure conditions**: Criteria triggering a block or escalation.
12. **Handoff to other skills**: Transitions to downstream skills in the workflow.

---

## Skills Directory

| Skill ID | Name | Core Responsibility | Primary Artifacts |
|---|---|---|---|
| `project-definition` | [Project Definition](project-definition/SKILL.md) | Clarify problem, scope, constraints, and requirements. | `PROJECT.md`, `REQUIREMENTS.md` |
| `software-architect` | [Software Architect](software-architect/SKILL.md) | Design components, interfaces, data flows, and ADRs. | `ARCHITECTURE.md`, `DECISIONS.md` |
| `embedded-engineer` | [Embedded Engineer](embedded-engineer/SKILL.md) | Ensure hardware constraints (RAM, Flash, RTOS, peripherals). | Hardware budgets, memory maps |
| `ui-designer` | [UI Designer](ui-designer/SKILL.md) | Design readable, responsive, stateful interfaces (LVGL, Web). | UI component specs, state designs |
| `prompt-generator` | [Prompt Generator](prompt-generator/SKILL.md) | Craft scoped, reproducible prompts for development & fixes. | Markdown prompt files |
| `code-auditor` | [Code Auditor](code-auditor/SKILL.md) | Rigorously audit actual source code against requirements. | `AUDIT_REPORT.md`, `KNOWN_ISSUES.md` |
| `test-engineer` | [Test Engineer](test-engineer/SKILL.md) | Design test matrices and document empirical test results. | `TEST_PLAN.md`, `TEST_RESULTS.md` |
| `release-reviewer` | [Release Reviewer](release-reviewer/SKILL.md) | Evaluate readiness and make Go / No-Go release decisions. | `RELEASE_CHECKLIST.md`, `RELEASE_REPORT.md` |

---

## Execution Modes

1. **Integrated AI Execution**: When running in Antigravity or compatible assistants, skills are loaded automatically via workflow directives.
2. **Manual Fallback**: Any developer or AI assistant can execute a skill manually by loading the corresponding `SKILL.md` file and providing the required inputs as specified in [AGENTS.md](../AGENTS.md).
