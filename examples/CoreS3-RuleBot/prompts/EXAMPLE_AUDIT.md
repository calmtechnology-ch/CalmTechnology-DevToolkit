# Example Code Audit Prompt: CoreS3-RuleBot

```markdown
# TASK: Execute Source Code Quality Audit on CoreS3-RuleBot

You are acting as the Lead Code Auditor using `CalmTechnology-DevToolkit/skills/code-auditor/SKILL.md`.

## Target
- **Repository**: `examples/CoreS3-RuleBot`
- **Target Commit**: `f7f57796fa6be68d7230c15d834c63250e5c4318`
- **Profile**: `CalmTechnology-DevToolkit/profiles/cores3.md`

## Audit Protocol
1. Verify that `engine/` contains zero Arduino or M5Stack headers (pure portable C++17).
2. Check `firmware/src/cores3_adapter.cpp` for display rotation: confirm it uses `M5.Display.setRotation(0)` for landscape 320x240, NEVER `setRotation(1)`.
3. Inspect memory allocation patterns in `dialogue_engine.cpp` for heap safety.
4. Check error handling on malformed UTF-8 byte sequences.
5. Record findings in `docs/AUDIT_REPORT.md` and evaluate Quality Gate QG-04.
```
