# Prompt: Initialize New Project

## 1. Quick Daily Prompt (Direct Use)

> **Note**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has been communicated to the assistant and its files are accessible. In a fresh conversation session, provide the relative or absolute path if necessary (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

```text
Utilise CalmTechnology-DevToolkit.

Initialise la documentation de ce projet
selon le workflow new-project.

Ne commence pas à programmer.
```

---

## 2. Detailed Technical Prompt (Complete Specification)

```markdown
# TASK: Initialize New Project with CalmTechnology-DevToolkit

You are acting as the Lead Requirements Engineer and Systems Architect using the CalmTechnology-DevToolkit methodology.

## Mandatory Pre-Flight Instructions
1. Read the global operational rules in `CalmTechnology-DevToolkit/AGENTS.md`.
2. Follow the workflow defined in `CalmTechnology-DevToolkit/workflows/new-project.md`.
3. Activate the skill `CalmTechnology-DevToolkit/skills/project-definition/SKILL.md`.
4. Review the target technical profile: `CalmTechnology-DevToolkit/profiles/[e.g., cores3.md / web-application.md]`.

## Project Identification
- **Project Name**: [Enter Project Name, e.g., CoreS3-RuleBot]
- **Target Organization / Author**: [Enter GitHub Org or Author]
- **Target Platform**: [e.g., M5Stack CoreS3 / ESP32-S3 / Web / Electron / Python]
- **Target Version**: 0.1.0 (Foundation)
- **Target License**: MIT

## Concept & Objectives
[Describe the project idea, target audience, primary problem to solve, and core use cases here]

## Execution Instructions
1. Create the `docs/` directory in the project root if it does not already exist.
2. Initialize and populate `docs/PROJECT.md` using the template `CalmTechnology-DevToolkit/templates/PROJECT.md`.
3. Formulate structured functional requirements (`REQ-F-001`, `REQ-F-002`, etc.) and non-functional requirements (`REQ-NF-001`, etc.) in `docs/REQUIREMENTS.md` using `CalmTechnology-DevToolkit/templates/REQUIREMENTS.md`.
4. Define explicit acceptance criteria and out-of-scope boundaries.
5. Initialize `docs/PROJECT_STATE.md` using `CalmTechnology-DevToolkit/templates/PROJECT_STATE.md` with active phase set to `DEFINITION`.
6. DO NOT write any application source code during this turn.

## Expected Response
- Summary of the defined project charter and scope boundaries.
- Full text or diff of created `docs/PROJECT.md`, `docs/REQUIREMENTS.md`, and `docs/PROJECT_STATE.md`.
- Evaluation of Quality Gate QG-01 (Definition Ready).
- Recommendation for Phase 2 (Architecture).
```
