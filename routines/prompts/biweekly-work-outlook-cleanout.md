Moved to Routines from Email Purger on Nov 12, 2026. Context: /workspace/routines/context/biweekly-work-outlook-cleanout.md.

Ask-first (Manny, Nov 12, 2026): before opening more than 5 web pages for one task, starting a subagent, re-running a step that already failed twice, or any job expected to take more than 15 minutes, hand Manny a one-line ask of what and why to Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f) as a handoff that ends with "No reply needed.", and wait for his yes in Email Purger's chat. Never message Manny in the Routines chat. Exception: standing deliverables he already approved run as usual.

Run a read-only cleanout proposal for Manny’s Wealcatch work inbox (manny@wealcatchmd.com) in Outlook.

Gate first: run `python3 /workspace/common/routine_gate.py --cron "15 8 * * 1"`. Exit 10 = stay silent and end. Exit 0 = continue. If that script errors, fall back to `python3 /workspace/common/shabbat_gate.py` (exit 10 = skip silently).

Biweekly only: read `/workspace/email-purger/work-cleanout-state.json`. If `lastRun` is within the last 13 days, stay silent and end. Otherwise continue.

Scan the Outlook inbox for promotions, newsletters, and stale clutter. Honor standing rules: never touch starred, important, flagged, or Keep; always preserve bank, insurance, school, and family mail; never delete, archive, unsubscribe, or send without Manny’s explicit yes in Email Purger's chat.

Write a messages JSON under `/workspace/email-purger/` for this run, then build the proposal with `python3 /workspace/email-purger/scripts/group_messages.py messages.json --out proposal.json` (skill: email-purger-group). Proposal only — the script never touches mail.

Update `work-cleanout-state.json` with today’s date as `lastRun` after a completed scan (whether or not there is a proposal).

Passive: if nothing material is new or the proposal is empty, stay silent (no “nothing new” message). If there is a real proposal, hand it to Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f) as a handoff that ends with "No reply needed.", for Manny to review in Email Purger's chat, and wait for his approval there before changing anything. Never message Manny in the Routines chat.

Who receives the result and where: Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f), as a handoff that ends with "No reply needed.", so Manny can review a real proposal in Email Purger's chat; otherwise no one. When there is nothing new: stay silent. This copy never messages Manny in the Routines chat.
