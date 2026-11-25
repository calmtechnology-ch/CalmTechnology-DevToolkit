# Technical Profiles Catalog

Technical profiles supply platform-specific constraints, hardware characteristics, memory budgets, and best practices. A technical profile **augments** skills with concrete constraints — it does not replace a skill.

---

## Profile Directory

| Profile | Target Environment | Key Technical Focus | Primary Skills Augmented |
|---|---|---|---|
| [`esp32.md`](esp32.md) | Espressif ESP32 Architecture | Internal SRAM, FreeRTOS tasks, WDT, Wi-Fi, non-blocking I/O | `embedded-engineer`, `software-architect` |
| [`cores3.md`](cores3.md) | M5Stack CoreS3 (ESP32-S3) | 320x240 LCD (native landscape `setRotation(0)`), PSRAM, touch, audio | `embedded-engineer`, `ui-designer` |
| [`voice-application.md`](voice-application.md) | Voice Interfaces & HCI | Audio pipeline, VAD, STT, TTS, barge-in, latency, API keys | `software-architect`, `test-engineer` |
| [`web-application.md`](web-application.md) | Modern Web Applications | Frontend state, network resilience, a11y, CSP, responsive design | `ui-designer`, `software-architect` |
| [`electron.md`](electron.md) | Desktop Electron Apps | Main/renderer isolation, preload IPC, process security | `software-architect`, `code-auditor` |
| [`python.md`](python.md) | Python Applications & Engines | Virtualenvs, packaging, type hints, structured logging, pytest | `software-architect`, `test-engineer` |

---

## How to Apply a Profile
When configuring a development prompt or invoking an engineering skill:
1. Reference the profile file in the prompt context (e.g., `profiles/cores3.md`).
2. Require the AI assistant to adopt the profile's constraints as non-negotiable boundaries.
3. Validate memory, peripheral, and concurrency choices against the profile's checklist.
