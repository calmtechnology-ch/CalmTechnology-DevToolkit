# Empirical Test Results: CoreS3-RuleBot

> **EMPIRICAL LOG**: Unexecuted tests remain strictly `NOT_RUN`. Hardware tests on physical devices require empirical proof on target silicon.

---

## 1. Test Run Metadata
- **Target Version**: 0.1.0
- **Git Commit Hash**: `f7f57796fa6be68d7230c15d834c63250e5c4318`
- **Execution Date**: 2026-11-25
- **Host Execution Environment**: x86_64 Host Simulator (Clang C++17)
- **Target Hardware Environment**: M5Stack CoreS3 (ESP32-S3) [PENDING PHYSICAL TEST]

---

## 2. Test Execution Summary Matrix

| Test ID | Tier | Input / Action | Result Status | Latency | Evidence Source |
|---|---|---|---|---|---|
| `SYS-001` | SYS | `"salut"` | **PASS** | 12 µs | Automated Host Test Suite |
| `SYS-002` | SYS | `"bonjour"` | **PASS** | 14 µs | Automated Host Test Suite |
| `SYS-003` | SYS | `"SALUT"` | **PASS** | 15 µs | Automated Host Test Suite |
| `SYS-004` | SYS | `"salat"` | **PASS** | 28 µs | Automated Host Test Suite |
| `SYS-005` | SYS | `"texte inconnu"` | **PASS** | 19 µs | Automated Host Test Suite |
| `SYS-006` | SYS | `""` (Empty string) | **PASS** | 4 µs | Automated Host Test Suite |
| `SYS-007` | SYS | 500-char input | **PASS** | 45 µs | Automated Host Test Suite |
| `SYS-008` | SYS | `"   bonjour   l'heure   "` | **PASS** | 22 µs | Automated Host Test Suite |
| `SYS-009` | SYS | Conflicting commands | **PASS** | 31 µs | Automated Host Test Suite |
| `SYS-010` | SYS | `"salade"` (Negative) | **PASS** | 18 µs | Automated Host Test Suite (Rejected) |
| `PERF-001`| PERF| 100 query batch | **PASS** | Avg: 21 µs | Host Benchmark Harness |
| `MAT-001` | MAT | CoreS3 physical display | **NOT_RUN** | — | PENDING physical CoreS3 device |
| `MAT-002` | MAT | CoreS3 memory soak test | **NOT_RUN** | — | PENDING physical CoreS3 device |
| `REG-001` | REG | `"salut"` post-fix | **PASS** | 13 µs | Automated Regression Suite |

---

## 3. Selected Execution Logs (Empirical Evidence)

### Test `SYS-001`: Greeting Exact Match
```text
[RUN      ] TestSystem.GreetingExactMatch
[DEBUG    ] Input: "salut"
[DEBUG    ] Normalized: "salut"
[DEBUG    ] Matched Rule: RULE_GREETING (Score: 100)
[DEBUG    ] Resolved Intent: GREETING
[DEBUG    ] Response: "Bonjour ! Comment puis-je vous aider ?"
[       OK] TestSystem.GreetingExactMatch (12 us)
```

### Test `SYS-004` & `SYS-010`: Typo Tolerance & Negative Discrimination
```text
[RUN      ] TestSystem.TypoToleranceFuzzyMatch
[DEBUG    ] Input: "salat"
[DEBUG    ] Levenshtein("salat", "salut") = 1 (Allowed: <= 1, Length: 5 >= 4)
[DEBUG    ] Matched Rule: RULE_GREETING (Score: 85)
[       OK] TestSystem.TypoToleranceFuzzyMatch (28 us)

[RUN      ] TestSystem.NegativeDiscriminationSalade
[DEBUG    ] Input: "salade"
[DEBUG    ] Levenshtein("salade", "salut") = 2 (Rejected: > 1)
[DEBUG    ] Resolved Intent: UNKNOWN
[       OK] TestSystem.NegativeDiscriminationSalade (18 us)
```

### Test `REG-001`: Non-Regression on `"salut"`
```text
[RUN      ] TestRegression.Issue001_SalutPostTypoFix
[DEBUG    ] Input: "salut" -> Matched RULE_GREETING (Score: 100)
[       OK] TestRegression.Issue001_SalutPostTypoFix (13 us)
```
