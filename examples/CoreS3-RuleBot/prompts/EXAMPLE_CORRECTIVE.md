# Example Corrective Prompt: CoreS3-RuleBot (`ISSUE-001`)

```markdown
# TASK: Targeted Fix for Regression ISSUE-001 ("salut" Keyword Failure)

You are acting as the Lead Embedded Engineer using `CalmTechnology-DevToolkit/skills/prompt-generator/SKILL.md`.

## Defect Details
- **Issue ID**: `ISSUE-001`
- **Severity**: HIGH (Regression on P0 Requirement `REQ-F-002`)
- **Observed Behavior**: Input `"salut"` returns intent `UNKNOWN` instead of `GREETING`.
- **Root Cause Locus**: `engine/text_utils.cpp`, in function `normalize_vowel_tokens()`.

## Strict Scope Boundaries
- **Permitted File**: Confined strictly to `engine/text_utils.cpp`.
- **Forbidden Files**: All other files in `engine/`, `firmware/`, and `rules/`.
- **Forbidden Actions**: Do NOT add new features or refactor unrelated normalizer functions.

## Verification & Non-Regression
1. Run reproduction test `REG-001`: Must FAIL before fix, and PASS after fix.
2. Run full test suite (`SYS-001` to `SYS-010`): All must PASS.
3. Update `examples/CoreS3-RuleBot/docs/KNOWN_ISSUES.md` marking `ISSUE-001` as RESOLVED.
4. Update `examples/CoreS3-RuleBot/docs/PROJECT_STATE.md`.
```
