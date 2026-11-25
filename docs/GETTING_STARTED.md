# Getting Started with CalmTechnology-DevToolkit

Welcome to **CalmTechnology-DevToolkit**. This guide explains how to start working with your AI assistant in under 5 minutes without having to read the entire methodology beforehand.

---

## 1. Shared Setup (No Installation Required)

The toolkit is 100% file-based Markdown. Keep a single copy of `CalmTechnology-DevToolkit` in your parent directory, shared across all your projects:

```text
Documents/
└── Antigravity-5.1/
    ├── CalmTechnology-DevToolkit/   # Shared methodology
    ├── ProjectA/                    # Project A (own docs/ and src/)
    └── ProjectB/                    # Project B (own docs/ and src/)
```

No git submodules, symlinks, or full toolkit copies are needed.

---

## 2. The 3 Primary Everyday Situations

Select the situation that matches your current goal:

### Situation A — Creating a New Project
1. Open your new project directory.
2. In your AI chat session, send the quick prompt:
   ```text
   Utilise CalmTechnology-DevToolkit.
   Initialise la documentation de ce projet selon le workflow new-project.
   Ne commence pas à programmer.
   ```
3. Describe your project concept and constraints. The assistant will:
   - Create `docs/` and populate `PROJECT.md`, `REQUIREMENTS.md`, and `PROJECT_STATE.md`.
   - Evaluate Quality Gate QG-01 (Definition Ready).

### Situation B — Importing an Existing Codebase
1. Open the existing codebase directory in your editor.
2. In your AI chat session, send the quick prompt:
   ```text
   Utilise CalmTechnology-DevToolkit.
   Examine ce projet existant et initialise sa documentation à partir du code réel.
   Ne modifie aucun fichier source.
   ```
3. The assistant will inspect the code, reverse-engineer baseline requirements, document existing tests, create `docs/PROJECT_STATE.md`, and propose the immediate next step without altering source files.

### Situation C — Resuming an Integrated Project
1. Open a project that already contains `docs/PROJECT_STATE.md`.
2. In your AI chat session, send the quick prompt:
   ```text
   Utilise CalmTechnology-DevToolkit.
   Lis PROJECT_STATE.md, vérifie l'état réel du projet et propose la prochaine étape.
   Ne modifie pas le code.
   ```
3. The assistant reads the living project memory, checks recent changes, confirms protected validated features, and suggests the next bounded action.

---

## 3. Core Principles to Keep in Mind
1. **Never code without requirements**: Formulate `REQ-F-xxx` before modifying source code.
2. **Consult `PROJECT_STATE.md` first**: Keep it concise; it is the single source of truth across AI chat sessions.
3. **Zero fabrication of test results**: An unexecuted test is strictly `NOT_RUN` (or `BLOCKED` if equipment is missing). Compilation success does not prove functional runtime validity.
4. **Report missing paths**: If the assistant cannot access the toolkit path, it must signal the error immediately rather than pretending to load it.

---

## 4. Next Steps
- Consult the [User Guide](USER_GUIDE.md) / [Guide utilisateur (FR)](USER_GUIDE.fr.md).
- Explore the [CoreS3-RuleBot Case Study](../examples/CoreS3-RuleBot/README.md).
- Check the [Quality Gates Specification](QUALITY_GATES.md).
