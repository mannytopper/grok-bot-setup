---
name: routine-gate
description: >-
  Use when a scheduled routine needs a single yes/no on whether to run today
  (weekday allow-list plus Shabbat / Yom Tov), before any fetch, send, or
  browser work.
---
# Routine gate (no AI)

```bash
python3 /workspace/common/routine_gate.py --days Mon,Tue,Wed,Thu,Fri
python3 /workspace/common/routine_gate.py --cron "30 9 * * 5"
python3 /workspace/common/routine_gate.py --days Fri --evening
python3 /workspace/common/routine_gate.py --date YYYY-MM-DD --days Sun,Mon,Tue,Wed,Thu,Fri
```

- Prints JSON `{run, skip, date, weekday, reason?}`.
- Exit **0** = run, **10** = skip, **2** = bad args.
- `--days` takes weekday names. `--cron` uses standard cron day-of-week (0/7 = Sun, 5 = Fri) and converts.
- Does not send mail or write state. Never message the user on a skip.

## Test
`python3 /workspace/common/routine_gate.py --selftest`
