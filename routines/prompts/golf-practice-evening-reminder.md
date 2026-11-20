SKIP WINDOW (added Nov 17, 2026 at Manny's request "Pause golf practice this week", relayed by Connor): if today's America/New_York date is from 2026-11-17 through 2026-11-21, stop silently. Do no work and send no message. From 2026-11-22 on, ignore this line and run normally.

Moved to Routines from Spackler - Golf Practice on Nov 12, 2026. Context: /workspace/routines/context/golf-practice-evening-reminder.md.

Ask-first (Manny, Nov 12, 2026): before opening more than 5 web pages for one task, starting a subagent, re-running a step that already failed twice, or any job expected to take more than 15 minutes, message Manny in one line with what and why, and wait for his yes. Exception: standing deliverables he already approved run as usual.

Remind Manny of tonight's golf practice before his 8:15 PM session (Sunday, Monday, Wednesday).

1. Gate: run `python3 /workspace/common/routine_gate.py --days Sun,Mon,Wed --evening`. Exit 10 means skip (Friday night, Shabbat, Yom Tov, or not a practice day): stop quietly and send nothing.
2. Read his current plan, `/workspace/golf/practice-plan-v2.html` (Crisp Irons: Weekly Practice Plan v2), and find today's night: Sunday is the Sequence night, Monday the Strike night, Wednesday the Transfer night.
3. Send Manny one short message: tonight's theme, then the three blocks (times 8:15 to 9:00 PM, card letter, and what to do) in full plain sentences, and the gear to set out (Garmin R50, bump turn board, divot board, mat). Keep it to a few lines. He's right-handed: always say "lead" or "trail" arm or hand, never "one arm" or "one hand". Don't invent drills that aren't in the plan. If the plan file is missing or unreadable, send one short message saying the reminder couldn't load the plan.

The reminder goes only to Manny in the Routines chat in Grok Bot; no one else. On skipped days, send nothing.
