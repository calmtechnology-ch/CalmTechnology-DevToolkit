# Glossary of Engineering & Embedded Terms

## Terms & Abbreviations

- **ADR (Architecture Decision Record)**: A structured document capturing an important architectural choice, its context, alternatives considered, pros, cons, and consequences.
- **Antigravity**: Advanced agentic AI development environment created by Google DeepMind.
- **Barge-In**: A voice interaction capability allowing a human user to interrupt active text-to-speech (TTS) playback by speaking or tapping the screen.
- **CoreS3**: M5Stack CoreS3, an ESP32-S3 powered development hardware platform with integrated 320x240 LCD, capacitive touch screen, dual microphones, speaker, RTC, and PMIC.
- **DMA (Direct Memory Access)**: Hardware mechanism allowing peripherals (SPI, I2S) to transfer data directly to/from internal SRAM without CPU intervention.
- **Evidence Provenance**: Standardized classification of the origin and reliability of test claims:
  - `DIRECTLY_VERIFIED`: Result observed and verified directly in an active execution.
  - `USER_REPORTED`: Result communicated by the human operator (never claimed as autonomous AI observation).
  - `EXTERNAL_REPORTED`: Result originating from an external benchmark, CI, or third-party artifact.
  - `ILLUSTRATIVE`: Pedagogical or hypothetical example; does not constitute validation proof.
  - `UNVERIFIED`: Claim whose empirical proof has not been established.
- **FreeRTOS**: Real-time operating system kernel utilized by ESP-IDF and Arduino-ESP32 for preemptive multi-tasking.
- **FSM (Finite State Machine)**: A computation model consisting of states, inputs, and transitions between states.
- **HAL (Hardware Abstraction Layer)**: A software layer that isolates core business or algorithmic logic from physical hardware driver dependencies.
- **ILI9342C**: LCD controller used in the M5Stack CoreS3. Features native landscape resolution `320x240` at `setRotation(0)`.
- **Levenshtein Distance**: An algorithm measuring the minimum number of single-character edits (insertions, deletions, substitutions) required to transform one string into another.
- **LVGL**: Light and Versatile Graphics Library, an open-source embedded GUI library.
- **M5GFX / M5Unified**: Unified C++ driver and graphics libraries developed by M5Stack for their hardware ecosystem.
- **PlatformIO**: An open-source, multi-framework professional IDE and CLI build system for embedded development.
- **PSRAM (Pseudo-Static RAM)**: External high-density RAM connected to ESP32 via SPI/QSPI/OPI buses.
- **Quality Gate (QG)**: A formal milestone checkpoint ensuring requirements, architecture, build, audit, or test criteria are satisfied before phase progression. Authorized statuses: `PASS`, `FAIL`, `BLOCKED`, `NOT_EVALUATED`, `NOT_APPLICABLE`.
- **Release Decision**: The executive verdict of a formal release evaluation: `GO`, `CONDITIONAL_GO`, `NO_GO`, or `INSUFFICIENT_EVIDENCE`.
- **SRAM**: Static RAM inside the microcontroller. The fastest and most critical memory resource on ESP32 chips.
- **Test Execution Status**: Standardized outcome of a test case: `NOT_RUN`, `PASS`, `FAIL`, `BLOCKED`, `NOT_APPLICABLE`.
- **TWDT (Task Watchdog Timer)**: FreeRTOS hardware watchdog mechanism that reboots the microcontroller if a high-priority task fails to yield or feed the watchdog within a timeout window.
- **VAD (Voice Activity Detection)**: Algorithm detecting the presence or absence of human speech in an audio stream.
