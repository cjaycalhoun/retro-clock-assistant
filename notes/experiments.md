# Experiments

## Motor stepping experiments

- Raw GPIO chunked stepping worked but required careful watchdog-safe loops.
- `delayMicroseconds(1400)` was the fastest reliable raw stepping delay observed.
- Current baseline uses ESPHome `uln2003` component.

## Video timing experiment

A short video with stopwatch reference showed roughly consistent 60-second minute changes over five minutes, but the clock still drifted slow over several days. This suggests small per-minute mechanical/step offset may accumulate over time.
