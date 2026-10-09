# Calibration

## Known calibration information

Earlier raw GPIO stepping tests found:

- `delayMicroseconds(1400)` was the fastest reliable raw GPIO stepping value.
- 10 displayed minutes took 36.96 seconds.
- That equals 3.696 seconds per displayed clock minute.

The current firmware uses ESPHome `uln2003` stepper component instead of the earlier raw GPIO chunked stepping approach.

Current motor settings:

- `max_speed: 340 steps/s`
- `2054 steps` per displayed minute
- `delay: minutes * 7000`

The clock was observed drifting slow by roughly 10–15 minutes over 3 days. This led to increasing steps per displayed minute from 2048 to 2054.

Further long-duration calibration is still needed.

## Calibration table

| Date | Steps/min | Max speed | Delay/min | Observed drift | Notes |
|---|---:|---:|---:|---|---|
| Initial | 2048 | 340 steps/s | 6500 ms | 10–15 min slow over ~3 days | Baseline ESPHome uln2003 |
| Current | 2054 | 340 steps/s | 7000 ms | TBD | GPIO16 fix applied |

## Calibration procedure

1. Set the clock to a known displayed time.
2. Record actual local time.
3. Let the clock run for at least 24 hours.
4. Record displayed clock time and actual local time.
5. Calculate drift.
6. Adjust steps/min slightly:
   - If slow, increase steps/min.
   - If fast, decrease steps/min.
7. Update this document with each result.
