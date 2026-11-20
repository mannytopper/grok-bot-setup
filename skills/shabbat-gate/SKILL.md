---
name: shabbat-gate
description: >-
  Use at the start of any routine, reminder or scheduled job in any of the
  user's bots, to decide whether it may run or message the user, because nothing
  runs or reaches him on Shabbat or Yom Tov.
---
# Shabbat / Yom Tov gate

The user is Orthodox. Nothing runs or reaches him on Shabbat or Diaspora Yom Tov (America/New_York).

## Check
```bash
python3 /workspace/common/shabbat_gate.py            # today, ET
python3 /workspace/common/shabbat_gate.py --evening  # also counts Friday / Erev Yom Tov after candle lighting
python3 /workspace/common/shabbat_gate.py --date YYYY-MM-DD
```
- Prints JSON `{skip, date, reason?, error?}`. Exit code 0 means run; 10 means skip.
- Yom Tov: Rosh Hashana, Yom Kippur, Sukkot I–II, Shmini Atzeret, Simchat Torah, Pesach I, II, VII, VIII, Shavuot I–II. Chol HaMoed and Erev days are not Yom Tov (use `--evening` for jobs that run after about 3 PM on an Erev day).
- If hebcal.com is unreachable, Saturday is still caught offline and a weekday is allowed to run, with `error` set; mention the error only if something else needs the user.
- `/workspace/common/hebcal_check.py` is the older date-only version that live routines already call. Its output is the same shape, so either works.

## On skip
End the run silently: no message, no email, no retry loop. If the job has to happen, it runs on the next allowed day.
