# Contributing to CalmTechnology-DevToolkit

Thank you for your interest in contributing to **CalmTechnology-DevToolkit**.

This project provides a calm, disciplined, and evidence-based methodology for AI-assisted software engineering, especially for embedded, desktop, web, and voice applications.

---

## 1. Principles of Contribution

1. **Clarity and Usability**: Every file, skill, profile, and workflow must be immediately actionable by developers and AI agents.
2. **Zero Fictional Data**: Templates and examples must clearly distinguish between real verified data and educational hypothetical scenarios.
3. **Strict Scope in v0.1.0**: The Foundation release consists exclusively of structured Markdown documents, profiles, workflows, and prompts. No executable runtime code, external dependencies, or complex automation frameworks belong in this version.
4. **Bilingual Documentation**: Core user guides and high-level onboarding documents must be maintained in both English (`.md`) and French (`.fr.md`).

---

## 2. Repository Structure & Conventions

- `skills/<skill-name>/SKILL.md`: Must begin with a valid YAML frontmatter block (`name`, `description`) and contain all 12 mandatory sections defined in `docs/SKILL_FORMAT.md`.
- `workflows/<workflow-name>.md`: Must provide clear phase-by-phase guidance with entry and exit criteria.
- `templates/<TEMPLATE_NAME>.md`: Must provide production-ready structures with clear placeholders.
- `profiles/<profile-name>.md`: Must supply concrete technical constraints, memory budgets, and best practices.
- `prompts/<prompt-name>.md`: Must provide copy-pasteable, structured prompts for AI interaction.
- `examples/<project>/`: Must present complete, traceable, and realistic development cases.

---

## 3. Pull Request and Verification Process

Before submitting a contribution:
1. Run internal consistency checks:
   - Ensure all internal Markdown links are valid and relative.
   - Verify that all skill YAML headers are intact.
   - Confirm that no temporary files or sensitive tokens are included.
2. Review the Quality Gates defined in `docs/QUALITY_GATES.md`.
3. Provide a clear summary of modifications and the motivation behind them.
