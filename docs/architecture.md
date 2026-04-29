# Firmware Architecture

## High-Level Behavior
The firmware scans a 4x4 keypad and controls 12 LEDs according to key events.
The design is polling-based and executes repeatedly inside `loop()`.

## Source Layout
- `src/main.cpp`: complete application logic (provided logic preserved).
- `docs/wiring.md`: hardware and pinout contract.
- `README.md`: usage + flashing paths.

## Module Breakdown (`src/main.cpp`)
1. **Constants and Pin Maps**
   - `LEDS`, `ROWS`, `COLS`
   - `keys` matrix defines keypad symbols.
   - `ledPins`, `rowPins`, `colPins` define GPIO mapping.

2. **Keypad Driver Object**
   - `Keypad keypad = Keypad(makeKeymap(...), ...)`
   - Delegates row/column scan and key decode to library.

3. **Initialization (`setup`)**
   - Configures every LED pin as output.
   - Forces all LEDs OFF at startup.

4. **Main Control Loop (`loop`)**
   - Reads key (`getKey()`).
   - If valid, enters `switch` and executes deterministic LED action:
     - Single-key ON commands: `1..8`, `A..D`
     - Group ON/OFF for blue bank: `9` / `0`
     - Group ON/OFF for red bank: `*` / `#`
   - Sleeps `10 ms` before next iteration.

## Behavioral Constraints
- No Wi‑Fi/network logic.
- No PWM/brightness control.
- LEDs latch state until another command changes them.
- No explicit software debounce besides loop delay.

## Portability Note
Current implementation targets Arduino-compatible RP2040 environments. A Pico SDK-native version would keep the same behavior but replace Arduino + Keypad dependencies.
