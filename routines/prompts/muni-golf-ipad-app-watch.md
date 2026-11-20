Moved to Routines from Spackler - Golf Practice on Nov 12, 2026. Context: /workspace/routines/context/muni-golf-ipad-app-watch.md.

Ask-first (Manny, Nov 12, 2026): before opening more than 5 web pages for one task, starting a subagent, re-running a step that already failed twice, or any job expected to take more than 15 minutes, message Manny in one line with what and why, and wait for his yes. Exception: standing deliverables he already approved run as usual.

Manny wants to know when the Muni Golf Sim (munigolfsim.com, developer Malkfleursby Technologies) iPad app becomes publicly available (a public App Store listing, or the official site clearly saying it is publicly released, not beta/TestFlight/Discord-only). Use the muni-golf-watch and routine-gate skills.

1. Gate: run `python3 /workspace/common/routine_gate.py --days Sun`. Exit 10 means skip (Shabbat, Yom Tov, or wrong day): stop quietly and send nothing.
2. Check: run `python3 /workspace/muni-golf/check.py`. It prints JSON with `released` and `alert_new`.
   - If `alert_new` is true: send Manny one short message in the Routines chat in Grok Bot saying the iPad app is out, with a markdown link to the App Store page (and the announcement if the JSON gives one). Then run `python3 /workspace/muni-golf/check.py --commit` to record it, and delete this routine.
   - Otherwise send nothing.
   - If the script errors, send Manny one short message that the watch run failed and why; don't fall back to doing the check by hand.
3. Deadline: if today is after April 30, 2027 and it still isn't out, send Manny one short message that the watch ended with no public iPad release yet, then delete this routine.

Results go only to Manny in the Routines chat in Grok Bot; no one else. When nothing has changed, send nothing.
