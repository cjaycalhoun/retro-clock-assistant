# Setup and draft limitations

## Package contents

The HiSonic package is imported at the repository root: `esphome/` contains the motor baseline, `home-assistant/` contains helpers and six automation drafts, and `docs/`, `notes/`, and `TASKS.md` preserve the hardware history and remaining work. The full ReSpeaker firmware, photos, and wiring diagrams were not supplied.

## Motor baseline

Copy `esphome/hisonic-clock-motor.yaml` into your ESPHome configuration directory and provide `wifi_ssid` and `wifi_password` in your local `secrets.yaml`. Confirm the board and physical GPIO wiring against `wiring.md`, then validate the configuration with your installed ESPHome version before compiling or flashing it. No firmware was flashed during this import.

## Home Assistant drafts

Do not enable the supplied sync automations as a complete workflow yet. Each automation file is one mapping, not a complete `automations.yaml` list. The helper file contains top-level integration keys and must be merged into the corresponding configuration sections or loaded as a Home Assistant package. It does not define the proposed timer.

Known gaps from the supplied files:

- The 20-second cancellation timer is absent. Three automations contain timer TODOs and the timer-finished automation has `triggers: []`.
- The firmware rejects requests above 30 minutes, while the drafts request 60 minutes and larger corrections.
- The compensation formula uses 3.696 seconds per minute from an earlier raw GPIO experiment. The supplied firmware uses a seven-second delay per minute; this formula needs fresh calibration.
- A compensated correction can exceed the helpers' maximum of 720 minutes.
- `running` is cleared immediately after the motor action is sent, without waiting for physical completion. Busy, cancellation, overlapping requests, and restart behavior need integration testing.
- Spoken slots are converted using `int` without an explicit invalid-input fallback. Typed and spoken recognition need validation before motor control is enabled.

Implement and validate these items on the target Home Assistant/ESPHome installation before enabling automated sync. The package's checklist is a roadmap, not a record of completed implementation.
