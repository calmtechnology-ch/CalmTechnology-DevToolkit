# Technical Profile: Generic ESP32 Architecture

## 1. Hardware Architecture & Memory Characteristics
- **CPU Architecture**: Dual-core Xtensa LX6 (or single-core variants), 160 or 240 MHz.
- **Internal SRAM**: ~520 KB total, but ~320 KB usable by application (after ROM, RTOS, and Wi-Fi stack reservation).
- **External PSRAM**: Optional (up to 4 MB or 8 MB via SPI/QSPI).
- **Flash Memory**: Typically 4 MB to 16 MB external SPI Flash with memory-mapped execution (XIP).

### Internal SRAM vs. PSRAM Rules
- **DMA Buffers MUST use Internal SRAM**: Any buffer used for SPI, I2S, or UART DMA transfers must be allocated from internal DMA-capable SRAM (`MALLOC_CAP_DMA | MALLOC_CAP_INTERNAL`). PSRAM cannot be targeted directly by ESP32 DMA engines.
- **Wi-Fi / Bluetooth Buffers**: Internal SRAM is consumed heavily (~60-100 KB) when Wi-Fi and TCP/IP (lwIP) stacks are active.
- **Heap Fragmentation**: Frequent dynamic allocation (`malloc` / `free` or `std::string` / `std::vector`) creates fatal heap fragmentation on 32-bit embedded platforms. Use static buffers, fixed pools, or reserve memory upfront.

---

## 2. FreeRTOS & Concurrency Model
- **Task Pinning**:
  - `Core 0`: Dedicated to Wi-Fi, Bluetooth, and network stack processing.
  - `Core 1`: Application domain logic, sensor polling, and UI loops.
- **Task Priorities**:
  - Keep low-priority worker tasks between priority `1` and `3`.
  - Audio and real-time processing between `4` and `8`.
  - Never run an infinite loop at priority > `1` without cooperative yields (`vTaskDelay` or `taskYIELD()`).
- **Task Watchdog Timer (TWDT)**:
  - Default timeout is typically 5 seconds.
  - Any loop exceeding 5 seconds without yielding triggers an immediate hardware reboot.

---

## 3. Peripheral Bus Management
- **I2C Bus**:
  - Standard speed: 100 kHz (`Standard-mode`) or 400 kHz (`Fast-mode`).
  - Use proper physical pull-up resistors (typically 2.2kΩ to 4.7kΩ).
  - Mutex protection is mandatory if multiple FreeRTOS tasks access the same I2C bus.
- **SPI Bus**:
  - Isolate high-speed display transfers from slower SPI sensors.
  - Respect maximum clock frequencies specified in device datasheets.
- **UART / Serial**:
  - Use ring buffers for incoming streams to avoid buffer overruns at 115200+ baud.

---

## 4. Measurement & Profiling Protocols
Never guess heap usage. Use exact runtime measurement APIs:
```cpp
#include <esp_system.h>
#include <esp_heap_caps.h>

// Measure free internal SRAM
size_t free_internal = heap_caps_get_free_size(MALLOC_CAP_INTERNAL);
size_t min_free_internal = heap_caps_get_minimum_free_size(MALLOC_CAP_INTERNAL);

// Measure free PSRAM (if installed)
size_t free_psram = heap_caps_get_free_size(MALLOC_CAP_SPIRAM);

// Monitor FreeRTOS stack high water mark (unused bytes remaining)
UBaseType_t stack_remaining = uxTaskGetStackHighWaterMark(NULL);
```

---

## 5. Non-Blocking Design Guidelines
- Never use blocking delays (`delay()` or busy waits) in main execution paths.
- Employ state machines, event queues, and non-blocking timers (`esp_timer`).
- Always check return codes of ESP-IDF functions: check `esp_err_t == ESP_OK`.
