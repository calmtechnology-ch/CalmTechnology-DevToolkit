# CoreS3-RuleBot — Educational Methodology Example

> **Educational Reference Project**  
> Target Platform: M5Stack CoreS3 (ESP32-S3) | Organization: [calmtechnology-ch](https://github.com/calmtechnology-ch)  
> Official Reference Repository: [https://github.com/calmtechnology-ch/CoreS3-RuleBot](https://github.com/calmtechnology-ch/CoreS3-RuleBot)

---

## 1. Overview & Pedagogical Purpose
This directory contains a complete, production-grade educational case study showing how the **CalmTechnology-DevToolkit** methodology is applied to a real-world embedded software engineering project: **CoreS3-RuleBot**.

### What is CoreS3-RuleBot?
CoreS3-RuleBot is a deterministic, offline, rule-based dialogue engine running locally on the **M5Stack CoreS3** microcontroller without relying on external cloud LLMs, internet connectivity, or heavy neural runtimes.

### Core Engineering Challenges Demonstrated
1. **Physical Resource Constraints**: Operating safely within ESP32-S3 SRAM and PSRAM boundaries with zero heap fragmentation.
2. **Display Orientation Integrity**: Adhering strictly to CoreS3's native landscape `320x240` orientation (`M5.Display.setRotation(0)`).
3. **Deterministic Text Processing**: French diacritics removal, case folding, tokenization, and pattern matching.
4. **Typo Tolerance vs. False Positives**: Managing bounded Levenshtein edit distance without accepting false positives (e.g., distinguishing "salat" from "salade").
5. **Rigorous Quality Gates**: Maintaining strict separation between host simulator tests (`SYS-xxx`), regression tests (`REG-xxx`), and target hardware acceptance tests (`MAT-xxx`).
6. **Transparent Release Reviews**: Demonstrating why an embedded release without physical hardware proof cannot receive a definitive `GO` decision.

---

## 2. Directory Layout

```text
examples/CoreS3-RuleBot/
├── README.md                          # Educational case presentation
├── WALKTHROUGH.md                     # Step-by-step lifecycle walkthrough
├── docs/                              # Living project documentation
│   ├── PROJECT.md                     # Project charter and scope
│   ├── REQUIREMENTS.md                # Functional & non-functional requirements
│   ├── ARCHITECTURE.md                # Engine architecture & trade-off analysis
│   ├── DECISIONS.md                   # ADRs (text engine, rotation, memory)
│   ├── PROJECT_STATE.md               # Definitive living project state
│   ├── TEST_PLAN.md                   # 13 pedagogical test specifications
│   ├── TEST_RESULTS.md                # Empirical test results log
│   └── KNOWN_ISSUES.md                # Defect registry with educational scenario
├── prompts/                           # Prompts used during development
│   ├── INITIAL_DEVELOPMENT.md         # Prompt for initial engine implementation
│   ├── EXAMPLE_AUDIT.md               # Prompt for code quality audit
│   └── EXAMPLE_CORRECTIVE.md          # Prompt for targeted regression fix
└── reports/
    └── EXAMPLE_RELEASE_REVIEW.md      # Formal Go/No-Go release gate evaluation
```

---

## 3. Real Project State vs. Pedagogical Scenarios
The CoreS3-RuleBot educational case study strictly distinguishes between five categories of information:
1. **Facts Verified in Real Repository**: Reference GitHub repository at commit `f7f57796fa6be68d7230c15d834c63250e5c4318`.
2. **Architectural Proposals & ADRs**: Formal trade-offs (`ARCHITECTURE.md`) and accepted architectural choices (`ADR-001` to `ADR-003`).
3. **Pedagogical Scenarios (`ILLUSTRATIVE`)**: The defect scenario `ISSUE-001` and regression test `REG-001` are educational models demonstrating the corrective lifecycle.
4. **Execution Status vs. Empirical Proof**: Test cases (`SYS-001` to `SYS-010`) are cataloged in `TEST_PLAN.md`; unverified in this toolkit workspace (`status: NOT_RUN`, provenance `UNVERIFIED`). Illustrative logs and latency figures in `TEST_RESULTS.md` are marked `ILLUSTRATIVE`.
5. **Hardware Tests Awaiting Confirmation**: CoreS3 physical hardware tests (`MAT-001`, `MAT-002`) are **`BLOCKED`** due to lack of connected physical silicon.
6. **Formal Release Decision**: Demonstrates why Gate QG-06 is **`BLOCKED`** and the release verdict is strictly **`INSUFFICIENT_EVIDENCE`** when hardware verification is pending.
