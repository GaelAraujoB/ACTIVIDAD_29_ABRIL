# Raspberry Pi Pico W Keypad-to-LED Controller

## Overview
This project runs on a **Raspberry Pi Pico W (RP2040)** and maps a **4x4 matrix keypad** to **12 discrete LEDs**.
Each key press turns on/off one LED or a group of LEDs according to fixed logic defined in `src/main.cpp`.

> Firmware logic is preserved exactly from the provided source (Arduino-style `setup()` / `loop()`).

## Repository Structure

```text
.
├── CMakeLists.txt
├── include/
├── src/
│   └── main.cpp
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Features
- 4x4 keypad scanning via `Keypad.h`
- 12 independent LED channels
- Group commands:
  - `9` = turn ON LEDs 1..8
  - `0` = turn OFF LEDs 1..8
  - `*` = turn ON LEDs A..D
  - `#` = turn OFF LEDs A..D
- 10 ms loop debounce/poll delay

## Hardware Components (from `diagram.json`)
- 1x Raspberry Pi Pico / Pico W
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red)
- 12x 220Ω resistors (LED current limiting)
- 4x 1kΩ resistors (keypad row pull-ups to 3V3)
- Jumper wires

## GPIO Mapping Summary
See full table in [`docs/wiring.md`](docs/wiring.md).

## Build/Run Options

### Option A: Wokwi (fastest)
1. Create/open a Raspberry Pi Pico W project in Wokwi.
2. Paste `src/main.cpp` as the sketch source.
3. Ensure the diagram wiring matches `docs/wiring.md`.
4. Start simulation.

### Option B: Real hardware (Arduino-Pico core)
Because firmware uses Arduino APIs (`pinMode`, `digitalWrite`, `delay`, `Keypad.h`):
1. Install **Arduino IDE**.
2. Install **Raspberry Pi Pico/RP2040** board package (Earle Philhower core).
3. Install library: **Keypad** (Library Manager).
4. Select board: **Raspberry Pi Pico W**.
5. Open `src/main.cpp` content in an `.ino` sketch (or include as source in your Arduino project).
6. Upload via USB.

## Pico SDK Note
A pure Pico SDK port would require replacing Arduino/Keypad APIs with Pico SDK GPIO + keypad scan code. This repo intentionally keeps logic unchanged and documents current implementation.

## Wi‑Fi / Secrets
This firmware does **not** use Wi‑Fi or credentials.
