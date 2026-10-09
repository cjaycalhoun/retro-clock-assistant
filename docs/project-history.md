# Project History

This project evolved from a vintage HiSonic radio/clock restoration into a Home Assistant voice assistant and smart mechanical clock.

Key milestones:

- ReSpeaker voice assistant integrated with Home Assistant Assist.
- External WS2811 LED moved to GPIO4 / D3 after GPIO3 proved unreliable.
- Original power switch reused for the ReSpeaker/audio branch.
- PAM8403 amp added for internal speaker output.
- Separate ESP32 added for the clock motor.
- Raw GPIO motor stepping was tested, including 1400 microsecond step timing.
- ESPHome `uln2003` stepper platform restored as the current motor baseline.
- GPIO5 was replaced with GPIO16 for improved reliability.
- Clock sync strategy redesigned as a special-case explicit voice flow.
