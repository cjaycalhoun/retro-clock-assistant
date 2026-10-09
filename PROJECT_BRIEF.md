# Project Brief: HiSonic Smart Clock

## Goal

Restore a vintage HiSonic clock/radio into a Home Assistant voice assistant and smart mechanical rolling-digit clock while preserving the physical character of the original device.

## Current system architecture

The project has two main electronics branches:

1. **Voice assistant/audio branch**
   - Seeed ReSpeaker Lite / XIAO ESP32-S3
   - Home Assistant Assist voice satellite
   - Wake word: `OK Nabu`
   - External WS2811 status LED on GPIO4 / D3
   - PAM8403 amplifier
   - Speaker system
   - Original radio power switch powers this branch

2. **Clock motor branch**
   - Generic ESP32 dev board
   - 28BYJ-48 stepper motor
   - ULN2003 driver board
   - Mechanical rolling-digit clock display
   - ESPHome firmware exposes clock-advance API actions to Home Assistant

## Known working state

- ReSpeaker voice assistant works with Home Assistant Assist.
- Manual voice commands for advancing the clock 1 minute and 5 minutes work.
- The clock motor currently works with ESPHome `uln2003` stepper platform.
- GPIO16 is used instead of GPIO5 for reliability.
- The system is physically assembled.

## Current ESPHome motor baseline

See `esphome/hisonic-clock-motor.yaml`.

Important values:

- `pin_a: GPIO19`
- `pin_b: GPIO16`
- `pin_c: GPIO18`
- `pin_d: GPIO17`
- `max_speed: 340 steps/s`
- `2054 steps` per displayed clock minute
- `delay: minutes * 7000`

## Special clock sync requirements

Clock sync is a special-case workflow and requires more user rigor than typical voice commands.

Use explicit commands:

- `OK Nabu, sync the clock`
- `OK Nabu, sync clock from 9 40`
- `OK Nabu, halt clock sync`
- `OK Nabu, cancel clock sync`
- `OK Nabu, continue clock sync`
- `OK Nabu, proceed anyway`

Avoid ambiguous short replies:

- `yes`
- `no`
- `halt`
- `wait`
- `9 40`

## Known issues

- Clock drift: previously observed slow by roughly 10–15 minutes over 3 days.
- GPIO5 caused reliability/boot issues and should be avoided for the motor driver.
- Home Assistant Assist/ReSpeaker can get confused by fragile multi-turn dialog; use explicit wake-word commands instead.
- Current `advance_clock_minutes` action has a 30-minute safety cap.

## Open tasks

- Validate long-duration drift after 2054 steps/min change.
- Build helper-based state machine for sync flow.
- Add 20-second cancel window before motor movement.
- Add large-correction handling.
- Add wiring photos and diagrams.
