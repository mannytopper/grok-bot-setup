First-Monday check (added Nov 13, 2026): run `date +%u` and `date +%d` (America/New_York). Continue only if today is a Monday (%u = 1) and the day of the month is 01 to 07. Otherwise stay silent and end now.

Moved to Routines from Email Purger on Nov 12, 2026. Context: /workspace/routines/context/monthly-gmail-cleanout.md.

Ask-first (Manny, Nov 12, 2026): before opening more than 5 web pages for one task, starting a subagent, re-running a step that already failed twice, or any job expected to take more than 15 minutes, hand Manny a one-line ask of what and why to Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f) as a handoff that ends with "No reply needed.", and wait for his yes in Email Purger's chat. Never message Manny in the Routines chat. Exception: standing deliverables he already approved run as usual.

Run a read-only cleanout scan of mannytopper@gmail.com for Email Purger.

First: run the Shabbat/Yom Tov gate (`python3 /workspace/common/shabbat_gate.py`). If exit 10, stay silent and end.

Then scan promotions, social, updates, and forums for new clutter since the last run. Honor standing rules: never touch Starred, Important, or Keep; always preserve bank, insurance, school, and family; never delete, archive, unsubscribe, or send without Manny’s explicit yes in Email Purger's chat.

Group candidates by type (newsletters, promotions, stale, other). Prepare proposed delete, archive, and unsubscribe actions. Write a short proposal under /workspace/email-purger/ with today’s date.

Passive: if nothing material is new, stay silent (no “nothing new” message). If there is a real proposal, hand it to Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f) as a handoff that ends with "No reply needed.", for Manny to review in Email Purger's chat, and wait for his approval there before changing anything. Never message Manny in the Routines chat.

Who receives the result and where: Email Purger (Grok Bot agent id 604b5043-13ef-4fed-8501-7fa24112766f), as a handoff that ends with "No reply needed.", so Manny can review a real proposal in Email Purger's chat; otherwise no one. When there is nothing new: stay silent. This copy never messages Manny in the Routines chat.
