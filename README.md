# HiSonic Smart Clock

A restored vintage HiSonic clock/radio converted into a Home Assistant voice assistant and smart mechanical rolling-digit clock.

## Current status

This repository imports the supplied `hisonic-smart-clock-codex-package.zip` scaffold. Hardware behavior below is reported by that package; it has not been independently tested as part of this import.

The motor configuration is the supplied baseline. The Home Assistant automations are **design drafts, not a ready-to-install sync system**. See [setup and draft limitations](docs/setup.md) before using them.

The system is physically assembled and mostly working.

Working features:

- Home Assistant Assist voice control through a Seeed ReSpeaker Lite / XIAO ESP32-S3.
- Wake word: `OK Nabu`.
- External WS2811 status LED on GPIO4 / D3.
- Original radio power switch controls the ReSpeaker/audio branch.
- PAM8403 amp drives the speaker system.
- Separate ESP32 controls the mechanical rolling-digit clock motor.
- Manual voice commands to advance 1 minute and 5 minutes are working.
- Clock sync is being redesigned as a special-case explicit voice flow.

## Hardware overview

- Vintage HiSonic clock/radio enclosure
- Seeed ReSpeaker Lite / XIAO ESP32-S3 voice satellite
- External WS2811 status LED
- PAM8403 audio amp and speaker system
- Generic ESP32 clock motor controller
- 28BYJ-48 stepper motor
- ULN2003 driver board
- Mechanical rolling-digit clock display

## Firmware overview

- `esphome/hisonic-clock-motor.yaml` contains the current ESPHome motor baseline.
- `esphome/respeaker-voice-assistant.NOT_INCLUDED.md` documents why the full ReSpeaker YAML is not committed yet.

## Home Assistant integration

Home Assistant provides:

- ESPHome API actions for advancing the clock.
- Assist voice commands.
- Planned helper-based state machine for safe clock sync.

Clock sync is intentionally treated as a special case. It requires explicit phrases and avoids ambiguous short replies like `yes`, `no`, or `halt`.

## Security warning

Do not commit secrets, passwords, Wi-Fi credentials, API keys, encryption keys, device tokens, IP addresses, or private network details.

Use placeholders such as:

```yaml
ssid: !secret wifi_ssid
password: !secret wifi_password
```

Do not commit `secrets.yaml`.

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

The existing repository license is [Apache-2.0](LICENSE). The imported HiSonic package was supplied under the [MIT license](LICENSE.hisonic); its original copyright and permission notice are retained here.
