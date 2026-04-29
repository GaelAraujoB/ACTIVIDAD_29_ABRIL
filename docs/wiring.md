# Wiring and GPIO Mapping (Raspberry Pi Pico W)

## Assumptions and Notes
- Mapping is derived from the provided Wokwi `diagram.json` and firmware pin arrays.
- LED anodes are driven from GPIO through 220Ω series resistors.
- All LED cathodes are tied to GND.
- Keypad rows have external 1kΩ pull-ups to 3V3 in the diagram.

## Keypad Connections

| Keypad Signal | Pico W GPIO | Firmware Array |
|---|---:|---|
| C1 | GP19 | `colPins[0]` |
| C2 | GP18 | `colPins[1]` |
| C3 | GP17 | `colPins[2]` |
| C4 | GP16 | `colPins[3]` |
| R1 | GP26 | `rowPins[0]` |
| R2 | GP22 | `rowPins[1]` |
| R3 | GP21 | `rowPins[2]` |
| R4 | GP20 | `rowPins[3]` |

## LED Connections

| Logical LED | Key Label Group | Pico W GPIO | Firmware Index |
|---|---|---:|---:|
| LED1 | `1` | GP11 | `ledPins[0]` |
| LED2 | `2` | GP10 | `ledPins[1]` |
| LED3 | `3` | GP9  | `ledPins[2]` |
| LED4 | `4` | GP8  | `ledPins[3]` |
| LED5 | `5` | GP7  | `ledPins[4]` |
| LED6 | `6` | GP6  | `ledPins[5]` |
| LED7 | `7` | GP5  | `ledPins[6]` |
| LED8 | `8` | GP4  | `ledPins[7]` |
| LED9  | `A` | GP3  | `ledPins[8]` |
| LED10 | `B` | GP2  | `ledPins[9]` |
| LED11 | `C` | GP28 | `ledPins[10]` |
| LED12 | `D` | GP27 | `ledPins[11]` |

## Power / Ground
- LED cathodes: to Pico GND (common).
- Keypad pull-up network (4x 1kΩ): tied to Pico 3V3.

## Wokwi Run Checklist
1. Confirm keypad row/column wiring exactly as table above.
2. Confirm each LED has its own 220Ω resistor.
3. Confirm all LED cathodes go to common GND.
4. Start simulation and press keys `1..9`, `0`, `A..D`, `*`, `#`.
