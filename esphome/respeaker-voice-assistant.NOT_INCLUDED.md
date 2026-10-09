# ReSpeaker Voice Assistant YAML Not Included

The full ReSpeaker ESPHome YAML is intentionally not included in this initial scaffold because it may contain device-specific settings or sensitive configuration.

Known project details:

- Device: Seeed ReSpeaker Lite / XIAO ESP32-S3
- Wake word: `OK Nabu`
- External LED: WS2811 or compatible
- External LED pin: GPIO4 / D3
- GPIO3 was unreliable and should not be used for the external LED
- Original radio power switch powers the ReSpeaker/audio branch

When adding the full YAML, remove all secrets, keys, IP addresses, and private network details before committing.
