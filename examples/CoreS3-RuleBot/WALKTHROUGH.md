# CoreS3-RuleBot Lifecycle Walkthrough

This document guides you step-by-step through the engineering lifecycle of **CoreS3-RuleBot** as executed using the **CalmTechnology-DevToolkit**.

---

## Phase 1: Project Definition & Requirements (`QG-01`)
1. **Problem Statement**: Cloud-connected LLMs are unsuitable for instantaneous, offline, low-power embedded interaction on M5Stack CoreS3 due to latency, privacy, network failures, and API costs.
2. **Requirements Formulation**:
   - `REQ-F-001` to `REQ-F-005`: Normalization, tokenization, intent recognition, typo tolerance, parameter extraction.
   - `REQ-NF-001` to `REQ-NF-003`: Memory budget (<150 KB internal SRAM), latency (<30 ms), physical CoreS3 landscape orientation (`setRotation(0)`).
3. **Artifacts Produced**:
   - [`docs/PROJECT.md`](docs/PROJECT.md)
   - [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md)
   - [`docs/PROJECT_STATE.md`](docs/PROJECT_STATE.md) (Phase: `DEFINITION`, Gate QG-01: `PASS`)

---

## Phase 2: Architecture & Decision Modeling (`QG-02`)
1. **Architectural Evaluation of Recognition Approaches**:
   - Character Transition Matrix vs. Trie vs. Token-Based Matching vs. Bounded Edit Distance.
   - *Decision (`ADR-001`)*: Hybrid Token Matcher with bounded Levenshtein distance (max distance = 1).
2. **Display Orientation Decision (`ADR-002`)**:
   - CoreS3 hardware ILI9342 panel is natively landscape `320x240` at `setRotation(0)`.
   - Never use `setRotation(1)` (which rotates to portrait `240x320`).
3. **Artifacts Produced**:
   - [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md)
   - [`docs/DECISIONS.md`](docs/DECISIONS.md) (Gate QG-02: `PASS`)

---

## Phase 3: Bounded Implementation (`QG-03`)
1. Generated development prompt: [`prompts/INITIAL_DEVELOPMENT.md`](prompts/INITIAL_DEVELOPMENT.md).
2. Pure C++17 engine implemented cleanly decoupled from hardware.
3. Clean compilation verified on host compiler (GCC/Clang) and PlatformIO (Gate QG-03: `PASS`).

---

## Phase 4: Source Code Audit (`QG-04`)
1. Executed 10-step code audit using [`prompts/EXAMPLE_AUDIT.md`](prompts/EXAMPLE_AUDIT.md).
2. Verified decoupling between domain logic and `M5Unified` hardware layer.
3. Zero `CRITICAL` or `HIGH` vulnerabilities found (Gate QG-04: `PASS`).

---

## Phase 5: Pedagogical Defect & Corrective Release Cycle
1. **Defect Scenario (`ISSUE-001`)**:
   - Introduction of typo tolerance caused keyword "salut" to misclassify after modifying vowel normalization rules.
2. **Corrective Plan**:
   - Formulated minimal fix in tokenizer.
   - Generated precision prompt: [`prompts/EXAMPLE_CORRECTIVE.md`](prompts/EXAMPLE_CORRECTIVE.md).
   - Created regression test `REG-001`.
3. **Non-Regression Verification**:
   - `REG-001` verified passing.
   - Defect resolved in [`docs/KNOWN_ISSUES.md`](docs/KNOWN_ISSUES.md).

---

## Phase 6: Release Gate Review & Formal Verdict (`QG-06`)
1. Conducted release evaluation using `release-reviewer` skill.
2. Review report generated in [`reports/EXAMPLE_RELEASE_REVIEW.md`](reports/EXAMPLE_RELEASE_REVIEW.md).
3. **Formal Verdict**: **`INSUFFICIENT_EVIDENCE`**
   - *Justification*: Host simulator tests passed (`SYS-001` to `SYS-009`), but physical hardware tests on real CoreS3 device (`MAT-001`, `MAT-002`) remain `NOT_RUN`.
   - In accordance with the toolkit's strict rules, an embedded release cannot be declared `GO` without physical hardware verification proof!
