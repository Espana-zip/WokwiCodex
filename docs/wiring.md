# Wiring and GPIO Mapping

This document maps the provided Wokwi design to Raspberry Pi Pico W GPIO usage.

## High-Level Topology

- Keypad columns `C1..C4` are connected to GPIO pins and scanned by firmware.
- Keypad rows `R1..R4` are connected to GPIO pins and also tied to 3V3 via 1k pull-up resistors.
- Each LED anode is driven by a GPIO through a 220Ω resistor.
- All LED cathodes are tied to common GND.

## Keypad GPIO Map

| Keypad Signal | Pico W GPIO |
|---|---|
| C1 | GP19 |
| C2 | GP18 |
| C3 | GP17 |
| C4 | GP16 |
| R1 | GP26 |
| R2 | GP22 |
| R3 | GP21 |
| R4 | GP20 |

## LED GPIO Map

| LED Label | Color | Pico W GPIO |
|---|---|---|
| 1 | Blue | GP11 |
| 2 | Blue | GP10 |
| 3 | Blue | GP9 |
| 4 | Blue | GP8 |
| 5 | Blue | GP7 |
| 6 | Blue | GP6 |
| 7 | Blue | GP5 |
| 8 | Blue | GP4 |
| A | Red | GP3 |
| B | Red | GP2 |
| C | Red | GP28 |
| D | Red | GP27 |

## Power and Ground

- 3V3 is routed to a 4x 1k resistor network feeding keypad rows (pull-up arrangement).
- LED cathodes connect to `GND`.

## Notes / Assumptions

- The mapping above is derived from the provided `diagram.json` connection list.
- Electrical behavior (active-high/active-low logic) must follow the original firmware implementation.
