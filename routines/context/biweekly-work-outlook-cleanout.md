# Biweekly work Outlook cleanout (owner: Email Purger, folder: biweekly-work-outlook-cleanout)

- **Owner bot:** Email Purger (agent id `604b5043-13ef-4fed-8501-7fa24112766f`)
- **Original folder id:** `biweekly-work-outlook-cleanout`
- **Enabled state:** Enabled
- **Schedule/trigger:** `CRON_TZ=America/New_York 15 8 * * 1` (Mondays around 8:15 AM ET); biweekly via state file
- **Timing:** Flexible, 15 minutes early or late. Skip if `lastRun` in the state file is within the last 13 days. State `lastRun` was 2026-11-09 as of the Nov 12 handoff.
- **Connectors/accounts:** Outlook connector on the Wealcatch work inbox (manny@wealcatchmd.com), read-only scan. Routines already has the Outlook connector connected. Confirm the same account is signed in.
- **Scripts:** `/workspace/common/routine_gate.py`, with `/workspace/common/shabbat_gate.py` as the fallback (exit 10 = skip silently). Invoked as `python3 /workspace/common/routine_gate.py --cron "15 8 * * 1"`. Then `python3 /workspace/email-purger/scripts/group_messages.py messages.json --out proposal.json`.
- **Skills:** email-purger-group, routine-gate
- **Files/state:** `/workspace/email-purger/work-cleanout-state.json` (update `lastRun` after a completed scan, whether or not there is a proposal). Per-run messages JSON and `proposal.json` under `/workspace/email-purger/`.
- **Memory facts:** Never touch starred, important, flagged, or Keep. Always preserve bank, insurance, school, and family mail. Never delete, archive, unsubscribe, or send without Manny's explicit yes in Email Purger's chat. Passive if nothing material is new.
- **Permissions:** None for the scan. The grouping script never touches mail. No standing send, no local execution.
- **Hooks:** None
- **Open issues:** Same as the monthly cleanout: proposals are handed to Email Purger for Manny's yes in that chat, not in Routines. Confirm the Outlook work account on Routines. Preserve the lastRun state so the biweekly skip still works after the move.

## Original prompt (verbatim)

```
Run a read-only cleanout proposal for Manny’s Wealcatch work inbox (manny@wealcatchmd.com) in Outlook.

Gate first: run `python3 /workspace/common/routine_gate.py --cron "15 8 * * 1"`. Exit 10 = stay silent and end. Exit 0 = continue. If that script errors, fall back to `python3 /workspace/common/shabbat_gate.py` (exit 10 = skip silently).

Biweekly only: read `/workspace/email-purger/work-cleanout-state.json`. If `lastRun` is within the last 13 days, stay silent and end. Otherwise continue.

Scan the Outlook inbox for promotions, newsletters, and stale clutter. Honor standing rules: never touch starred, important, flagged, or Keep; always preserve bank, insurance, school, and family mail; never delete, archive, unsubscribe, or send without Manny’s explicit yes in this Email Purger chat.

Write a messages JSON under `/workspace/email-purger/` for this run, then build the proposal with `python3 /workspace/email-purger/scripts/group_messages.py messages.json --out proposal.json` (skill: email-purger-group). Proposal only — the script never touches mail.

Update `work-cleanout-state.json` with today’s date as `lastRun` after a completed scan (whether or not there is a proposal).

Passive: if nothing material is new or the proposal is empty, stay silent (no “nothing new” message). If there is a real proposal, message Manny in this Email Purger chat with a concise grouped summary and wait for his approval before changing anything.

Who receives the result and where: Manny in this Email Purger chat only when there is a proposal needing approval; otherwise no one. When there is nothing new: stay silent.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/biweekly-work-outlook-cleanout.md for context.

Run a read-only cleanout proposal for Manny’s Wealcatch work inbox (manny@wealcatchmd.com) in Outlook.

Gate first: run `python3 /workspace/common/routine_gate.py --cron "15 8 * * 1"`. Exit 10 = stay silent and end. Exit 0 = continue. If that script errors, fall back to `python3 /workspace/common/shabbat_gate.py` (exit 10 = skip silently).

Biweekly only: read `/workspace/email-purger/work-cleanout-state.json`. If `lastRun` is within the last 13 days, stay silent and end. Otherwise continue.

Scan the Outlook inbox for promotions, newsletters, and stale clutter. Honor standing rules: never touch starred, important, flagged, or Keep; always preserve bank, insurance, school, and family mail; never delete, archive, unsubscribe, or send without Manny’s explicit yes in Email Purger's chat.

Write a messages JSON under `/workspace/email-purger/` for this run, then build the proposal with `python3 /workspace/email-purger/scripts/group_messages.py messages.json --out proposal.json` (skill: email-purger-group). Proposal only — the script never touches mail.

Update `work-cleanout-state.json` with today’s date as `lastRun` after a completed scan (whether or not there is a proposal).

Passive: if nothing material is new or the proposal is empty, stay silent (no “nothing new” message). If there is a real proposal, hand it to Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f) for Manny to review in Email Purger's chat, and wait for his approval there before changing anything. Never message Manny in the Routines chat, and never ask him for approval there.

Who receives the result and where: Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f), so Manny can review the proposal in Email Purger's chat, only when there is a proposal needing approval; otherwise no one. When there is nothing new: stay silent. The copy never messages Manny in the Routines chat and never asks him for approval there.
```
