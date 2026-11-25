# Technical Profile: M5Stack CoreS3 (ESP32-S3)

## 1. Hardware Architecture Overview
The **M5Stack CoreS3** is an integrated development device powered by the Espressif **ESP32-S3FN8** (dual-core Xtensa LX7 @ 240 MHz with vector instructions).

- **Flash**: 16 MB SPI Flash.
- **PSRAM**: 8 MB OPI PSRAM (high-speed octal interface).
- **Internal SRAM**: 512 KB (approx. 380 KB usable after RTOS & Wi-Fi).
- **Power Management (PMIC)**: AXP2101 + AW9523 I/O expander.
- **Real-Time Clock (RTC)**: BM8563.
- **IMU**: BMI270 (6-axis accelerometer & gyroscope) + BMM150 (magnetometer).
- **Audio Subsystem**:
  - Dual Microphones: ES7210 I2S audio ADC.
  - Speaker / Amplifier: AW88298 16-bit I2S Class-D amplifier.
- **Display & Touch**:
  - LCD Controller: ILI9342C 2.0-inch TFT LCD, 320x240 pixels.
  - Touch Controller: FT6336U capacitive touch sensor.

---

## 2. Display & Screen Rotation Rule (CRITICAL)

> ### **M5Stack CoreS3 Display Orientation Rule**
> - On the M5Stack CoreS3 (ILI9342C display), the **native hardware orientation is already landscape 320x240 at rotation `0`**.
> - **DO NOT USE `M5.Display.setRotation(1)`** to get landscape mode!
> - Calling `M5.Display.setRotation(1)` rotates the display by 90°, turning it into **portrait mode (240x320)** with inverted touch axes.
> - For standard landscape `320x240` on CoreS3, use **`M5.Display.setRotation(0)`** (or keep the default rotation initialized by `M5.begin()`).

```cpp
// Correct initialization for M5Stack CoreS3
#include <M5Unified.h>

void setup() {
    auto cfg = M5.config();
    M5.begin(cfg);
    
    // Explicitly set or verify rotation 0 for landscape 320x240
    M5.Display.setRotation(0); 
    // M5.Display.width() is 320, M5.Display.height() is 240
}
```

---

## 3. Memory Allocation Rules on ESP32-S3
- **8 MB Octal PSRAM**: Available for large static buffers, font tables, dialogue history buffers, audio ring buffers, and LVGL display buffers.
- **Internal SRAM**: Reserve strictly for:
  - FreeRTOS task stacks.
  - DMA buffers for I2S audio capture (`ES7210`) and audio playback (`AW88298`).
  - DMA buffers for SPI display transfers.
  - Wi-Fi and Bluetooth protocol stack buffers.
- **Allocating in PSRAM**:
  ```cpp
  // Allocating a large buffer in PSRAM
  uint8_t* buffer = (uint8_t*) heap_caps_malloc(64 * 1024, MALLOC_CAP_SPIRAM);
  if (!buffer) {
      // Fallback or error handling
  }
  ```

---

## 4. Audio Subsystem Best Practices
- The **ES7210** microphone ADC and **AW88298** amplifier share the I2S bus.
- In M5Unified, manage audio using `M5.Mic.begin()` / `M5.Speaker.begin()`.
- Set sampling rates appropriately (e.g., 16000 Hz, 16-bit mono for voice recognition).
- Maintain dedicated DMA ring buffers (at least 2 buffers of 512 bytes) in internal SRAM to prevent audio under-runs or crackling.

---

## 5. Touch Interface Best Practices
- The **FT6336U** touch controller communicates over I2C.
- Read touch inputs cooperatively in the main loop or dedicated UI task:
  ```cpp
  M5.update(); // Updates display, buttons, and touch state
  auto detail = M5.Touch.getDetail();
  if (detail.isPressed()) {
      int16_t x = detail.x;
      int16_t y = detail.y;
      // Coordinates are 0..319 and 0..239 in rotation 0
  }
  ```
- Touch zones must have a minimum physical size of 40x40 pixels for finger accuracy.

---

## 6. Recommended PlatformIO Configuration (`platformio.ini`)
```ini
[env:m5stack-cores3]
platform = espressif32@^6.5.0
board = esp32-s3-devkitc-1
framework = arduino
monitor_speed = 115200
board_build.mcu = esp32s3
board_build.f_cpu = 240000000L
board_build.f_flash = 80000000L
board_build.flash_mode = qio
board_build.partitions = default_16MB.csv
build_flags = 
    -DARDUINO_M5STACK_CORES3
    -DBOARD_HAS_PSRAM
    -mfix-esp32-psram-cache-issue
    -O2
lib_deps = 
    m5stack/M5Unified@^0.1.14
    m5stack/M5GFX@^0.1.14
```
