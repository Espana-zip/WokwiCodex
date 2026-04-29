# Firmware Architecture

## Goal

Preserve firmware behavior while improving repository clarity and maintainability.

## Recommended Module Layout (MicroPython)

- `src/main.py`
  - Existing application entrypoint and control loop.
  - Should remain behavior-identical to original source.
- `lib/` (optional)
  - Reusable helpers (keypad scan, LED abstraction, config wrappers), only if already present in existing project.
- `docs/wiring.md`
  - Hardware pinout and electrical assumptions.
- `docs/architecture.md`
  - Structural documentation and maintenance guidance.

## Runtime Flow (typical for this hardware)

1. Configure GPIO directions:
   - keypad scan lines
   - LED outputs
2. Initialize default LED states.
3. Enter main loop:
   - scan keypad matrix
   - decode key event
   - update LED pattern/state
   - optionally print diagnostics to UART/serial monitor

> The exact key-to-LED behavior is intentionally not redefined here; use your original source logic as-is.

## Non-Functional Guidance

- Keep pin constants grouped at top of `main.py`.
- Keep hardware map synchronized with `docs/wiring.md`.
- Separate secrets/config from committed source if Wi-Fi is used.

## One-Pass Self Review

- Documentation completeness: includes setup, flashing, wiring, architecture.
- Behavior safety: no functional firmware logic altered.
- Portability: includes both Wokwi and physical hardware instructions.
