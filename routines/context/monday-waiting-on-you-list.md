# Monday waiting-on-you list (owner: Connor · Executive Assistant, folder: monday-waiting-on-you-list)

- **Owner bot:** Connor · Executive Assistant
- **Original folder id:** `monday-waiting-on-you-list`
- **Enabled state:** Enabled
- **Schedule/trigger:** `CRON_TZ=America/New_York 0 7 * * 1` (Mondays around 7:00 AM ET). (The Nov 9 export still said 9:00 AM; current cron is 7:00 AM per Connor's Nov 12 handoff.)
- **Timing:** Flexible, 15 minutes early or late
- **Connectors/accounts:** Google Calendar and Outlook calendar. Uses dq.py. Routines already has both calendar connectors.
- **Scripts:** `/workspace/common/routine_gate.py`, with `/workspace/common/shabbat_gate.py` as the fallback (exit 10 = skip silently). plus `dq.py` (decision-queue).
- **Skills:** decision-queue, routine-gate
- **Files/state:** Decision-queue files as used by dq.py / the decision-queue skill.
- **Memory facts:** Passive: stay silent when there is nothing waiting. Otherwise one short message with one line per decision.
- **Permissions:** None. Chat only. No local execution.
- **Hooks:** None
- **Open issues:** Prompt text is from the Nov 9 export and still says around 9:00 AM ET.

## Original prompt (verbatim)

_FLAG: the verbatim saved prompt could not be retrieved from Connor's Nov 12, 2026 ~11:20Z UpdateRoutine get results, because ReadTranscript returns spoken messages only and leaves tool calls out. The text below is from Manny's Nov 9, 2026 Connor export (`/workspace/grok-bot-export-connor-·-executive-assistant.json`). Connor's Nov 12 handoff gave current folder ids, schedules, and permissions (used in the metadata above); several schedules have changed since this prompt text was exported, and the prompt itself may still mention the old time._

```
Manny's weekly "waiting on you" list, Mondays around 9:00 AM ET (Manny approved this as idea 5 on Nov 6, 2026). Keep it short and cheap.

1. Gate first: run `python3 /workspace/common/routine_gate.py --days Mon`. Exit 10 means skip (Yom Tov): do nothing and send nothing. Exit 0 means run. If the script errors, fall back to `python3 /workspace/common/hebcal_check.py` (skip if it prints "skip": true).
2. Open decisions: follow the decision-queue skill and run `python3 /workspace/decision-queue/dq.py list --open`. Never close, answer or act on any item yourself.
3. Unanswered invites: check Manny's calendars (his main Google Calendar mannytopper@gmail.com and his Outlook calendar) from today through the next 14 days for invites he hasn't answered yet (needsAction or no response). Manny deliberately left the Hatzalah committee meeting tentative, so don't list it. Read only; never RSVP, edit or delete anything. Don't invent anything.
4. If both lists are empty, stay completely silent and send nothing. Otherwise send Manny one short message: a one-line intro, then one line per decision (the question and Connor's suggested answer) and one line per unanswered invite (title, day and time in ET, organizer), so he can clear them all in one reply. When he answers an item later in chat, close it with dq.py using his words.

The result goes only to Manny in this Grok Bot chat (Connor's chat). No one else is messaged, and nothing is sent when there's nothing waiting.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/monday-waiting-on-you-list.md for context.

Manny's weekly "waiting on you" list, Mondays around 9:00 AM ET (Manny approved this as idea 5 on Nov 6, 2026). Keep it short and cheap.

1. Gate first: run `python3 /workspace/common/routine_gate.py --days Mon`. Exit 10 means skip (Yom Tov): do nothing and send nothing. Exit 0 means run. If the script errors, fall back to `python3 /workspace/common/hebcal_check.py` (skip if it prints "skip": true).
2. Open decisions: follow the decision-queue skill and run `python3 /workspace/decision-queue/dq.py list --open`. Never close, answer or act on any item yourself.
3. Unanswered invites: check Manny's calendars (his main Google Calendar mannytopper@gmail.com and his Outlook calendar) from today through the next 14 days for invites he hasn't answered yet (needsAction or no response). Manny deliberately left the Hatzalah committee meeting tentative, so don't list it. Read only; never RSVP, edit or delete anything. Don't invent anything.
4. If both lists are empty, stay completely silent and send nothing. Otherwise send Manny one short message: a one-line intro, then one line per decision (the question and Connor's suggested answer) and one line per unanswered invite (title, day and time in ET, organizer), so he can clear them all in one reply. When he answers an item later in chat, close it with dq.py using his words.

The result goes only to Manny in the Routines chat in Grok Bot. No one else is messaged, and nothing is sent when there's nothing waiting.
```
