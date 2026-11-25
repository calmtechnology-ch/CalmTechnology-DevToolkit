# Standard Skill Format Specification

## 1. Overview
All skills in the **CalmTechnology-DevToolkit** adhere to a standard, modular specification ensuring consistent interpretation by both AI assistants and human software engineers.

---

## 2. Mandatory YAML Frontmatter
Every `SKILL.md` must begin with a YAML header delimited by triple dashes (`---`):

```yaml
---
name: skill-identifier
description: Concise, high-level summary of what the skill accomplishes.
---
```

---

## 3. The 12 Mandatory Sections
Following the YAML frontmatter, every `SKILL.md` must contain all 12 standardized sections:

1. **Role**: The professional persona and core responsibility.
2. **Objectives**: Explicit list of concrete outcomes the skill must achieve.
3. **When to use**: Triggers, lifecycle phases, and conditions that call for this skill.
4. **Required inputs**: Essential documents, files, or information needed to execute.
5. **Optional inputs**: Contextual or supplementary information that improves execution.
6. **Constraints**: Non-negotiable boundaries, safety rules, and methodological guardrails.
7. **Execution procedure**: Step-by-step operational instructions.
8. **Decision rules**: Heuristics, trade-off policies, and conflict resolution rules.
9. **Expected outputs**: Specific deliverables, reports, or document updates produced.
10. **Quality checklist**: Self-verification checklist to validate before declaring completion.
11. **Failure conditions**: Criteria that indicate the skill has failed or must escalate.
12. **Handoff to other skills**: Clear transition points to subsequent skills in the workflow.

---

## 4. Authoring Guidelines
- **Zero Hallucination**: Skills must forbid inventing test results or performance metrics.
- **Traceability**: Skills must require the use of stable identifiers (`REQ-xxx`, `ADR-xxx`, `ISSUE-xxx`, `SYS-xxx`, `MAT-xxx`).
- **Composability**: Skills must be capable of standalone execution or seamless chaining within workflows.
