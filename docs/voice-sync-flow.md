# Voice Sync Flow

Clock sync is a special case and requires more user rigor than ordinary voice commands.

Do not rely on Home Assistant Assist staying in a multi-turn listening state. Every follow-up should use a fresh wake word and a complete phrase.

## Preferred command set

```text
OK Nabu, sync the clock
OK Nabu, sync clock from 9 40
OK Nabu, halt clock sync
OK Nabu, cancel clock sync
OK Nabu, continue clock sync
OK Nabu, proceed anyway
```

## Avoid ambiguous short replies

```text
yes
no
halt
wait
9 40
```

## Desired behavior

### 1. Prompt

User says:

```text
OK Nabu, sync the clock
```

Assistant responds:

```text
Sure. Clock sync requires an exact displayed time. Please say: OK Nabu, sync clock from 9 40.
```

### 2. Displayed time supplied

User says:

```text
OK Nabu, sync clock from 9 40
```

Automation calculates forward-only correction from displayed time to current local Home Assistant time.

### 3. Corrections of 60 minutes or less

Assistant says:

```text
I will advance the clock X minutes. To cancel, say: OK Nabu, halt clock sync. I will start in 20 seconds.
```

Home Assistant waits 20 seconds before starting motor movement.

### 4. Cancel

If the user says:

```text
OK Nabu, halt clock sync
```

during the pending window, cancel the movement.

### 5. Corrections over 60 minutes

Assistant says:

```text
This correction is X minutes. It would be faster to manually set the clock to [current time minus 1 hour], then let me advance it one hour. After adjusting the dial, say: OK Nabu, continue clock sync. Or say: OK Nabu, proceed anyway.
```

### 6. Continue after manual adjustment

If the user says:

```text
OK Nabu, continue clock sync
```

then advance 60 minutes.

### 7. Proceed anyway

If the user says:

```text
OK Nabu, proceed anyway
```

then proceed with the original long correction.
