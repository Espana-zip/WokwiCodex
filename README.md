# Raspberry Pi Pico W Keypad + 12-LED Controller

Documentation-first repository structure for a Raspberry Pi Pico W project that reads a 4x4 matrix keypad and controls 12 discrete LEDs.

> **Important:** The application logic is intentionally not rewritten in this refactor. Keep your existing firmware behavior unchanged by placing your original source file in `src/main.py`.

## Proposed Repository Structure (MicroPython)

```text
.
├── README.md
├── diagram.json
├── src/
│   └── main.py          # your existing application logic (unchanged)
├── lib/                 # optional MicroPython helper modules
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Hardware Features

- Raspberry Pi Pico W (RP2040)
- 4x4 membrane keypad (8 GPIO lines)
- 12 LEDs (8 numeric + 4 alpha indicators)
- Current limiting on each LED (220Ω)
- Keypad row pull-up network (4x 1kΩ to 3V3)

## Components List (from diagram)

- 1x Raspberry Pi Pico / Pico W board
- 1x 4x4 membrane keypad
- 12x LEDs:
  - 8x blue (labels: 1..8)
  - 4x red (labels: A..D)
- 12x 220Ω resistors (LED series resistors)
- 4x 1kΩ resistors (keypad row pull-ups)

## Quick Start (Wokwi)

1. Open Wokwi and create/import a Pico project.
2. Copy `diagram.json` into the project.
3. Put your original firmware into `src/main.py` (or `main.py` at root if your existing simulator setup expects that).
4. Start simulation and open Serial Monitor for diagnostics.

## Quick Start (Real Pico W Hardware)

1. Flash the latest MicroPython UF2 for **Raspberry Pi Pico W**.
2. Mount the board as USB storage (`RPI-RP2`) while in BOOTSEL mode.
3. Copy firmware files:
   - `src/main.py` -> `main.py` on device
   - any `lib/*` helpers -> `/lib` on device
4. Reset board and validate keypad/LED behavior.

## Wi-Fi Notes (if your firmware uses Wi-Fi)

- Store credentials outside tracked files (for example `secrets.py`, excluded via `.gitignore`).
- Recommended pattern in `main.py`:
  - `from secrets import WIFI_SSID, WIFI_PASSWORD`
- Never hard-code or commit credentials.

## C/C++ Variant (if needed)

If your real source is Pico SDK C/C++, use this structure instead:

```text
.
├── CMakeLists.txt
├── include/
├── src/
└── docs/
```

Keep source logic unchanged and only reorganize files/documentation.
