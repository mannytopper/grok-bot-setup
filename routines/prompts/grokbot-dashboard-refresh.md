Moved to Routines from Alfred · Bot Chief Advisor on Nov 12, 2026. Context: /workspace/routines/context/grokbot-dashboard-refresh.md.

Ask-first (Manny, Nov 12, 2026): before opening more than 5 web pages for one task, starting a subagent, re-running a step that already failed twice, or any job expected to take more than 15 minutes, message Manny in one line with what and why, and wait for his yes. Exception: standing deliverables he already approved run as usual.

Gate first (Manny, Nov 6, 2026: "Yes, switch every bot's routines to use the new scripts"): run `python3 /workspace/common/routine_gate.py --days Mon`. Exit 10 = skip silently and end with no message. Exit 0 = run. If the script errors, fall back to the Yom Tov check below.

At the start of this run, read /workspace/shared-brain/INDEX.md and apply anything relevant. Protocol: HOW-TO-USE.md.

Weekly Monday refresh of Manny's Grok Bot Organization Dashboard Page (canvas_id 0ba3ca83-b62a-426d-926c-fb5c27231fef, url https://cursor.com/canvas/store-1847315e-d46f-4b3f-a695-8c7bc5477658/0ba3ca83-b62a-426d-926c-fb5c27231fef). Keep usage minimal; Manny asked for that explicitly. (Changed from daily to weekly on Nov 3, 2026; Manny: "Alfred 3: yes, weekly on Sunday", then the same day "dashboard refresh can shift to 850am monday".) This refresh is standing work that runs without asking Manny first (Manny, Nov 9, 2026: "those do NOT need my approval").

Fallback only: if today is Yom Tov (a Jewish holiday), do nothing and end silently.

Do the refresh in this scheduled run itself. Do not hand it off to Alfred's main session.

- Read the page's "Data as of" time from /workspace/dash/dashboard.canvas.tsx.
- Read each active bot's history since then with ReadTranscript, read-only, saving it to temporary working files only for this refresh. Use the current teammate list (deleted bots are skipped). Include this bot's own recent activity the same way.
- Missed-routine check (modeled on Fleet Doctor; Manny approved Nov 2, 2026): using routine status and the bot histories just read, note any routine since the last refresh that failed, or that was due and didn't run (skip Shabbat and Yom Tov, when nothing should run). Name the owning bot and routine. Show it on the dashboard.
- No usage forecast. Manny said on Nov 3, 2026: "Alfred 2: yes, remove the usage forecast". Usage and waste audits belong to Usage Guard (Manny, Nov 6, 2026). Remove or leave out the Usage section on the dashboard.
- Update only the data, the Data-as-of time (ET), the missed-routine list, and the open follow-ups, with small targeted EditCanvas edits on the same canvas_id (0ba3ca83-b62a-426d-926c-fb5c27231fef). Keep the subway-tile design and a 30-day window, back up the dashboard source first (see /workspace/dash/dashboard.pre-*.canvas.tsx), and never invent activity. Skip bots with nothing new. Source file: /workspace/dash/dashboard.canvas.tsx.
- Send nothing: no messages, email or printing, and don't change any other routine or bot, except the dashboard page itself.
- If ReadTranscript of another bot's history, or EditCanvas on that canvas, cannot be done from this scheduled run, tell Manny in the Routines chat in Grok Bot, in one or two short sentences, what could not be done and why, and stop. Do not hand the work back to Alfred.

Passive (Manny, Nov 5, 2026 via Connor): stay silent and only message Manny when something needs his attention. Post nothing on success, nothing-new, or routine-status runs. Tell Manny in the Routines chat in Grok Bot, in one or two short sentences, only if the refresh fails or a routine failed or was missed (name it). Otherwise end with no message to him.

No bot history backups. Manny said on Oct 31, 2026: "Remove backing up of any bots from your routines for now. Until the clear chat function is available there is no need for a backup." Do not run the weekly history backup or write to /workspace/bot-history-backups/ until Manny asks to turn it back on.

Results: nobody when the refresh succeeds with nothing missed; Manny in the Routines chat in Grok Bot only when the refresh fails, a routine failed or was missed, or part of the refresh could not be done from this run.
