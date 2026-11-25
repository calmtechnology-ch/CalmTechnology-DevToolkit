# Requirements Specification: CoreS3-RuleBot

## 1. Traceability & Conventions
- Every functional requirement uses the prefix: `REQ-F-xxx`
- Every non-functional requirement uses the prefix: `REQ-NF-xxx`
- Verification Statuses: `PROPOSED`, `ACCEPTED`, `IMPLEMENTED`, `VALIDATED`, `REJECTED`.
- Note: In this educational example, status is `IMPLEMENTED` pending execution and empirical test capture in target repository.
- All requirements mapped to tests in `docs/TEST_PLAN.md`.

---

## 2. Functional Requirements (`REQ-F-xxx`)

### `REQ-F-001`: French Text Normalization
- **Description**: The system shall normalize French UTF-8 input strings by converting to lowercase, stripping diacritics (`é` -> `e`, `à` -> `a`, `ç` -> `c`, `œ` -> `oe`), removing punctuation, and collapsing consecutive whitespace.
- **Priority**: P0 (MVP)
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. `"SALUT !"` normalizes to `"salut"`.
  2. `"À l'aide, s'il vous plaît"` normalizes to `"a l aide s il vous plait"`.
- **Mapped Tests**: `SYS-001`, `SYS-003`, `SYS-008` (Execution pending in target repo)

### `REQ-F-002`: Greeting Intent Resolution
- **Description**: The system shall resolve standard greeting keywords (`bonjour`, `salut`, `coucou`, `hello`, `hey`) to intent `GREETING` and return an appropriate polite response.
- **Priority**: P0 (MVP)
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. `"bonjour"` resolves to `GREETING`.
  2. `"salut"` resolves to `GREETING`.
- **Mapped Tests**: `SYS-001`, `SYS-002` (Execution pending in target repo)

### `REQ-F-003`: Typo Tolerance (Bounded Edit Distance)
- **Description**: The system shall recognize target keywords with up to 1 character substitution or omission if configured, without triggering false positives on phonetically or orthographically distinct words.
- **Priority**: P1
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. `"salat"` resolves to `GREETING` (distance 1 from `"salut"`).
  2. `"salade"` is NOT recognized as `GREETING` (resolves to `UNKNOWN`).
- **Mapped Tests**: `SYS-004`, `REG-001` (Execution pending in target repo)

### `REQ-F-004`: Rejection of Unknown Inputs
- **Description**: Any input string that does not match configured rules or falls below confidence thresholds shall resolve to intent `UNKNOWN` with a polite fallback message.
- **Priority**: P0 (MVP)
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. `"quel est le sens de la vie"` resolves to `UNKNOWN`.
  2. Empty string `""` is cleanly rejected without crash.
- **Mapped Tests**: `SYS-005`, `SYS-006` (Execution pending in target repo)

### `REQ-F-005`: Safe Long Input Handling
- **Description**: The system shall safely truncate or bound any input exceeding buffer limits (e.g., 256 bytes) without buffer overrun or stack corruption.
- **Priority**: P0 (MVP)
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. A 1000-character input is safely processed within bounded memory.
- **Mapped Tests**: `SYS-007` (Execution pending in target repo)

### `REQ-F-006`: Ambiguity & Concurrency Resolution
- **Description**: If an input triggers two conflicting action rules (e.g., conflicting commands), the system shall resolve deterministically or declare an explicit ambiguity rather than executing dangerous actions.
- **Priority**: P1
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. Input with conflicting intents yields explicit rejection or priority-based resolution.
- **Mapped Tests**: `SYS-009` (Execution pending in target repo)

---

## 3. Non-Functional Requirements (`REQ-NF-xxx`)

### `REQ-NF-001`: CoreS3 Native Display Orientation
- **Description**: The firmware shall render on the CoreS3 ILI9342 display in native landscape `320x240` using `M5.Display.setRotation(0)`.
- **Priority**: P0 (MVP)
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. Display width is 320, height is 240. Touch coordinates match visual widgets.
- **Mapped Tests**: `MAT-001` (Blocked: Physical hardware unavailable)

### `REQ-NF-002`: Internal SRAM Budget & Zero Heap Leak
- **Description**: Core dialogue processing shall allocate zero dynamic heap memory during query execution. Memory degradation across 100 requests shall be <= 0 bytes.
- **Priority**: P0 (MVP)
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. `heap_caps_get_free_size(MALLOC_CAP_INTERNAL)` remains stable after 100 queries.
- **Mapped Tests**: `MAT-002` (Blocked: Physical hardware unavailable)

### `REQ-NF-003`: Execution Latency
- **Description**: Intent resolution time on ESP32-S3 @ 240 MHz shall not exceed 1000 microseconds (1 ms).
- **Priority**: P1
- **Status**: IMPLEMENTED
- **Acceptance Criteria**:
  1. Profiling timer measures < 1 ms average execution latency.
- **Mapped Tests**: `PERF-001` (Execution pending in target repo)
