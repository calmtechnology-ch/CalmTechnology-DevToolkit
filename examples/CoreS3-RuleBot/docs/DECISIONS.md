# Architecture Decision Records: CoreS3-RuleBot

## ADR Registry

| ADR ID | Date | Status | Title |
|---|---|---|---|
| `ADR-001` | 2026-11-20 | ACCEPTED | Hybrid Token Matcher with Bounded Levenshtein Typo Tolerance |
| `ADR-002` | 2026-11-20 | ACCEPTED | CoreS3 Display Orientation Native Landscape (`setRotation(0)`) |
| `ADR-003` | 2026-11-20 | ACCEPTED | Declarative Rule Compilation into Constexpr Tables |

---

## `ADR-001`: Hybrid Token Matcher with Bounded Levenshtein Distance
- **Status**: ACCEPTED
- **Date**: 2026-11-20
- **Related Requirements**: `REQ-F-001`, `REQ-F-002`, `REQ-F-003`, `REQ-NF-002`

### 1. Context
We need a natural command recognition engine running on ESP32-S3 that tolerates minor typos (e.g., "salat" for "salut") while preventing false positives, maintaining execution time < 1 ms, and consuming minimal RAM.

### 2. Alternatives
1. *Full Levenshtein Edit Distance across entire sentence*: High CPU cost, matches false positives on short sentences.
2. *Exact Keyword Trie*: Ultra fast, but zero tolerance for minor typos or user keyboard slips.
3. *Character Transition DFA*: Extremely complex to update and maintain.

### 3. Decision
Implement a **Hybrid Token Matcher**:
- Tokenize normalized input on spaces into individual words.
- Primary matching: Exact match against keyword tables.
- Secondary matching (typo tolerance): If exact match fails, evaluate Levenshtein distance on words >= 4 characters with a maximum edit distance of 1.
- Restrict typo tolerance to designated intent keywords and enforce negative rejection on known confusing words (e.g., "salade").

### 4. Consequences
- **Pros**: Sub-millisecond execution; zero heap allocations; high accuracy.
- **Cons**: Requires maintainer to specify minimum word length for fuzzy matching.

---

## `ADR-002`: M5Stack CoreS3 Display Orientation (Native Landscape)
- **Status**: ACCEPTED
- **Date**: 2026-11-20
- **Related Requirements**: `REQ-NF-001`

### 1. Context
The M5Stack CoreS3 features an ILI9342C 320x240 LCD panel. Developers often incorrectly apply `M5.Display.setRotation(1)` assuming it activates landscape mode.

### 2. Decision
In CoreS3 firmware, use **`M5.Display.setRotation(0)`**.
- Native hardware orientation is ALREADY landscape 320x240 at rotation 0.
- `setRotation(1)` rotates the display to portrait 240x320 and flips the capacitive touch coordinate mapping.

### 3. Consequences
- Guarantees correct display layout and perfect alignment between visual buttons and FT6336U touch coordinates.

---

## `ADR-003`: Declarative Rule Compilation into Constexpr Tables
- **Status**: ACCEPTED
- **Date**: 2026-11-20
- **Related Requirements**: `REQ-NF-002`

### 1. Context
Dynamic JSON parsing on microcontroller boot consumes significant RAM and CPU.

### 2. Decision
Use an offline Python tool (`tools/generate_rules.py`) to compile declarative rules from `rules/rules.json` into a static C++ header `engine/generated_rules.hpp` containing `constexpr` string tables placed in Flash memory.
