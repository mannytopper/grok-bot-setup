---
name: morning-parts
description: >-
  Use when deciding which parts of the morning combined run apply on a given
  America/New_York date (calendar dashboard, rundown, inbox digest, Tesla watch,
  domain digest, Mon/Wed/Fri X watch), before calling those scripts.
---
# Morning parts (no AI)

```bash
python3 /workspace/common/morning_parts.py
python3 /workspace/common/morning_parts.py --date YYYY-MM-DD
```

Prints JSON with `scheduled` and `parts` booleans for parts A to F. Saturday gives all false.
Always pair with `routine_gate` or `shabbat_gate` before acting. Never sends.

## Test
`python3 /workspace/common/morning_parts.py --selftest`
