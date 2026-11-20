# Weekly bot fleet audit (moved from Dreamer, folder weekly-bot-fleet-audit, 2026-11-12)

Original enabled: False
Schedule: 30 9 * * 5 (America/New_York), Flexible schedule with a 15-minute window either side. Paused after Nov 6, 2026 because Usage Guard's weekly review covers it. Instruction text is the last verbatim Optomizer update of weekly-bot-fleet-audit (Dreamer's UpdateRoutine get was not readable from this export run).

Context: goals and watch items live in /workspace/dreamer/goals.md (replaces Dreamer's memory). Any 'memory' or 'journal' step means /workspace/dreamer/goals.md or /workspace/dreamer/journal.md. Never touch Usage Guard.

## Prompt for the Routines copy

Manny's weekly read-only usage audit of all his Grok Bots. It moved here from Bot Optomizer on Nov 5, 2026, at Manny's request.

At the start of this run, read /workspace/shared-brain/INDEX.md and open any file whose topic fits (rules, routines, scripts, lessons), and apply what's relevant. Append lasting fleet-audit lessons other bots can use to /workspace/shared-brain/lessons.md as '- (YYYY-MM-DD, Routines) ...' (never secrets or personal contact details), then run chmod -R a+rX /workspace/shared-brain.

Run the audit by following the @Bot fleet usage audit skill (bot-fleet-usage-audit). Change nothing on any bot or routine. If today is a Jewish holiday (Yom Tov), skip the run and send nothing (python3 /workspace/common/shabbat_gate.py; exit 10 means skip). If /workspace/bot-audit/history/ already has a snapshot for today's date, the audit already ran today, so skip the run and send nothing.

Manny's rules to check: nothing may run or reach him on Shabbat (Saturday, or Friday after candle lighting) or on Yom Tov, and flag any routine that does prominently. No routine may email a b52media.com address or lborck@/lbork@.

Follow-ups this week, from changes made Oct 30 to Nov 5, 2026: Connor merged three morning routines into "Morning combined run" at 6:45 AM Sunday to Friday. Insurance info's meeting prep went from about 36 runs a week to 17. On Nov 4, Spackler's Muni Golf watch, Parsha's backup check and Murray's Callaway Strata Plus price watch were paused, and Connor, Insurance info, Parsha, Murray and Dreamer moved repeated steps into scripts and skills. On Nov 5, Connor's calendar dashboard started reusing the morning calendar sync, and attachments started being passed as file paths instead of pasted base64. Report what these changes did to usage. Drop this follow-up paragraph once it has been reported.

Build the week's input JSON and render it with python3 /workspace/bot-audit/audit.py INPUT.json (defaults: out-dir /workspace/bot-audit, history-dir /workspace/bot-audit/history; it uses /workspace/bot-audit/.venv for WeasyPrint). The report is report-DATE.html and .pdf in /workspace/bot-audit/, and the snapshot goes in history/. Keep it grayscale for black-and-white printing. "Largest chats this week" is for information only; don't tell him to clear chats.

Passive delivery (Manny, Nov 5, 2026): stay silent on skips, on successes with nothing to hand him, and on routine-status chatter. The Friday audit HTML and PDF are a standing report he asked for, so deliver them to Manny in the Routines chat in Grok Bot with a short summary (usage used and when it resets, the biggest week-over-week changes, the top 3 fixes, and the largest chats this week), well before Shabbos. Outside that report, message him only when something failed or he needs to act or decide.

## Original prompt (verbatim)

Manny's weekly read-only usage audit of all his Grok Bots. It moved here from Bot Optomizer on Nov 5, 2026, at Manny's request.

At the start of this run, read /workspace/shared-brain/INDEX.md and open any file whose topic fits (rules, routines, scripts, lessons), and apply what's relevant. Append lasting fleet-audit lessons other bots can use to /workspace/shared-brain/lessons.md as '- (YYYY-MM-DD, Dreamer) ...' (never secrets or personal contact details), then run chmod -R a+rX /workspace/shared-brain.

Run the audit by following the @Bot fleet usage audit skill (bot-fleet-usage-audit). Change nothing on any bot or routine. If today is a Jewish holiday (Yom Tov), skip the run and send nothing (python3 /workspace/common/shabbat_gate.py; exit 10 means skip). If /workspace/bot-audit/history/ already has a snapshot for today's date, the audit already ran today, so skip the run and send nothing.

Manny's rules to check: nothing may run or reach him on Shabbat (Saturday, or Friday after candle lighting) or on Yom Tov, and flag any routine that does prominently. No routine may email a b52media.com address or lborck@/lbork@.

Follow-ups this week, from changes made Oct 30 to Nov 5, 2026: Connor merged three morning routines into "Morning combined run" at 6:45 AM Sunday to Friday. Insurance info's meeting prep went from about 36 runs a week to 17. On Nov 4, Spackler's Muni Golf watch, Parsha's backup check and Murray's Callaway Strata Plus price watch were paused, and Connor, Insurance info, Parsha, Murray and Dreamer moved repeated steps into scripts and skills. On Nov 5, Connor's calendar dashboard started reusing the morning calendar sync, and attachments started being passed as file paths instead of pasted base64. Report what these changes did to usage. Drop this follow-up paragraph once it has been reported.

Build the week's input JSON and render it with python3 /workspace/bot-audit/audit.py INPUT.json (defaults: out-dir /workspace/bot-audit, history-dir /workspace/bot-audit/history; it uses /workspace/bot-audit/.venv for WeasyPrint). The report is report-DATE.html and .pdf in /workspace/bot-audit/, and the snapshot goes in history/. Keep it grayscale for black-and-white printing. "Largest chats this week" is for information only; don't tell him to clear chats.

Passive delivery (Manny, Nov 5, 2026): stay silent on skips, on successes with nothing to hand him, and on routine-status chatter. The Friday audit HTML and PDF are a standing report he asked for, so deliver them to Manny in this Dreamer chat with a short summary (usage used and when it resets, the biggest week-over-week changes, the top 3 fixes, and the largest chats this week), well before Shabbos. Outside that report, message him only when something failed or he needs to act or decide.
