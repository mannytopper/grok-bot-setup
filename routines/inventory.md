# Routines move inventory (2026-11-12)

Prepared for the Routines bot (routine host) from owner-bot replies and exports on Nov 12, 2026. No routine was created, paused, or changed, and no one was messaged.

Context files are in `/workspace/routines/context/<folder-id>.md`. Each file has the verbatim original prompt (or a flag if it could not be retrieved) and a proposed Routines-copy prompt. Dreamer's six context files were written separately and are listed here as **moving now**; they were not overwritten.

Murray's `miami-trip-daily-brief` is skipped: today's card is its last, and it deletes itself after the Nov 12 card. No context file was written for it.

Notes that apply across the list:

- Routines' own inbox is `mtopper@mail.grokbot.com` (the same base address the other bots cite).
- Gmail, Outlook, Outlook calendar, and Google Calendar connectors are already connected for Routines.
- WHI-LT-26-03 (machineId `cc87a891-f809-4773-a01b-4755b0cc5cc6`) is registered but was offline when this inventory was written.
- Usage Guard is off-limits and is not listed.
- Nothing was paused or deleted. Copies are not created in this pass.

## Inventory

| Owner | Folder | Schedule / trigger | Enabled | Local execution? | Standing send? | Hook? | Move risk |
|---|---|---|---|---|---|---|---|
| Murray · Family and Home | `family-price-watches` | Email: mtopper+price-fly5d@mail.grokbot.com from noreply@camelcamelcamel.com | Enabled | No | No | Yes (CamelCamelCamel plus-address) | High — plus-address must work on Routines' inbox or CamelCamelCamel must be re-pointed |
| Murray · Family and Home | `bestgloal-email-price-watch` | Email: mtopper+price-bestgloal@mail.grokbot.com from noreply@camelcamelcamel.com | Enabled | No | No | Yes (CamelCamelCamel plus-address) | High — plus-address must work on Routines' inbox or CamelCamelCamel must be re-pointed |
| Murray · Family and Home | `gliston-email-price-watch` | Email: mtopper+price-gliston@mail.grokbot.com from noreply@camelcamelcamel.com | Enabled | No | No | Yes (CamelCamelCamel plus-address) | High — plus-address must work on Routines' inbox or CamelCamelCamel must be re-pointed |
| Murray · Family and Home | `weekday-local-feed` | Cron 0 8 * * 1-5, flexible 15/15, America/New_York | Enabled | No | No | No | Low |
| Murray · Family and Home | `order-concierge-sweep` | Cron 15 9 * * 1-5, flexible 15/15, America/New_York | Enabled | No | No | No | Low — confirm Gmail account and includeSpamTrash |
| Murray · Family and Home | `miami-trip-daily-brief` | Cron 0 7 * * 0-4, flexible 15/15 (Sun–Thu 7:00 AM ET) | Enabled (ends today, Nov 12) | No | No | No | Skip — last card is today; it deletes itself after the Nov 12 card. No context file written. |
| Insurance info · Meeting Prep | `answer-emailed-insurance-questions` | Email: mtopper+insurance@ and mtopper@ mail.grokbot.com, no sender filter | Enabled | No | Yes — Oct 14 staff auto-replies | Yes (two email listeners) | High — standing send must be re-granted by Manny; listeners must be recreated |
| Insurance info · Meeting Prep | `wiki-sync-on-login-company-forms-rates` | Webhook from Windows Desk login ping on WHI-LT-26-03 | Enabled | Yes | No | Yes (login webhook; URL is a secret) | High — admin PowerShell to repoint webhook; laptop currently offline |
| Insurance info · Meeting Prep | `meeting-prep-docs-2-to-4-hours-before-each-meeti` | Cron 0 7 * * 1-5 flexible 15/15, plus email mtopper+meetingprep@ from manny@wealcatchmd.com | Enabled | Yes (copy finals) | No | Yes (Power Automate email) | High — confirm plus-address or repoint Power Automate; laptop offline for file copy |
| Insurance info · Meeting Prep | `open-office-follow-ups-watch` | Cron 30 9 * * 1-5, flexible 15/15, America/New_York | Enabled | No | No | No | Low |
| Parsha · Weekly Teen Parsha PDF | `weekly-parsha-pdf` | Cron 30 9 * * 5, flexible, America/New_York | Enabled | Yes (save + print + close Acrobat) | No (standing chat deliverable + print) | No | High this week — keep Nov 13 run on Parsha; needs local execution; Friday print collision with Alfred |
| Parsha · Weekly Teen Parsha PDF | `parsha-backup-check` | Cron 52 9 * * 5, flexible, America/New_York | Paused | Yes, only if it steps in | No | No | Medium — keep paused; same local-execution dependency if it ever runs |
| Connor · Executive Assistant | `desk-login-run-claims-download-detail` | Cron 0 7 * * 1-5, flexible 15/15, America/New_York (reminder only) | Enabled | No | Saved send rules apply to the real run, not the reminder | No | High — vault fill needs Manny in chat; Connor suggests keeping the run; verbatim prompt not retrieved |
| Connor · Executive Assistant | `shared-calendar-sync-manny-ronit` | Cron 0 7 * * 0 exact, plus Outlook Power Automate webhook | Enabled | No | No | Yes (Power Automate webhook; new URL on move) | High — webhook URL changes; prompt text not confirmed verbatim |
| Connor · Executive Assistant | `morning-combined-run-rundown-dashboard-inbox-dig` | Cron 0 7 * * 0-5, flexible 0 early / 15 late, America/New_York | Enabled | No | Yes — rundown and domain digest emails | No (reads Connor agent inbox) | High — may not read Connor's inbox; standing sends must be granted; prompt not confirmed verbatim |
| Connor · Executive Assistant | `weekly-grok-bot-setup-review` | Cron 0 7 * * 1, flexible 15/15, America/New_York | Enabled | No | No | No | Medium — prompt text not confirmed verbatim |
| Connor · Executive Assistant | `weekly-usage-dashboard-refresh` | Cron 0 7 * * 1, flexible 0 early / 15 late, America/New_York | Enabled | No | No | No | Medium — prompt text not confirmed verbatim; needs canvas edit access |
| Connor · Executive Assistant | `monday-waiting-on-you-list` | Cron 0 7 * * 1, flexible 15/15, America/New_York | Enabled | No | No | No | Medium — prompt text not confirmed verbatim |
| Connor · Executive Assistant | `reminder-finance-bank-of-america-connector-nov-1` | One-off cron 0 9 13 11 *, exact, America/New_York | Enabled | No | No | No | High this week — fires Nov 13; prompt not confirmed verbatim |
| Connor · Executive Assistant | `griot-s-interior-cleaner-check-in-dec-10` | One-off cron 45 6 10 12 *, exact, America/New_York | Enabled | No | No | No | Low — December one-off; prompt not confirmed verbatim |
| Email Purger | `monthly-gmail-cleanout` | Cron 0 8 1-7 * 1, flexible 15/15, America/New_York | Enabled | No | No | No | Low — proposals stay in Email Purger's chat per Manny's Nov 12 decision |
| Email Purger | `biweekly-work-outlook-cleanout` | Cron 15 8 * * 1, flexible 15/15, America/New_York; biweekly via lastRun | Enabled | No | No | No | Low — proposals stay in Email Purger's chat; preserve lastRun state |
| Spackler - Golf Practice | `golf-practice-evening-reminder` | Cron 50 19 * * 0,1,3, flexible 10/10, America/New_York | Paused (until Nov 15) | No | No | No | Medium — keep paused until the Nov 15 resume points at the correct copy |
| Spackler - Golf Practice | `muni-golf-ipad-app-watch` | Cron 45 6 * * 0, flexible 15/15, America/New_York | Paused | No | No | No | Low — keep paused |
| Spackler - Golf Practice | `resume-golf-practice-reminder` | One-off cron 0 12 15 11 *, exact, America/New_York | Enabled | No | No | No | High — must resume the correct copy on Nov 15 or the reminder can run twice |
| Alfred · Bot Chief Advisor | `weekly-company-grok-bot-improvement-review` | Cron 0 10 * * 5, flexible 15/15, America/New_York | Enabled | Yes (save + print one-pager) | No (standing chat+print deliverable) | No | High — local execution; Friday print collision with Parsha; transcript access from a scheduled run |
| Alfred · Bot Chief Advisor | `grokbot-dashboard-refresh` | Cron 50 8 * * 1, flexible 15/15, America/New_York | Enabled | No | No | No | High — scheduled run only hands off; real work is in Alfred's main session (ReadTranscript + EditCanvas) |
| Alfred · Bot Chief Advisor | `monthly-bot-portfolio-strategy-review` | Cron 30 9 1 * *, flexible 15/15, America/New_York | Paused | No | No | No | Low — keep paused |
| Alfred · Bot Chief Advisor | `quarterly-company-ai-operating-model-review` | Cron 0 10 1 1,4,7,10 *, flexible 15/15, America/New_York | Paused | No | No | No | Low — keep paused |
| Dreamer · Bot Team Optomizer | `nightly-dreaming-logs-to-skills` | Crons 30 21 * * 1-4 and 0 11 * * 5, flexible 15/15, America/New_York | Enabled | No | No | No | moving now |
| Dreamer · Bot Team Optomizer | `weekly-grok-bot-x-tips` | Cron 0 9 * * 5, flexible 15/15, America/New_York | Enabled | No | No | No | moving now |
| Dreamer · Bot Team Optomizer | `weekly-bot-fleet-audit` | Cron 30 9 * * 5, flexible 15/15, America/New_York | Paused (keep paused; Usage Guard covers this) | No | No | No | moving now |
| Dreamer · Bot Team Optomizer | `weekly-bot-scorecard` | Cron 45 9 * * 5, flexible 15/15, America/New_York | Enabled | No | No | No | moving now |
| Dreamer · Bot Team Optomizer | `weekly-routine-ideas` | Cron 0 10 * * 5, flexible 15/15, America/New_York | Enabled | No | No | No | moving now |
| Dreamer · Bot Team Optomizer | `weekly-grok-bot-marketplace-template-check` | Cron 0 11 * * 5, flexible 15/15, America/New_York | Enabled | No | No | No | moving now |

## Decisions for Manny

1. **Connor's AMS run.** The weekday routine is now only a "run ams now" reminder. The real Claims + Download Detail run needs Manny in chat for the Vertafore vault fill (vault id 1035329). Connor suggests keeping the run itself with Connor. If only the reminder moves, decide who handles the reply and whether saved send rules for the claims and Download Detail emails must be granted to Routines.
2. **Connor's calendar sync webhook.** Manny's Power Automate flow pings a webhook when Outlook changes. A Routines copy would get a new URL, which has to be pasted into that flow. Confirm the first real fire before the original is paused.
3. **Connor's morning run and Connor's agent inbox.** The inbox digest reads Connor's agent inbox (`mtopper@mail.grokbot.com`). Routines has the same base address, but Connor warned it may not be readable from another bot. Standing rundown and domain-digest emails also have to be granted to Routines.
4. **Connor one-off tomorrow.** The Finance (Bank of America) connector reminder fires Nov 13, 2026 at 9:00 AM ET. Moving it first risks a missed or double reminder; consider leaving this one-off on Connor.
5. **Insurance wiki-sync Windows task.** The login webhook URL would change. Repointing `%LOCALAPPDATA%\InsuranceWikiSync` / the "Desk login ping" task needs Windows admin rights, so it has to be done in an administrator PowerShell. The laptop is currently offline.
6. **Insurance meeting-prep Power Automate email.** The flow "Grok meeting prep webhook" sends mail to `mtopper+meetingprep@mail.grokbot.com` from the work Outlook account about two hours before each event. Confirm Routines can listen on that same plus-address; if it cannot, the flow needs a new destination. Final PDFs also copy to the laptop, which needs local execution and is currently offline.
7. **Insurance staff auto-reply standing permission (Oct 14, 2026).** Automatic replies to staff at the Wealcatch work domains were granted to Insurance info. That permission does not carry over on another bot's word. Manny has to grant it to Routines himself before the original is paused.
8. **Murray's CamelCamelCamel plus-address inboxes.** FLY5D, BESTGLOAL, and GLISTON alerts go to `mtopper+price-fly5d@`, `mtopper+price-bestgloal@`, and `mtopper+price-gliston@mail.grokbot.com`, which currently belong to Murray's agent inbox. Confirm Routines can receive at those exact addresses before moving; otherwise CamelCamelCamel has to be re-subscribed.
9. **Parsha's Friday Nov 13 run.** The weekly sheet (Vayetzei) should stay with Parsha this week so only one printer copy goes out. After that, Routines needs local execution on WHI-LT-26-03 (currently offline).
10. **Dreamer's nightly review.** It depends on Dreamer's journal memory (goals and last-run notes), which cannot be copied as files. Context files for Dreamer's six routines are being written separately (moving now) and point at `/workspace/dreamer/goals.md` as a stand-in; confirm that continuity is actually enough before the originals are paused.
11. **Spackler's Nov 15 resume one-off.** `resume-golf-practice-reminder` fires Sunday Nov 15 at 12:00 PM ET and turns `golf-practice-evening-reminder` back on. If the Routines copy of the evening reminder replaces Spackler's before then, this one-off has to point at the Routines copy, or it will turn the original back on and the reminder will run twice. Keep the evening-reminder copy paused until then, and do not test it before the evening of Nov 15.
12. **Alfred's dashboard refresh.** The Monday 8:50 AM ET scheduled run only hands off. The real work runs from Alfred's main session (ReadTranscript of every bot, plus canvas edits to `0ba3ca83-b62a-426d-926c-fb5c27231fef`). Check whether Routines can do that work itself before moving it.
13. **Alfred's Friday one-pager.** The Weekly Company & Grok Bot Improvement Review saves the PDF to `C:\Users\Manny\Documents\Grok Work\Weekly Summary\` and prints once on the Brother HL-L2420DW, so it needs local execution on WHI-LT-26-03 (currently offline).
14. **Alfred's originals.** Alfred needs Manny's yes in Alfred's own chat before it pauses or deletes its originals.
15. **Friday printer collision.** Parsha's sheet (9:30 AM ET) and Alfred's one-pager (10:00 AM ET) both print on Friday on the same Brother HL-L2420DW. After both have moved, the two jobs can overlap if the laptop or printer is busy.

## Prompt retrieval notes

- **Retrieved verbatim** from owner replies, handoff files, or the Nov 9/12 exports named in the brief: Murray (5 moved; Miami skipped), Insurance info (4), Parsha (2), Email Purger (2), Spackler (3), Alfred (4).
- **Connor (8):** exact prompts were supposed to come from Connor's session transcript on Nov 12, 2026 around 11:20Z (UpdateRoutine get results; AMS prompt updated Nov 11 around 12:18Z). ReadTranscript returned spoken messages only and left tool calls out, so those get results were not recoverable. For seven routines, the Nov 9 export prompt is included and clearly flagged; current folder ids, schedules, and permissions are taken from Connor's Nov 12 handoff (several crons have changed since the export, and some prompt text still mentions the old time). For `desk-login-run-claims-download-detail`, the Nov 9 export prompt is the superseded automated run, not the current reminder-only prompt, and must not be used to create the copy.
