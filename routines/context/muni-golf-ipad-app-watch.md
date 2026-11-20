# Muni Golf iPad app watch (owner: Spackler - Golf Practice, folder: muni-golf-ipad-app-watch)

- **Owner bot:** Spackler - Golf Practice
- **Original folder id:** `muni-golf-ipad-app-watch`
- **Enabled state:** Paused (since Nov 4, 2026; not deleted). A paused original stays paused on the copy.
- **Schedule/trigger:** `CRON_TZ=America/New_York 45 6 * * 0` (Sundays around 6:45 AM ET)
- **Timing:** Flexible, 15 minutes early or late
- **Connectors/accounts:** None. The check script hits munigolfsim.com and the App Store.
- **Scripts:** `python3 /workspace/common/routine_gate.py --days Sun`. `python3 /workspace/muni-golf/check.py` (and `--commit` after a new public-release alert). State under `/workspace/muni-golf/`.
- **Skills:** muni-golf-watch, routine-gate
- **Files/state:** State under `/workspace/muni-golf/` as used by check.py.
- **Memory facts:** Alert only when the iPad app is publicly available (a public App Store listing, or the official site clearly saying it is publicly released, not beta/TestFlight/Discord-only). Developer: Malkfleursby Technologies, munigolfsim.com. If still not out after April 30, 2027, send one short end-of-watch message and delete this routine. Do not fall back to a hand check if the script errors.
- **Permissions:** None. Chat only. The prompt tells the run to delete itself after a release alert or after the deadline.
- **Hooks:** None
- **Open issues:** Keep paused until Manny wants it on. Self-delete is in the prompt; do not pause or delete the original as part of this inventory.

## Original prompt (verbatim)

```
Manny wants to know when the Muni Golf Sim (munigolfsim.com, developer Malkfleursby Technologies) iPad app becomes publicly available (a public App Store listing, or the official site clearly saying it is publicly released, not beta/TestFlight/Discord-only). Use the muni-golf-watch and routine-gate skills.

1. Gate: run `python3 /workspace/common/routine_gate.py --days Sun`. Exit 10 means skip (Shabbat, Yom Tov, or wrong day): stop quietly and send nothing.
2. Check: run `python3 /workspace/muni-golf/check.py`. It prints JSON with `released` and `alert_new`.
   - If `alert_new` is true: send Manny one short message in this Grok Bot chat saying the iPad app is out, with a markdown link to the App Store page (and the announcement if the JSON gives one). Then run `python3 /workspace/muni-golf/check.py --commit` to record it, and delete this routine.
   - Otherwise send nothing.
   - If the script errors, send Manny one short message that the watch run failed and why; don't fall back to doing the check by hand.
3. Deadline: if today is after April 30, 2027 and it still isn't out, send Manny one short message that the watch ended with no public iPad release yet, then delete this routine.

Results go only to Manny in this Grok Bot chat (Spackler - Golf Practice); no one else. When nothing has changed, send nothing.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/muni-golf-ipad-app-watch.md for context.

Manny wants to know when the Muni Golf Sim (munigolfsim.com, developer Malkfleursby Technologies) iPad app becomes publicly available (a public App Store listing, or the official site clearly saying it is publicly released, not beta/TestFlight/Discord-only). Use the muni-golf-watch and routine-gate skills.

1. Gate: run `python3 /workspace/common/routine_gate.py --days Sun`. Exit 10 means skip (Shabbat, Yom Tov, or wrong day): stop quietly and send nothing.
2. Check: run `python3 /workspace/muni-golf/check.py`. It prints JSON with `released` and `alert_new`.
   - If `alert_new` is true: send Manny one short message in the Routines chat in Grok Bot saying the iPad app is out, with a markdown link to the App Store page (and the announcement if the JSON gives one). Then run `python3 /workspace/muni-golf/check.py --commit` to record it, and delete this routine.
   - Otherwise send nothing.
   - If the script errors, send Manny one short message that the watch run failed and why; don't fall back to doing the check by hand.
3. Deadline: if today is after April 30, 2027 and it still isn't out, send Manny one short message that the watch ended with no public iPad release yet, then delete this routine.

Results go only to Manny in the Routines chat in Grok Bot; no one else. When nothing has changed, send nothing.
```
