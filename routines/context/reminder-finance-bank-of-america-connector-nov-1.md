# Reminder: Finance (Bank of America) connector (Nov 13) (owner: Connor · Executive Assistant, folder: reminder-finance-bank-of-america-connector-nov-1)

- **Owner bot:** Connor · Executive Assistant
- **Original folder id:** `reminder-finance-bank-of-america-connector-nov-1` (folder name still says nov-1; the fire date is Nov 13)
- **Enabled state:** Enabled
- **Schedule/trigger:** One-off `CRON_TZ=America/New_York 0 9 13 11 *` (once, November 13 at 9:00 AM ET)
- **Timing:** Exact
- **Connectors/accounts:** None for the reminder itself. It asks, with a widget, whether Manny wants the Finance connector installed (read-only, through Plaid, Bank of America). Don't install unless he says yes.
- **Scripts:** None. Skip and wait for the next weekday if the fire day is Shabbat or Yom Tov (Nov 13, 2026 is a Friday, not Shabbat).
- **Skills:** None listed
- **Files/state:** None
- **Memory facts:** Manny asked on Nov 5, 2026 to be asked again in one week; the fire date is Nov 13. Delete the routine after it fires. Don't install anything unless he says yes.
- **Permissions:** None. Widget in chat only.
- **Hooks:** None
- **Open issues:** This fires tomorrow (Nov 13, 9:00 AM ET). Moving it first risks a missed or double reminder; consider leaving this one-off on Connor. Prompt text is from the Nov 9 export.

## Original prompt (verbatim)

_FLAG: the verbatim saved prompt could not be retrieved from Connor's Nov 12, 2026 ~11:20Z UpdateRoutine get results, because ReadTranscript returns spoken messages only and leaves tool calls out. The text below is from Manny's Nov 9, 2026 Connor export (`/workspace/grok-bot-export-connor-·-executive-assistant.json`). Connor's Nov 12 handoff gave current folder ids, schedules, and permissions (used in the metadata above); several schedules have changed since this prompt text was exported, and the prompt itself may still mention the old time._

```
One-off reminder Manny asked for on Nov 5, 2026 ("ask me again in one week"). If today is Shabbat or Yom Tov, don't message him; wait for the next weekday. Otherwise ask Manny in chat whether he wants the Finance connector installed now. It's read-only, connects through Plaid, and would link his Bank of America account so Connor can see balances, transactions and recurring charges and catch subscriptions his email missed. Ask with a widget offering "Yes, install it" or "Not now". Don't install anything unless Manny says yes in chat. Delete this routine after it fires.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/reminder-finance-bank-of-america-connector-nov-1.md for context.

One-off reminder Manny asked for on Nov 5, 2026 ("ask me again in one week"). If today is Shabbat or Yom Tov, don't message him; wait for the next weekday. Otherwise ask Manny in the Routines chat in Grok Bot whether he wants the Finance connector installed now. It's read-only, connects through Plaid, and would link his Bank of America account so Connor can see balances, transactions and recurring charges and catch subscriptions his email missed. Ask with a widget offering "Yes, install it" or "Not now". Don't install anything unless Manny says yes in the Routines chat in Grok Bot. Delete this routine after it fires.
```
