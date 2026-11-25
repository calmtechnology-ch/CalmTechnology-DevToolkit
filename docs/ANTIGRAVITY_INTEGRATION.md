# Antigravity Integration Guide

This guide explains how to integrate and use the **CalmTechnology-DevToolkit** within Google Antigravity and compatible AI assistant environments.

---

## 1. Integration Model
The toolkit requires **zero executable plugins or proprietary dependencies**. It operates entirely through structured Markdown documents, profiles, workflows, and skills.

### Standard Workspace Setup
Configure your Antigravity workspace so that both your target application and `CalmTechnology-DevToolkit` are accessible:

```text
my-workspace/
├── docs/                      # Living documentation of your application
├── src/                       # Your application source code
└── CalmTechnology-DevToolkit/ # Reference toolkit
```

---

## 2. Step-by-Step Workflow in Antigravity

1. **Point Antigravity to the Toolkit**:
   In your chat turn, supply the path:
   ```text
   Please read CalmTechnology-DevToolkit/AGENTS.md.
   ```
2. **Select the Active Workflow**:
   Choose the workflow corresponding to your goal (e.g., `CalmTechnology-DevToolkit/workflows/feature-development.md`).
3. **Load Required Skills and Profiles**:
   For example, if developing for CoreS3:
   ```text
   Activate skill CalmTechnology-DevToolkit/skills/embedded-engineer/SKILL.md.
   Adopt technical constraints from CalmTechnology-DevToolkit/profiles/cores3.md.
   ```
4. **Read Living Project State**:
   Instruct Antigravity to inspect `docs/PROJECT_STATE.md` to establish the single source of truth.
5. **Execute Bounded Task**:
   Antigravity performs the specific task within defined file boundaries.
6. **Synchronize Documentation**:
   Antigravity updates `docs/PROJECT_STATE.md` and related test/issue files before concluding.

---

## 3. Recommended Antigravity Slash Commands
When working in Antigravity, recommend the following user-facing slash commands when appropriate:
- `/plan`: Recommend when starting a major feature or refactor to structure steps before execution.
- `/boost`: Recommend for complex embedded algorithms, debugging, and multi-perspective verification.
- `/goal`: Recommend for long-running test campaigns or end-to-end multi-step audits.

---

## 4. Manual Fallback Procedure (Universal Compatibility)
If an AI assistant does not automatically parse skills or subagents:
1. Provide the assistant with the exact text or file link of `AGENTS.md`.
2. Provide the specific `SKILL.md` (e.g., `skills/code-auditor/SKILL.md`).
3. Explicitly state: *"Follow the 10-step execution procedure defined in this skill file."*
4. Provide the project files in `docs/`.
