# Wiring

## Clock motor wiring

Current motor mapping:

```text
ESP32 GPIO19 -> ULN2003 IN1 / pin_a
ESP32 GPIO16 -> ULN2003 IN2 / pin_b
ESP32 GPIO18 -> ULN2003 IN3 / pin_c
ESP32 GPIO17 -> ULN2003 IN4 / pin_d
```

GPIO5 was previously used but should be considered deprecated/problematic.

## External LED

```text
ReSpeaker GPIO4 / D3 -> WS2811 data input
```

GPIO3 was unreliable and should not be used for the external LED.

## Audio amp

For PAM8403-style stereo boards:

```text
Left speaker  -> L+ and L-
Right speaker -> R+ and R-
```

Do not tie speaker negatives together. PAM8403 outputs are bridged and speaker negative terminals are not common ground.
