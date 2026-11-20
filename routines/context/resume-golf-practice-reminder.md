# Resume golf practice reminder (owner: Spackler - Golf Practice, folder: resume-golf-practice-reminder)

- **Owner bot:** Spackler - Golf Practice
- **Original folder id:** `resume-golf-practice-reminder`
- **Enabled state:** Enabled (one-off created Nov 10, 2026 for the week off)
- **Schedule/trigger:** `CRON_TZ=America/New_York 0 12 15 11 *` (once, Sunday Nov 15 at 12:00 PM ET)
- **Timing:** Exact
- **Connectors/accounts:** None. It only acts on the evening-reminder routine.
- **Scripts:** None
- **Skills:** None listed
- **Files/state:** None. Target folder: `golf-practice-evening-reminder`.
- **Memory facts:** Manny took the week of Nov 8 to 14, 2026 off from golf practice because he was away. This one-off should resume the paused evening reminder so it runs again Sunday night, Nov 15, then delete itself. Don't message Manny unless the resume fails.
- **Permissions:** Ability to unpause (enable) the evening-reminder routine and then delete this one-off. No send permission, no local execution.
- **Hooks:** None
- **Open issues:** If the Routines copy of golf-practice-evening-reminder replaces Spackler's before Nov 15, this one-off has to point at the Routines copy, or it will turn Spackler's original back on and the reminder will run twice. Decide before noon ET on Sunday Nov 15 which copy should be resumed. The proposed prompt points at the Routines copy. Don't test the evening reminder before the evening of Nov 15.

## Original prompt (verbatim)

```
Manny took the week of Nov 8 to 14, 2026 off from golf practice because he was away. Resume the paused routine "Golf practice evening reminder" (folder golf-practice-evening-reminder) so it runs again tonight, Sunday Nov 15. Don't message Manny unless the resume fails. Then delete this one-off routine.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/resume-golf-practice-reminder.md for context.

Manny took the week of Nov 8 to 14, 2026 off from golf practice because he was away. Resume the paused Routines copy of "Golf practice evening reminder" (folder golf-practice-evening-reminder) so it runs again tonight, Sunday Nov 15. Don't message Manny unless the resume fails. If it fails, message him in the Routines chat in Grok Bot. Then delete this one-off routine.
```
