# Weekly usage dashboard refresh (owner: Connor · Executive Assistant, folder: weekly-usage-dashboard-refresh)

- **Owner bot:** Connor · Executive Assistant
- **Original folder id:** `weekly-usage-dashboard-refresh`
- **Enabled state:** Enabled
- **Schedule/trigger:** `CRON_TZ=America/New_York 0 7 * * 1` (Mondays around 7:00 AM ET). (The Nov 9 export still said 8:00 AM; current cron is 7:00 AM, 0 minutes early and 15 late, per Connor's Nov 12 handoff.)
- **Timing:** Flexible, 0 minutes early, 15 minutes late
- **Connectors/accounts:** CheckSubscriptionUsage. Canvas `f6b1ba88` ("Grok Bot Usage by Bot"). No email connector, no local execution.
- **Scripts:** `/workspace/common/routine_gate.py`, with `/workspace/common/shabbat_gate.py` as the fallback (exit 10 = skip silently). Follow `/workspace/usage-dashboard/README.md`. Fallback gate: `/workspace/common/hebcal_check.py` if routine_gate errors.
- **Skills:** routine-gate
- **Files/state:** `/workspace/usage-dashboard/README.md` and the existing usage Page (canvas f6b1ba88-8f85-4127-a3b2-c1f087ceeca4). Edit the same Page so the link and desktop shortcut keep working.
- **Memory facts:** Use only real numbers; set the "last updated" time in ET. Keep usage low. Stay silent on success.
- **Permissions:** Need edit access to canvas f6b1ba88. No standing send, no local execution.
- **Hooks:** None
- **Open issues:** Prompt text is from the Nov 9 export and still says 8 AM ET. Confirm Routines can edit that canvas.

## Original prompt (verbatim)

_FLAG: the verbatim saved prompt could not be retrieved from Connor's Nov 12, 2026 ~11:20Z UpdateRoutine get results, because ReadTranscript returns spoken messages only and leaves tool calls out. The text below is from Manny's Nov 9, 2026 Connor export (`/workspace/grok-bot-export-connor-·-executive-assistant.json`). Connor's Nov 12 handoff gave current folder ids, schedules, and permissions (used in the metadata above); several schedules have changed since this prompt text was exported, and the prompt itself may still mention the old time._

```
Manny asked on Nov 5, 2026 for his Grok Bot usage-by-bot dashboard to be updated every Monday morning at 8 AM ET. First run `python3 /workspace/common/routine_gate.py --days Mon` (routine-gate skill, Manny approved Nov 6, 2026); exit 10 means skip (Yom Tov or not Monday): do nothing and send nothing. If that script errors, fall back to `python3 /workspace/common/hebcal_check.py` and skip if it says skip. Otherwise follow /workspace/usage-dashboard/README.md: pull the current usage by bot, by routine and by day with CheckSubscriptionUsage, and update the SAME Page "Grok Bot Usage by Bot" (canvas f6b1ba88-8f85-4127-a3b2-c1f087ceeca4) in one edit so the link and Manny's desktop shortcut keep working. Use only real numbers, and set the "last updated" time in ET. Keep usage low. Stay silent on success; message Manny in this chat only if the refresh fails, in one line saying what failed.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/weekly-usage-dashboard-refresh.md for context.

Manny asked on Nov 5, 2026 for his Grok Bot usage-by-bot dashboard to be updated every Monday morning at 8 AM ET. First run `python3 /workspace/common/routine_gate.py --days Mon` (routine-gate skill, Manny approved Nov 6, 2026); exit 10 means skip (Yom Tov or not Monday): do nothing and send nothing. If that script errors, fall back to `python3 /workspace/common/hebcal_check.py` and skip if it says skip. Otherwise follow /workspace/usage-dashboard/README.md: pull the current usage by bot, by routine and by day with CheckSubscriptionUsage, and update the SAME Page "Grok Bot Usage by Bot" (canvas f6b1ba88-8f85-4127-a3b2-c1f087ceeca4) in one edit so the link and Manny's desktop shortcut keep working. Use only real numbers, and set the "last updated" time in ET. Keep usage low. Stay silent on success; message Manny in the Routines chat in Grok Bot only if the refresh fails, in one line saying what failed.
```
