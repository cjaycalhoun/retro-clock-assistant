# Vintage Smart Clock

A rescued vintage HiSonic clock/radio converted into a voice assistant and smart mechanical rolling-digit clock.

<img width="500" height="500" alt="hisonic-listing-image" src="https://github.com/user-attachments/assets/42ac7460-0d66-46ac-90f4-9ee93d756c6f" />
<img width="500" height="500" alt="HiSonic-smart-clock" src="https://github.com/user-attachments/assets/d0a61dd2-920a-4c22-926f-b9e6895afbb9" />

https://github.com/user-attachments/assets/23634054-3202-4ada-8bc3-0e0b39309527




## Current status

The motor configuration is the supplied baseline. The Home Assistant automations are **design drafts, not a ready-to-install sync system**. See [setup and draft limitations](docs/setup.md) before using them.

The system is physically assembled and mostly working.

Working features:

- Home Assistant Assist voice control through a Seeed ReSpeaker Lite / XIAO ESP32-S3.
- External WS2811 status LED on GPIO4 / D3.
- Original radio power switch controls the ReSpeaker/audio branch.
- PAM8403 amp drives the speaker system.
- Separate ESP32 controls the mechanical rolling-digit clock motor.
- Manual voice commands to advance 1 minute and 5 minutes are working.
- Clock sync is being redesigned as a special-case explicit voice flow.

## Hardware overview

- Vintage HiSonic clock/radio enclosure with functional clock mechanics and speaker
- Seeed ReSpeaker Lite / XIAO ESP32-S3 voice satellite
- External WS2811 status LED
- PAM8403 audio amp
- ESP32 clock motor controller
- 28BYJ-48 stepper motor
- ULN2003 driver board

## Firmware overview

- `esphome/hisonic-clock-motor.yaml` contains the current ESPHome motor baseline.
- `esphome/respeaker-voice-assistant.NOT_INCLUDED.md` documents why the full ReSpeaker YAML is not committed yet.

## Home Assistant integration

Home Assistant provides:

- ESPHome API actions for advancing the clock.
- Assist voice commands.
- Planned helper-based state machine for safe clock sync.

Clock sync is WIP.

## Key docs

- [Setup and draft limitations](docs/setup.md)
- [Project brief](PROJECT_BRIEF.md)
- [Remaining tasks](TASKS.md)
- [Hardware](docs/hardware.md)
- [Wiring](docs/wiring.md)
- [Calibration](docs/calibration.md)
- [Voice sync flow](docs/voice-sync-flow.md)
- [Troubleshooting](docs/troubleshooting.md)

## License

Copyright (c) 2026 Cory Calhoun.

This project is licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/). See [LICENSE](LICENSE) for the full terms.

When sharing or adapting this project, credit Cory Calhoun, link to [retro-clock-assistant](https://github.com/cjaycalhoun/retro-clock-assistant) and the license, and indicate any changes. Shared adaptations must use CC BY-SA 4.0 or a compatible license as specified in the license terms.
