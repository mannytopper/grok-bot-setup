# Golf practice evening reminder (owner: Spackler - Golf Practice, folder: golf-practice-evening-reminder)

- **Owner bot:** Spackler - Golf Practice
- **Original folder id:** `golf-practice-evening-reminder`
- **Enabled state:** Paused (week off until Nov 15). Normally enabled. On Nov 10 Manny said to take the week off because he was away. A one-off (`resume-golf-practice-reminder`) turns it back on Sunday, Nov 15 at noon ET.
- **Schedule/trigger:** `CRON_TZ=America/New_York 50 19 * * 0,1,3` (Sunday, Monday, Wednesday at 7:50 PM ET)
- **Timing:** Flexible, 10 minutes early or late
- **Connectors/accounts:** None
- **Scripts:** `python3 /workspace/common/routine_gate.py --days Sun,Mon,Wed --evening` (exit 10 = skip quietly).
- **Skills:** routine-gate, shabbat-gate
- **Files/state:** `/workspace/golf/practice-plan-v2.html` (Crisp Irons: Weekly Practice Plan v2)
- **Memory facts:** Practice Sun/Mon/Wed after 8 PM; Tue/Thu are course days; never Friday night or Saturday. He is right-handed: always say "lead" or "trail" arm or hand, never "one arm" or "one hand". Few drills, full sentences, never invent drills that aren't in the plan. Sunday Sequence (Cards A, B, C), Monday Strike (D, A, B), Wednesday Transfer (review A, B, C, Card A club ladder, Card E random targets on R50). The tape-line weight-shift drill was dropped from Monday on Oct 26. Gear to set out: Garmin R50, bump turn board, divot board, mat. Session 8:15–9:00 PM.
- **Permissions:** None. Chat only. No local execution.
- **Hooks:** None
- **Open issues:** Keep the Routines copy paused until after the Nov 15 noon resume (or until that one-off has run against the correct copy). Do not run a test of this reminder before the evening of Sunday Nov 15. See resume-golf-practice-reminder for the double-run risk.

## Original prompt (verbatim)

```
Remind Manny of tonight's golf practice before his 8:15 PM session (Sunday, Monday, Wednesday).

1. Gate: run `python3 /workspace/common/routine_gate.py --days Sun,Mon,Wed --evening`. Exit 10 means skip (Friday night, Shabbat, Yom Tov, or not a practice day): stop quietly and send nothing.
2. Read his current plan, `/workspace/golf/practice-plan-v2.html` (Crisp Irons: Weekly Practice Plan v2), and find today's night: Sunday is the Sequence night, Monday the Strike night, Wednesday the Transfer night.
3. Send Manny one short message: tonight's theme, then the three blocks (times 8:15 to 9:00 PM, card letter, and what to do) in full plain sentences, and the gear to set out (Garmin R50, bump turn board, divot board, mat). Keep it to a few lines. He's right-handed: always say "lead" or "trail" arm or hand, never "one arm" or "one hand". Don't invent drills that aren't in the plan. If the plan file is missing or unreadable, send one short message saying the reminder couldn't load the plan.

The reminder goes only to Manny in this Grok Bot chat (Spackler - Golf Practice); no one else. On skipped days, send nothing.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/golf-practice-evening-reminder.md for context.

Remind Manny of tonight's golf practice before his 8:15 PM session (Sunday, Monday, Wednesday).

1. Gate: run `python3 /workspace/common/routine_gate.py --days Sun,Mon,Wed --evening`. Exit 10 means skip (Friday night, Shabbat, Yom Tov, or not a practice day): stop quietly and send nothing.
2. Read his current plan, `/workspace/golf/practice-plan-v2.html` (Crisp Irons: Weekly Practice Plan v2), and find today's night: Sunday is the Sequence night, Monday the Strike night, Wednesday the Transfer night.
3. Send Manny one short message: tonight's theme, then the three blocks (times 8:15 to 9:00 PM, card letter, and what to do) in full plain sentences, and the gear to set out (Garmin R50, bump turn board, divot board, mat). Keep it to a few lines. He's right-handed: always say "lead" or "trail" arm or hand, never "one arm" or "one hand". Don't invent drills that aren't in the plan. If the plan file is missing or unreadable, send one short message saying the reminder couldn't load the plan.

The reminder goes only to Manny in the Routines chat in Grok Bot; no one else. On skipped days, send nothing.
```
