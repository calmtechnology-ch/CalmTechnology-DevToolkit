# Getting Started with CalmTechnology-DevToolkit

Welcome to **CalmTechnology-DevToolkit**. This guide will help you set up and run your first disciplined, AI-assisted development workflow in under 5 minutes.

---

## 1. Prerequisites
- Any modern AI assistant capable of reading Markdown files (such as Google Antigravity, Claude, ChatGPT, Cursor).
- A Git-managed project repository (new or existing).
- No software installation or daemon processes required — the toolkit is 100% file-based Markdown.

---

## 2. Quick Setup in 3 Simple Steps

### Step 1: Make the Toolkit Accessible
Add `CalmTechnology-DevToolkit` to your workspace or place it in a sibling directory:
```text
my-project/
├── docs/                      # Your project documentation
└── CalmTechnology-DevToolkit/ # The toolkit repository
```

### Step 2: Initialize Your Project Documentation
Create a `docs/` folder in your project and copy the essential templates from `CalmTechnology-DevToolkit/templates/`:
- `PROJECT.md`
- `REQUIREMENTS.md`
- `ARCHITECTURE.md`
- `DECISIONS.md`
- `PROJECT_STATE.md`
- `TEST_PLAN.md`
- `TEST_RESULTS.md`
- `KNOWN_ISSUES.md`

### Step 3: Run Your AI Assistant
Direct your AI assistant to read the rules of engagement and the new project workflow:
```text
Please read CalmTechnology-DevToolkit/AGENTS.md.
We are starting a new project following CalmTechnology-DevToolkit/workflows/new-project.md.
Activate the skill CalmTechnology-DevToolkit/skills/project-definition/SKILL.md.
Here is my project concept: [Describe your idea]
```

---

## 3. The 3 Core Rules to Remember
1. **Never code without requirements**: Always define `REQ-F-xxx` before writing functions.
2. **Always read `PROJECT_STATE.md` first**: When opening a fresh chat, point your assistant to `docs/PROJECT_STATE.md` to resume without lost context.
3. **Never accept unexecuted tests**: If a test has not been executed, its status is strictly `NOT_RUN`. Compilation alone does not prove runtime success.

---

## 4. Next Steps
- Read the complete [User Guide](USER_GUIDE.md) / [Guide utilisateur (FR)](USER_GUIDE.fr.md).
- Explore the [CoreS3-RuleBot Example](../examples/CoreS3-RuleBot/README.md) to see a real project in action.
- Check the [Quality Gates Specification](QUALITY_GATES.md).
