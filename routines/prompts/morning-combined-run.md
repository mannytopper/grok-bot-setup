Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). Wherever this says "this Grok Bot chat" or "Connor's chat", it now means the Routines chat. Every send rule, recipient limit and gate below is unchanged.

---
Manny's combined morning run, Sunday to Friday at about 7:00 AM ET, on the box only. Each part is independent: if one fails, note it and keep going. Skill: morning-combined-run. Usage trim approved by Manny in Volt's chat, Nov 16, 2026: read only the part files for parts that run today, and only each part's own script or README; pull only what changed since the last run; never paste raw mailbox or calendar contents into chat. Every output and standing email is unchanged.

Quiet rule (Manny, Nov 5, 2026): routines stay silent and only message him in chat when something needs his attention. The standing emails below still go out as usual.

Attachments rule (Manny approved Nov 5, 2026, to cut usage): every Gmail send with an attachment must pass the attachment's content as a "$file:/path/to/file.b64" argument (the whole string value, nothing else), pointing at a base64 file written on the box (for example with `base64 -w0 file.pdf > file.b64`). Never read a .b64 file into the conversation and never paste base64 text into a tool call. Cleanup (Manny approved Nov 6, 2026): right after each send succeeds (or is found already sent), delete that send's .b64 file and any older .b64 files in the same folder, so no attachment copies pile up. Keep the PDF and PPTX files.

Step 0, gate and parts (no-AI scripts, Manny approved Nov 6, 2026; skills routine-gate and morning-parts):
1. Run `python3 /workspace/common/routine_gate.py --days Sun,Mon,Tue,Wed,Thu,Fri`. Exit 10 means skip (Saturday, Shabbat or Yom Tov): do nothing at all and send nothing. Exit 0 means run.
2. Run `python3 /workspace/common/morning_parts.py`. It prints JSON with a boolean for each part (A_calendar_dashboard, B_rundown_pdf, C_inbox_digest, D_tesla_watch, E_domain_digest, F_x_watch). Run only the parts marked true; don't work out the day rules by hand.
3. Fallback only if either script errors: run `python3 /workspace/common/hebcal_check.py` (skip if it prints "skip": true), or check the Hebcal API (Diaspora mode) yourself. Never run on Saturday. Yom Tov means both days of Rosh Hashanah, Yom Kippur, the first two and last two days of Sukkot (Shemini Atzeret and Simchat Torah), the first two and last two days of Pesach, and both days of Shavuot. Chol HaMoed, fast days, Chanukah and Purim don't count. Then apply the day rules written in each part below, and add one line to the chat message saying which script failed.


Parts (open /workspace/routines/prompts/morning-parts/<letter>.md only for parts marked true):
- A: calendar dashboard refresh (Page "Manny's Calendar")
- B: morning day rundown PDF, emailed to mannytopper@gmail.com
- C: inbox digest one-pager (Mon-Fri), plus the full "Waiting on you" list (every open dq.py item)
- D: Tesla / Enhance S3XY / Clicks watch (Mondays)
- E: domain sales digest PDF, emailed to mannytopper@gmail.com and [REDACTED] (Mondays)
- F: Grok Bot X watch deck (Mon/Wed/Fri)

Recipients and delivery: the rundown and X watch emails go only to mannytopper@gmail.com, and the domain digest email goes only to mannytopper@gmail.com and [REDACTED]. Never send anything to any b52media.com or b52.com address, or to lborck@ or lbork@. The inbox digest, the Tesla watch update, and any failure notes go only to Manny in this Grok Bot chat (Connor's chat). No one else is messaged. When everything succeeds and neither Part C nor Part D has anything that needs Manny, post nothing in chat.

If a part file is missing, use the full backup at /workspace/routines/backups/morning-combined-run.2026-11-16.md and add one line to the chat message.
