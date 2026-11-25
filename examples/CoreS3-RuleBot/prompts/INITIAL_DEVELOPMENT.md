# Initial Development Prompt: CoreS3-RuleBot

```markdown
# TASK: Implement Core Dialogue Engine for CoreS3-RuleBot

You are acting as the Lead Embedded Software Engineer on the CoreS3-RuleBot project.

## Mandatory Pre-Flight Instructions
1. Read `CalmTechnology-DevToolkit/AGENTS.md`.
2. Read `examples/CoreS3-RuleBot/docs/PROJECT_STATE.md`.
3. Follow `CalmTechnology-DevToolkit/profiles/cores3.md`.

## Target Component
Implement the pure C++17 dialogue engine in `engine/text_utils.cpp` and `engine/dialogue_engine.cpp`.

## Requirements to Fulfill
- `REQ-F-001`: French text normalization (strip UTF-8 accents, lowercase, punctuation).
- `REQ-F-002`: Greeting intent recognition (`salut`, `bonjour`, `hello`).
- `REQ-F-004`: Fallback to `UNKNOWN` on unrecognized inputs.
- `REQ-NF-002`: Zero dynamic heap allocations during `process_query()`.

## Modification Boundaries
- **Permitted Files**: `engine/text_utils.hpp`, `engine/text_utils.cpp`, `engine/dialogue_engine.hpp`, `engine/dialogue_engine.cpp`.
- **Forbidden Files**: `firmware/src/cores3_adapter.cpp`, `rules/rules.json`.

## Acceptance Verification
- Must compile cleanly with `g++ -std=c++17 -Wall -Wextra -Werror`.
- Run tests `SYS-001`, `SYS-002`, `SYS-005`: All must PASS.
- Update `examples/CoreS3-RuleBot/docs/PROJECT_STATE.md` upon completion.
```
