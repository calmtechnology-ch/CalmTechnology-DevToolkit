# Known Issues & Defect Registry: CoreS3-RuleBot

> **PEDAGOGICAL NOTICE**: This registry documents an educational defect scenario illustrating how the toolkit handles a real-world bug, regression test, and state update.

---

## Defect Summary Matrix

| Issue ID | Severity | Status | Version Found | Fix Version | Regression Test | Summary |
|---|---|---|---|---|---|---|
| `ISSUE-001` | HIGH | **RESOLVED** | 0.1.0 | 0.1.0.1 | `REG-001` | Keyword "salut" failed exact match after vowel diacritics update |

---

## Detailed Defect Cards

### `ISSUE-001`: Keyword "salut" Failed Match After Vowel Diacritics Update
- **Identifier**: `ISSUE-001`
- **Severity**: HIGH (Regression on P0 Core Requirement)
- **Status**: RESOLVED
- **Version Detected**: 0.1.0
- **Resolved In**: 0.1.0.1
- **Affected File**: `engine/text_utils.cpp`, function `normalize_vowel_tokens()`

#### 1. Description of Defect
During the introduction of extended typo tolerance and vowel normalization, an incorrect substitution rule stripped the letter `'u'` when followed by consonant `'t'`, turning `"salut"` into `"salt"`. Consequently, `"salut"` ceased to match the primary greeting rule.

#### 2. Reproduction Procedure
1. Send input: `"salut"`.
2. Inspect normalized string.
3. Observed result: Normalized to `"salt"`, intent returned was `UNKNOWN`.
4. Expected result: Normalized to `"salut"`, intent returned is `GREETING`.

#### 3. Root Cause Analysis
In `engine/text_utils.cpp`, an experimental vowel-reduction branch intended for phonetic matching was inadvertently active in the standard normalization pipeline:
```cpp
// Defective logic:
if (c == 'u' && next == 't') { skip_char(); } // BUG!
```

#### 4. Remediation & Targeted Fix
Removed the experimental reduction branch, confining vowel handling strictly to diacritics stripping (`ù`, `û` -> `u`).

#### 5. Verification & Non-Regression Test (Pedagogical Scenario)
- **Regression Test**: `REG-001` in `docs/TEST_PLAN.md`.
- **Pedagogical Status**: `RESOLVED (ILLUSTRATIVE SCENARIO)` — Illustrated in walkthrough with target latency of ~13 µs.
- **Evidence Provenance**: `ILLUSTRATIVE` (Hypothetical defect modeled for educational training; not a defect directly detected or verified on hardware in this toolkit repository).
