# Test Plan Specification: CoreS3-RuleBot

## 1. Test Strategy & Classification
This test plan defines the pedagogical verification suite for CoreS3-RuleBot, covering host simulation tests, negative test cases, performance profiling, hardware acceptance tests, and non-regression tests.

All unexecuted tests are initialized to `NOT_RUN`.

---

## 2. Test Cases Specification Matrix

| Test ID | Tier | Input / Condition | Expected Result | Associated Req / Defect | Initial Status |
|---|---|---|---|---|---|
| `SYS-001` | SYS | `"salut"` | Intent `GREETING` | `REQ-F-002` | NOT_RUN |
| `SYS-002` | SYS | `"bonjour"` | Intent `GREETING` | `REQ-F-002` | NOT_RUN |
| `SYS-003` | SYS | `"SALUT"` | Case folding -> Intent `GREETING` | `REQ-F-001`, `REQ-F-002` | NOT_RUN |
| `SYS-004` | SYS | `"salat"` | Typo tolerance -> Intent `GREETING` | `REQ-F-003` | NOT_RUN |
| `SYS-005` | SYS | `"texte inconnu"` | Fallback -> Intent `UNKNOWN` | `REQ-F-004` | NOT_RUN |
| `SYS-006` | SYS | `""` (Empty string) | Clean rejection, no crash | `REQ-F-004` | NOT_RUN |
| `SYS-007` | SYS | 500-character string | Bounded execution, no stack smash | `REQ-F-005` | NOT_RUN |
| `SYS-008` | SYS | `"   bonjour    l'heure   "` | Whitespace collapse & elision | `REQ-F-001` | NOT_RUN |
| `SYS-009` | SYS | Conflicting action commands | Deterministic resolution or ambiguity flag | `REQ-F-006` | NOT_RUN |
| `SYS-010` | SYS | `"salade"` (Negative test) | Rejection -> `UNKNOWN` (No false positive) | `REQ-F-003` | NOT_RUN |
| `PERF-001`| PERF| Batch of 100 queries | Average latency < 1 ms | `REQ-NF-003` | NOT_RUN |
| `MAT-001` | MAT | Execution on physical CoreS3 | Landscape 320x240 LCD rendering, touch OK | `REQ-NF-001` | NOT_RUN |
| `MAT-002` | MAT | 100 queries on CoreS3 | Memory degradation delta == 0 bytes | `REQ-NF-002` | NOT_RUN |
| `REG-001` | REG | `"salut"` post-typo fix | Intent `GREETING` recognized without regression | `ISSUE-001` | NOT_RUN |

---

## 3. Detailed Test Protocols

### `SYS-004`: Typo Tolerance Test
- **Input**: `"salat"`
- **Procedure**: Run dialogue engine with typo tolerance enabled (Levenshtein distance <= 1).
- **Expected Outcome**: Matches keyword `"salut"`, returns intent `GREETING`, confidence score > 80.

### `SYS-010`: Negative Discrimination Test (Anti-False-Positive)
- **Input**: `"salade"`
- **Procedure**: Run dialogue engine with typo tolerance enabled.
- **Expected Outcome**: Despite sharing prefix with `"salut"`, distance is >= 2. Engine MUST reject and return `UNKNOWN`.

### `MAT-001`: CoreS3 Hardware Acceptance Test
- **Target**: Physical M5Stack CoreS3.
- **Preconditions**: Firmware flashed via PlatformIO; USB serial connected.
- **Procedure**:
  1. Boot device and inspect LCD display orientation.
  2. Verify screen dimensions reported are 320 width x 240 height (`setRotation(0)`).
  3. Tap touch buttons and observe responsiveness.
- **Expected Outcome**: Crisp rendering, no screen inversion, correct coordinates.

### `MAT-002`: CoreS3 Memory Leak Soak Test
- **Target**: Physical M5Stack CoreS3.
- **Procedure**: Send 100 consecutive command queries over serial. Read `esp_get_free_heap_size()` before query 1 and after query 100.
- **Expected Outcome**: Free internal SRAM delta <= 0 bytes (zero memory leak).
