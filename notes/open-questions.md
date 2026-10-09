# Open Questions

- Does 2054 steps/min correct the 10–15 minute slow drift over 3 days?
- Should the interval be moved from boot-relative `interval: 60s` to Home Assistant wall-clock `time.on_time`?
- Should final sync use a larger-cap dedicated ESPHome API action instead of the 30-minute manual action?
- Is `max_speed: 340 steps/s` optimal under assembled mechanical load?
- Should the motor advance start before the top of the minute so the digit settles at `:00`?
