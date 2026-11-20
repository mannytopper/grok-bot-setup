# Grokbot dashboard refresh (owner: Alfred · Bot Chief Advisor, folder: grokbot-dashboard-refresh)

- **Owner bot:** Alfred · Bot Chief Advisor
- **Original folder id:** `grokbot-dashboard-refresh`
- **Enabled state:** Enabled. Also exempted from Alfred's approve-first rule (Nov 9, 2026).
- **Schedule/trigger:** `CRON_TZ=America/New_York 50 8 * * 1` (Mondays around 8:50 AM ET)
- **Timing:** Flexible, 15 minutes early or late
- **Connectors/accounts:** None. The scheduled run only hands off. The real refresh happens in Alfred's main session (ReadTranscript of every bot, then a helper uses EditCanvas). Routines would need ReadTranscript plus edit access to canvas `0ba3ca83-b62a-426d-926c-fb5c27231fef`.
- **Scripts:** `python3 /workspace/common/routine_gate.py --days Mon`.
- **Skills:** None listed beyond the gate. Canvas edit is done from the main session.
- **Files/state:** `/workspace/dash/dashboard.canvas.tsx` (source), backups `/workspace/dash/dashboard.pre-*.canvas.tsx`. Canvas id `0ba3ca83-b62a-426d-926c-fb5c27231fef`. The laptop has a "Grokbot dashboard" shortcut.
- **Memory facts:** No usage forecast (Nov 3). Chat-history backups OFF (Oct 31). Message Manny only when the refresh fails or a routine was missed. Silent on success.
- **Permissions:** None for sends or local execution. Need ReadTranscript across bots and EditCanvas access to canvas 0ba3ca83 if Routines is to do the real work itself.
- **Hooks:** None
- **Open issues:** The scheduled run only hands off, and the real work runs from Alfred's main session. Check whether Routines can do that work itself (ReadTranscript plus canvas edits). If it cannot, this routine may need to stay on Alfred or be redesigned. Alfred needs Manny's yes in Alfred's own chat before it pauses or deletes its originals.

## Original prompt (verbatim)

```
Gate first (Manny, Nov 6, 2026: "Yes, switch every bot's routines to use the new scripts"): run `python3 /workspace/common/routine_gate.py --days Mon`. Exit 10 = skip silently and end with no message. Exit 0 = run. If the script errors, fall back to the Yom Tov check below.

At the start of this run (and when Alfred does the handoff), read /workspace/shared-brain/INDEX.md and apply anything relevant. Protocol: HOW-TO-USE.md.

Weekly Monday refresh of Manny's Grok Bot Organization Dashboard Page (canvas_id 0ba3ca83-b62a-426d-926c-fb5c27231fef, url https://cursor.com/canvas/store-1847315e-d46f-4b3f-a695-8c7bc5477658/0ba3ca83-b62a-426d-926c-fb5c27231fef). Keep usage minimal; Manny asked for that explicitly. (Changed from daily to weekly on Nov 3, 2026; Manny: "Alfred 3: yes, weekly on Sunday", then the same day "dashboard refresh can shift to 850am monday".) This refresh is standing work that runs without asking Manny first (Manny, Nov 9, 2026: "those do NOT need my approval").

Fallback only: if today is Yom Tov (a Jewish holiday), do nothing and end silently.

This scheduled run can't read other bots' history, so don't try to refresh here. End right away and hand the refresh back to Alfred (the parent) with a one-line report: "Dashboard refresh handoff: please refresh the page from the main session." Don't message Manny from this run.

When Alfred gets the handoff, it does the refresh from its main session:
- Read the page's "Data as of" time from /workspace/dash/dashboard.canvas.tsx.
- Read each active bot's history since then, read-only, saving it to temporary working files only for this refresh. Use the current teammate list (deleted bots are skipped), plus Alfred's own activity.
- Missed-routine check (modeled on Fleet Doctor; Manny approved Nov 2, 2026): using Alfred's routine status and the bot histories just read, note any routine since the last refresh that failed, or that was due and didn't run (skip Shabbat and Yom Tov, when nothing should run). Name the owning bot and routine. Show it on the dashboard.
- No usage forecast. Manny said on Nov 3, 2026: "Alfred 2: yes, remove the usage forecast". Usage and waste audits belong to Usage Guard (Manny, Nov 6, 2026). Remove or leave out the Usage section on the dashboard.
- Hand those files and findings to one low-cost helper to update only the data, the Data-as-of time (ET), the missed-routine list, and the open follow-ups. Use small targeted edits on the same canvas_id, keep the subway-tile design and a 30-day window, back up the dashboard source first, and never invent activity. Skip bots with nothing new.
- Send nothing: no messages, email or printing, and don't change any other routine or bot.

Passive (Manny, Nov 5, 2026 via Connor): stay silent and only message Manny when something needs his attention. Post nothing on success, nothing-new, or routine-status runs. Tell Manny in this chat, in one or two short sentences, only if the refresh fails or a routine failed or was missed (name it). Otherwise end with no message to him.

No bot history backups. Manny said on Oct 31, 2026: "Remove backing up of any bots from your routines for now. Until the clear chat function is available there is no need for a backup." Do not run the weekly history backup or write to /workspace/bot-history-backups/ until Manny asks to turn it back on.

Results: nobody when the refresh succeeds with nothing missed; Manny in this Grok Bot chat only when the refresh fails or a routine failed or was missed.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/grokbot-dashboard-refresh.md for context.

Gate first (Manny, Nov 6, 2026: "Yes, switch every bot's routines to use the new scripts"): run `python3 /workspace/common/routine_gate.py --days Mon`. Exit 10 = skip silently and end with no message. Exit 0 = run. If the script errors, fall back to the Yom Tov check below.

At the start of this run (and when Alfred does the handoff), read /workspace/shared-brain/INDEX.md and apply anything relevant. Protocol: HOW-TO-USE.md.

Weekly Monday refresh of Manny's Grok Bot Organization Dashboard Page (canvas_id 0ba3ca83-b62a-426d-926c-fb5c27231fef, url https://cursor.com/canvas/store-1847315e-d46f-4b3f-a695-8c7bc5477658/0ba3ca83-b62a-426d-926c-fb5c27231fef). Keep usage minimal; Manny asked for that explicitly. (Changed from daily to weekly on Nov 3, 2026; Manny: "Alfred 3: yes, weekly on Sunday", then the same day "dashboard refresh can shift to 850am monday".) This refresh is standing work that runs without asking Manny first (Manny, Nov 9, 2026: "those do NOT need my approval").

Fallback only: if today is Yom Tov (a Jewish holiday), do nothing and end silently.

This scheduled run can't read other bots' history, so don't try to refresh here. End right away and hand the refresh back to Alfred (the parent) with a one-line report: "Dashboard refresh handoff: please refresh the page from the main session." Don't message Manny from this run.

When Alfred gets the handoff, it does the refresh from its main session:
- Read the page's "Data as of" time from /workspace/dash/dashboard.canvas.tsx.
- Read each active bot's history since then, read-only, saving it to temporary working files only for this refresh. Use the current teammate list (deleted bots are skipped), plus Alfred's own activity.
- Missed-routine check (modeled on Fleet Doctor; Manny approved Nov 2, 2026): using Alfred's routine status and the bot histories just read, note any routine since the last refresh that failed, or that was due and didn't run (skip Shabbat and Yom Tov, when nothing should run). Name the owning bot and routine. Show it on the dashboard.
- No usage forecast. Manny said on Nov 3, 2026: "Alfred 2: yes, remove the usage forecast". Usage and waste audits belong to Usage Guard (Manny, Nov 6, 2026). Remove or leave out the Usage section on the dashboard.
- Hand those files and findings to one low-cost helper to update only the data, the Data-as-of time (ET), the missed-routine list, and the open follow-ups. Use small targeted edits on the same canvas_id, keep the subway-tile design and a 30-day window, back up the dashboard source first, and never invent activity. Skip bots with nothing new.
- Send nothing: no messages, email or printing, and don't change any other routine or bot.

Passive (Manny, Nov 5, 2026 via Connor): stay silent and only message Manny when something needs his attention. Post nothing on success, nothing-new, or routine-status runs. Tell Manny in the Routines chat in Grok Bot, in one or two short sentences, only if the refresh fails or a routine failed or was missed (name it). Otherwise end with no message to him.

No bot history backups. Manny said on Oct 31, 2026: "Remove backing up of any bots from your routines for now. Until the clear chat function is available there is no need for a backup." Do not run the weekly history backup or write to /workspace/bot-history-backups/ until Manny asks to turn it back on.

Results: nobody when the refresh succeeds with nothing missed; Manny in the Routines chat in Grok Bot only when the refresh fails or a routine failed or was missed.
```
