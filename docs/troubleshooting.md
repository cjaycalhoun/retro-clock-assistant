# Troubleshooting

## Motor logs action but does not move

Likely causes:

- YAML pin does not match physical wire.
- GPIO5/GPIO16 mismatch.
- ULN2003 power missing.
- Motor connector loose.
- Stepper sequence mismatch.
- `release_motor` references wrong pin.

Known fix:

- Use GPIO16 instead of GPIO5.
- Make sure the wire is physically moved from GPIO5 to GPIO16.
- Confirm `release_motor` also references GPIO16.

## ReSpeaker gets stuck with purple LED

Likely cause:

- Home Assistant Assist got stuck in a fragile multi-turn flow.

Fix:

- Avoid multi-turn short answers.
- Use explicit wake-word commands.
- Restart ReSpeaker and/or Home Assistant Assist pipeline if needed.

## Clock drifts slow over days

Likely causes:

- Step count per displayed minute slightly low.
- Mechanical load/slip.
- ESPHome interval alignment.
- Motor movement not completing fully.

Current mitigation:

- Increase from 2048 to 2054 steps per displayed minute.
- Observe drift over 24+ hours.

## Long sync rejected

The current motor action has a 30-minute cap for safety:

```yaml
lambda: 'return minutes > 0 && minutes <= 30;'
```

For final clock sync, use either:

- A dedicated larger-cap sync action, or
- A staged/manual correction path for corrections over 30 minutes.
