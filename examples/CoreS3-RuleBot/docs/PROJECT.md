# Project Charter: CoreS3-RuleBot

## 1. Project Identity
- **Project Name**: CoreS3-RuleBot
- **Current Version**: 0.1.0
- **Organization**: calmtechnology-ch
- **Reference Repository**: https://github.com/calmtechnology-ch/CoreS3-RuleBot
- **License**: MIT
- **Target Platform**: M5Stack CoreS3 (ESP32-S3, ILI9342 LCD 320x240, M5Unified)

---

## 2. Problem Statement & Motivation
Interactive embedded devices often require natural voice or text command interfaces. Traditional approaches rely on cloud LLMs (OpenAI, Anthropic, Gemini), which introduce significant drawbacks:
- 1 to 3 seconds of network latency.
- Total failure during Wi-Fi disconnects or poor signal environments.
- Ongoing API token costs and privacy risks (transmitting private audio or transcripts to third parties).

**CoreS3-RuleBot** implements an ultra-fast, deterministic, rule-based dialogue engine executing 100% locally on the ESP32-S3 microcontroller in under 20 microseconds per query, requiring zero network access.

---

## 3. Goals & Objectives
1. **Deterministic Response**: Guaranteed, reproducible behavior with zero AI hallucinations.
2. **Low Latency**: Intent resolution and text normalization in < 1 ms.
3. **Memory Safety**: Operate within < 100 KB RAM; zero heap allocations during query processing.
4. **CoreS3 Hardware Integration**: Touch screen input, landscape 320x240 rendering, and serial REPL.

---

## 4. Scope Boundaries
### In Scope (v0.1.0)
- French text normalization (accents, uppercase, punctuation, elisions).
- Tokenization and keyword extraction.
- Intent classification: Greetings (`GREETING`), System Status (`STATUS`), Time (`TIME`), Brightness (`BRIGHTNESS`), Help (`HELP`), Unknown (`UNKNOWN`).
- Parameter extraction (brightness percentage 0-100%).
- Negation handling ("ne pas modifier", "sans changer").
- Dual target: Host PC console simulator and M5Stack CoreS3 firmware.

### Out of Scope (v0.1.0)
- Multi-lingual grammar models (French only in v0.1.0).
- Neural speech-to-text models (audio input via serial or simulated text in v0.1.0).
- Cloud API synchronization.
