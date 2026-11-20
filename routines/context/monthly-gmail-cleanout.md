# Monthly Gmail cleanout (owner: Email Purger, folder: monthly-gmail-cleanout)

- **Owner bot:** Email Purger (agent id `604b5043-13ef-4fed-8501-7fa24112766f`)
- **Original folder id:** `monthly-gmail-cleanout`
- **Enabled state:** Enabled
- **Schedule/trigger:** `CRON_TZ=America/New_York 0 8 1-7 * 1` (first Monday of each month around 8:00 AM ET; note standard cron ORs day-of-month and day-of-week, the intended meaning is the first Monday)
- **Timing:** Flexible, 15 minutes early or late
- **Connectors/accounts:** user-Gmail connector on mannytopper@gmail.com (read-only scan). Routines already has the Gmail connector connected. Confirm the same account is signed in.
- **Scripts:** `python3 /workspace/common/shabbat_gate.py` (exit 10 = stay silent and end). Proposal written under `/workspace/email-purger/` with today's date.
- **Skills:** None listed on the routine itself. Standing cleanout rules are in the prompt and memory.
- **Files/state:** Short proposal files under `/workspace/email-purger/` dated for the run.
- **Memory facts:** Never touch Starred, Important, or Keep. Always preserve bank, insurance, school, and family. Keep Dumbarton Minyan mail. SLRC alumni may be archived. Upgrade/Flex Pay loan promos are trash candidates. Never delete, archive, unsubscribe, or send without Manny's explicit yes. Passive: stay silent if nothing material is new.
- **Permissions:** None for the scan. It never changes mail until Manny approves in Email Purger's chat. No standing send, no local execution.
- **Hooks:** None
- **Open issues:** Manny decided Nov 12, 2026 that approvals stay in Email Purger's chat ("Stay here"). The proposed copy hands a real proposal to Email Purger and never messages Manny in the Routines chat or asks him for approval there. Confirm the Gmail account on Routines.

## Original prompt (verbatim)

```
Run a read-only cleanout scan of mannytopper@gmail.com for Email Purger.

First: run the Shabbat/Yom Tov gate (`python3 /workspace/common/shabbat_gate.py`). If exit 10, stay silent and end.

Then scan promotions, social, updates, and forums for new clutter since the last run. Honor standing rules: never touch Starred, Important, or Keep; always preserve bank, insurance, school, and family; never delete, archive, unsubscribe, or send without Manny’s explicit yes in this chat.

Group candidates by type (newsletters, promotions, stale, other). Prepare proposed delete, archive, and unsubscribe actions. Write a short proposal under /workspace/email-purger/ with today’s date.

Passive: if nothing material is new, stay silent (no “nothing new” message). If there is a real proposal, message Manny in this Email Purger chat with a concise grouped summary and wait for his approval before changing anything.

Who receives the result and where: Manny in this Email Purger chat only when there is a proposal needing approval; otherwise no one. When there is nothing new: stay silent.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/monthly-gmail-cleanout.md for context.

Run a read-only cleanout scan of mannytopper@gmail.com for Email Purger.

First: run the Shabbat/Yom Tov gate (`python3 /workspace/common/shabbat_gate.py`). If exit 10, stay silent and end.

Then scan promotions, social, updates, and forums for new clutter since the last run. Honor standing rules: never touch Starred, Important, or Keep; always preserve bank, insurance, school, and family; never delete, archive, unsubscribe, or send without Manny’s explicit yes in Email Purger's chat.

Group candidates by type (newsletters, promotions, stale, other). Prepare proposed delete, archive, and unsubscribe actions. Write a short proposal under /workspace/email-purger/ with today’s date.

Passive: if nothing material is new, stay silent (no “nothing new” message). If there is a real proposal, hand it to Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f) for Manny to review in Email Purger's chat, and wait for his approval there before changing anything. Never message Manny in the Routines chat, and never ask him for approval there.

Who receives the result and where: Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f), so Manny can review the proposal in Email Purger's chat, only when there is a proposal needing approval; otherwise no one. When there is nothing new: stay silent. The copy never messages Manny in the Routines chat and never asks him for approval there.
```
