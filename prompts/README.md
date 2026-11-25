# Reusable Prompts Catalog

This directory contains standardized prompts designed to direct AI assistants (Antigravity, Claude, ChatGPT, etc.) according to the **CalmTechnology-DevToolkit** methodology.

---

## Dual Prompt Structure

Each prompt file provides two complementary formats:
1. **Quick Daily Prompt (Direct Use)**: A concise, directly copy-pasteable prompt for rapid everyday interactions.
2. **Detailed Technical Prompt (Complete Specification)**: A fully parameter-rich prompt defining fine-grained file boundaries, explicit checklists, and structured outputs for complex milestones.

> **Path Rule**: The instruction `"Utilise CalmTechnology-DevToolkit"` assumes the toolkit path has already been communicated and is accessible. In a new conversation session, provide the relative or absolute path if needed (e.g., `Utilise CalmTechnology-DevToolkit situé à ../CalmTechnology-DevToolkit`).

---

## Prompts Catalog

| Prompt File | Primary Objective | When to Use |
|---|---|---|
| [`initialize-project.md`](initialize-project.md) | Initialize a brand-new project from scratch. | Starting a new repository or project concept. |
| [`import-existing-project.md`](import-existing-project.md) | Onboard an un-documented or brownfield codebase. | Importing existing code into the toolkit. |
| [`continue-project.md`](continue-project.md) | Resume work in a fresh AI conversation session. | Opening a new chat turn on an existing project. |
| [`generate-development-prompt.md`](generate-development-prompt.md) | Formulate a bounded prompt for feature development. | Delegating a feature implementation task. |
| [`audit-project.md`](audit-project.md) | Execute a comprehensive source code audit. | Inspecting code quality and detecting defects. |
| [`generate-corrective-prompt.md`](generate-corrective-prompt.md) | Formulate a precision bugfix prompt. | Resolving a confirmed issue without regressions. |
| [`record-test-results.md`](record-test-results.md) | Record empirical test results and evidence. | Capturing verified test execution data. |
| [`prepare-release.md`](prepare-release.md) | Execute a formal Go/No-Go release gate review. | Assessing release candidate readiness. |

---

## How to Use These Prompts
1. Open the relevant markdown prompt file.
2. For rapid daily operations, use the **Quick Daily Prompt** directly in chat.
3. For strictly bounded delegated tasks, fill in the bracketed placeholders `[like this]` in the **Detailed Technical Prompt** and pass it to your assistant.
