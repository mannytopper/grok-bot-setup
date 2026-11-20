# Parsha backup check (owner: Parsha · Weekly Teen Parsha PDF, folder: parsha-backup-check)

- **Owner bot:** Parsha · Weekly Teen Parsha PDF
- **Original folder id:** `parsha-backup-check`
- **Enabled state:** Paused (Nov 4, 2026, at Manny's request: pause, do not delete)
- **Schedule/trigger:** `CRON_TZ=America/New_York 52 9 * * 5` (every Friday at 9:52 AM ET)
- **Timing:** Flexible (default; not exact)
- **Connectors/accounts:** None. Local execution on WHI-LT-26-03 (machineId `cc87a891-f809-4773-a01b-4755b0cc5cc6`) only if it has to step in (otherwise it only reads the Parsha folder).
- **Scripts:** Same as weekly-parsha-pdf when it has to step in. Checks `C:\Users\Manny\Documents\Parsha` and `/home/box/parsha`.
- **Skills:** weekly-parsha-sheet-build
- **Files/state:** Same as weekly-parsha-pdf
- **Memory facts:** Backup for the 9:30 AM Friday run. Stay silent if the main run already delivered the sheet, is still underway (a RUNNING notice was sent today), it's Yom Tov, or there's nothing to do. Never print a second copy. Keep this copy paused, matching the original.
- **Permissions:** Local execution on WHI-LT-26-03 (machineId `cc87a891-f809-4773-a01b-4755b0cc5cc6`) only if it steps in (same print path as the main run). No email.
- **Hooks:** None
- **Open issues:** Keep paused. A paused original stays paused on the copy. Same laptop and Friday-print issues as the main run if it ever has to step in.

## Original prompt (verbatim)

```
Passive rule: stay silent whenever the main run already delivered the sheet, is still underway, it's Yom Tov, or there's nothing to do. Never send "nothing new", success-only, or status notes. Only message Manny if the main run clearly missed and you have to step in (RUNNING + the finished sheet, the standing deliverable), or if something failed and he needs to act.

Backup for the "Weekly Parsha PDF" routine (9:30 AM ET Fridays). Work out this week's parsha (Hebcal, diaspora) and check whether this week's sheet already exists in C:\Users\Manny\Documents\Parsha on WHI-LT-26-03 (named like "<Parsha> 5787.pdf") or on the box under /home/box/parsha, or was already sent to Manny in this chat today. If the main run delivered it or is clearly still underway (a RUNNING notice was sent today), stay quiet with no message. If it didn't run, send Manny a short RUNNING message in this chat, then run the full Weekly Parsha PDF job via the @Weekly parsha sheet build skill (skill id weekly-parsha-sheet-build), following that routine's saved instructions exactly (save to Documents\Parsha, print one copy, close Adobe, send the PDF here). Check the Parsha folder again right before printing so a second copy is never printed. Results go to Manny in this chat only. If it's a Jewish holiday (Yom Tov), do nothing and send nothing.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/parsha-backup-check.md for context.

Passive rule: stay silent whenever the main run already delivered the sheet, is still underway, it's Yom Tov, or there's nothing to do. Never send "nothing new", success-only, or status notes. Only message Manny if the main run clearly missed and you have to step in (RUNNING + the finished sheet, the standing deliverable), or if something failed and he needs to act.

Backup for the "Weekly Parsha PDF" routine (9:30 AM ET Fridays). Work out this week's parsha (Hebcal, diaspora) and check whether this week's sheet already exists in C:\Users\Manny\Documents\Parsha on WHI-LT-26-03 (named like "<Parsha> 5787.pdf") or on the box under /home/box/parsha, or was already sent to Manny in the Routines chat in Grok Bot today. If the main run delivered it or is clearly still underway (a RUNNING notice was sent today), stay quiet with no message. If it didn't run, send Manny a short RUNNING message in the Routines chat in Grok Bot, then run the full Weekly Parsha PDF job via the @Weekly parsha sheet build skill (skill id weekly-parsha-sheet-build), following that routine's saved instructions exactly (save to Documents\Parsha, print one copy, close Adobe, send the PDF here). Check the Parsha folder again right before printing so a second copy is never printed. Results go to Manny in the Routines chat in Grok Bot only. If it's a Jewish holiday (Yom Tov), do nothing and send nothing.
```
