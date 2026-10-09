# Hardware

## Voice assistant side

- Device: Seeed ReSpeaker Lite / XIAO ESP32-S3
- Purpose: Home Assistant Assist satellite
- Wake word: `OK Nabu`
- External LED: WS2811 or compatible addressable LED
- External LED GPIO: GPIO4 / D3
- Audio output routed to PAM8403 amp
- Original radio power switch controls this branch

## Clock motor side

- Device: Generic ESP32 dev board
- Motor: 28BYJ-48 stepper
- Driver: ULN2003
- Clock type: mechanical rolling-digit / flip-style display, not hands
- No seconds hand
- Display advances by minute increments

## Audio

- Amplifier: PAM8403 or similar small class-D amp
- Speaker system: assembled in the HiSonic enclosure

## Enclosure

Original vintage HiSonic radio/clock enclosure is retained.
