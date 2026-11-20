# Weekly Grok Bot setup review (owner: Connor · Executive Assistant, folder: weekly-grok-bot-setup-review)

- **Owner bot:** Connor · Executive Assistant
- **Original folder id:** `weekly-grok-bot-setup-review`
- **Enabled state:** Enabled
- **Schedule/trigger:** `CRON_TZ=America/New_York 0 7 * * 1` (Mondays around 7:00 AM ET). (The Nov 9 export still said 6:45 AM; current cron is 7:00 AM per Connor's Nov 12 handoff.)
- **Timing:** Flexible, 15 minutes early or late
- **Connectors/accounts:** None required beyond built-in tools. Uses the recent-changes skill, the Weekly Grok Bot Setup Review Page, and setup-improvement-log.md.
- **Scripts:** `/workspace/common/routine_gate.py`, with `/workspace/common/shabbat_gate.py` as the fallback (exit 10 = skip silently). Invoked for Mondays.
- **Skills:** recent-changes, routine-gate
- **Files/state:** Weekly Grok Bot Setup Review Page, and `setup-improvement-log.md` (path as used by the current Connor prompt).
- **Memory facts:** Passive: short note with a link if something new would help; otherwise stay silent as the prompt says. Read `/workspace/shared-brain/INDEX.md` at the start.
- **Permissions:** None. Chat only. No local execution.
- **Hooks:** None
- **Open issues:** Prompt text is from the Nov 9 export and was not confirmed against the Nov 12 UpdateRoutine get.

## Original prompt (verbatim)

_FLAG: the verbatim saved prompt could not be retrieved from Connor's Nov 12, 2026 ~11:20Z UpdateRoutine get results, because ReadTranscript returns spoken messages only and leaves tool calls out. The text below is from Manny's Nov 9, 2026 Connor export (`/workspace/grok-bot-export-connor-·-executive-assistant.json`). Connor's Nov 12 handoff gave current folder ids, schedules, and permissions (used in the metadata above); several schedules have changed since this prompt text was exported, and the prompt itself may still mention the old time._

```
Weekly look at new Grok Bot features and what they could do for Manny. Run on Connor's computer (the box). Gate first: run `python3 /workspace/common/routine_gate.py --days Mon` (routine-gate skill, Manny approved Nov 6, 2026); exit 10 means skip silently (Yom Tov) and cover the missed week next time. If the script errors, check yourself: Manny is an Orthodox Jew, so if today is Yom Tov, skip silently.

Keep usage to a minimum. Do the work directly with as few tool calls as possible. Don't start helpers, don't run broad web searches, and don't read teammate transcripts.

Scope: new Grok Bot features only. Do not audit bots, usage, overlap between bots, or setup health; Alfred's Friday review covers those.

1. What's new: load the Cursor-managed recent-changes skill and check one or two official Grok Bot changelog or announcement pages for the past 7 days. List each new or changed feature with its official source link. Include only what official sources confirm, mark anything still rolling out, and never invent features or links. If nothing is new, stop and send nothing.

2. What it could do for Manny: for each new feature, say in one or two plain sentences what it could do for Manny specifically (his calendar, email, morning rundown, AMS360 desk-login runs, Tesla watch, digests, or his other bots). Drop features that don't help him.

3. Change nothing: report only. Never edit, pause, delete, or create any routine, bot, skill, or connector without Manny's explicit yes in chat.

4. Log: append each week's features and notes to /cursor/stores/store-c188da78-b919-4edc-8372-5d298cf9eea0/setup-improvement-log.md.

Delivery (Manny's rule from Nov 5, 2026: routines stay quiet and only message him when something needs his attention): only if there are useful new features worth his decision, update the existing "Weekly Grok Bot Setup Review" Page (don't make a new one), keep it short, and send Manny a one-line note in this Grok Bot chat with the link. If nothing new would help him, send nothing at all and don't update the Page. Send nothing to anyone else.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/weekly-grok-bot-setup-review.md for context.

Weekly look at new Grok Bot features and what they could do for Manny. Run on Connor's computer (the box). Gate first: run `python3 /workspace/common/routine_gate.py --days Mon` (routine-gate skill, Manny approved Nov 6, 2026); exit 10 means skip silently (Yom Tov) and cover the missed week next time. If the script errors, check yourself: Manny is an Orthodox Jew, so if today is Yom Tov, skip silently.

Keep usage to a minimum. Do the work directly with as few tool calls as possible. Don't start helpers, don't run broad web searches, and don't read teammate transcripts.

Scope: new Grok Bot features only. Do not audit bots, usage, overlap between bots, or setup health; Alfred's Friday review covers those.

1. What's new: load the Cursor-managed recent-changes skill and check one or two official Grok Bot changelog or announcement pages for the past 7 days. List each new or changed feature with its official source link. Include only what official sources confirm, mark anything still rolling out, and never invent features or links. If nothing is new, stop and send nothing.

2. What it could do for Manny: for each new feature, say in one or two plain sentences what it could do for Manny specifically (his calendar, email, morning rundown, AMS360 desk-login runs, Tesla watch, digests, or his other bots). Drop features that don't help him.

3. Change nothing: report only. Never edit, pause, delete, or create any routine, bot, skill, or connector without Manny's explicit yes in chat.

4. Log: append each week's features and notes to /cursor/stores/store-c188da78-b919-4edc-8372-5d298cf9eea0/setup-improvement-log.md.

Delivery (Manny's rule from Nov 5, 2026: routines stay quiet and only message him when something needs his attention): only if there are useful new features worth his decision, update the existing "Weekly Grok Bot Setup Review" Page (don't make a new one), keep it short, and send Manny a one-line note in the Routines chat in Grok Bot with the link. If nothing new would help him, send nothing at all and don't update the Page. Send nothing to anyone else.
```
