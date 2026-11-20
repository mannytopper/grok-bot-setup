# AMS: daily run ams now reminder (owner: Connor · Executive Assistant, folder: desk-login-run-claims-download-detail)

- **Owner bot:** Connor · Executive Assistant
- **Original folder id:** `desk-login-run-claims-download-detail`
- **Enabled state:** Enabled (all eight Connor routines are enabled)
- **Schedule/trigger:** `CRON_TZ=America/New_York 0 7 * * 1-5` (weekdays around 7:00 AM ET). No webhook. (Older exports still show 8:00 AM or a desk-login webhook; current schedule is 7:00 AM from Connor's Nov 12 handoff.)
- **Timing:** Flexible, 15 minutes early or late
- **Connectors/accounts:** The scheduled reminder itself posts in chat only. The real run (after Manny replies "run ams now" in Connor's chat) uses computerUse, the Gmail connector to send the Download Detail report to the work inbox, and standing claim emails to Myron at the Wealcatch work domain. Vertafore Vault login id 1035329, fills only when Manny is in chat. No local execution on the laptop; work runs on the box.
- **Scripts:** `/workspace/common/routine_gate.py`, `/workspace/common/sent_marker.py`, `/workspace/ams/dd_date_range.py`, and `clean_download_detail.py`.
- **Skills:** process-transactnow-payment-claims, vertafore-download-detail-mt, routine-gate
- **Files/state:** AMS scripts and markers under `/workspace/ams/` and sent-marker state. Do not copy vault secrets; logins stay in the vault.
- **Memory facts:** Manny keeps Shabbat and Yom Tov. The scheduled routine cannot use the saved Vertafore login unless Manny is in chat. Duplicate claim emails or a duplicate report must never go out. Never send to any b52media.com or b52.com address, or to lborck@ or lbork@.
- **Permissions:** Saved send rules cover the claims emails and the Download Detail email for the real run. Those sends happen after Manny's "run ams now" in Connor's chat today, not from the scheduled reminder alone. No local execution on WHI-LT-26-03. No standing auto-send from the reminder itself.
- **Hooks:** None (webhook was removed; reminder is cron-only).
- **Open issues:** Verbatim current prompt was not retrieved (see flag below). Connor suggests leaving the actual run with Connor, because the vault fill only works when Manny is in that chat. If only the reminder moves, decide who handles "run ams now" and whether saved send rules must be granted to Routines.

## Original prompt (verbatim)

_FLAG: the current verbatim saved prompt could not be retrieved. Connor updated this routine on Nov 11, 2026 around 12:18Z (7:18 AM ET) so it only posts a "run ams now" reminder in chat; the Nov 9 export prompt below describes the older automated Claims + Download Detail run and is NOT the current saved prompt. It is included only as the last full prompt text on disk, clearly superseded. Do not use it to create the Routines copy. Current behavior, from Connor's Nov 12 handoff: cron weekdays 7:00 AM ET, flexible 15/15; it only posts a reminder in chat. The real run cannot be automated: the Vertafore Vault login (id 1035329; fill references vault_1035329_username and vault_1035329_password) only fills when Manny is in chat. When he replies "run ams now", Connor uses computerUse, Gmail send to the work inbox, claims emails to Myron at the work domain, and the claims/download-detail skills. Connor suggests leaving the run itself with Connor._

```
This runs on a schedule every weekday at about 8:00 AM ET. Manny switched it from the desk-login webhook to a regular schedule on Nov 9, 2026, by voice, and moved it from 9 to 8 AM the same day, so it no longer waits for his laptop. Everything runs on Connor's computer (the box) with the Vertafore login saved in his Vault.

Gate checks (if any fails, stop quietly and message no one):
- Run `python3 /workspace/common/routine_gate.py --days Mon,Tue,Wed,Thu,Fri` (routine-gate skill, Manny approved Nov 6, 2026). Exit 10 means skip (weekend, Shabbat or Yom Tov). If the script errors, check yourself: it must be Monday–Friday in America/New_York, never Saturday or Sunday, and never a Jewish holiday (Yom Tov).
- Run only once per day. Check RecallMemory for a "Desk-login AMS run done for YYYY-MM-DD" fact for today, run `python3 /workspace/common/sent_marker.py check download-detail:YYYY-MM-DD` (exit 1 = report already sent), and look in this conversation for today's Claims or Download Detail already having been run or emailed. If any job is already done, skip that job. Duplicate claim emails to myron@ or a duplicate report to manny@wealcatchmd.com must never happen.

Then do the jobs on Connor's computer (the box) only, in one Vertafore session:

1. Claims Payment Emails (Vertafore TransactNOW Claims, https://transactnow.vertafore.com/Claim). Follow the process-transactnow-payment-claims skill. Email each unread Payment claim once to myron@wealcatchmd.com with "CC Myself" unchecked. Then delete ALL claims, except any whose email failed. If there are none, note "no claims".
2. Download Detail MT (reports.vertafore.com, saved template "Download Detail Modified MT"). Follow the vertafore-download-detail-mt skill:
   - Get the dates from `python3 /workspace/ams/dd_date_range.py` and set them with Select Dates. Tuesday–Friday: today to today ("Current date"). Monday: the prior Saturday through today.
   - Export to Excel, then clean it with `python3 /workspace/ams/clean_download_detail.py INPUT.xlsx OUTPUT.xlsx` (removes "Renew policy", "Policy change", and "Renewal quote" rows, dedupes on Policy Number keeping the first, sorts A→Z by Transaction Description, keeps Parent Company, Customer Name, Policy Number, Line of Business, Primary Executive, Transaction Effective Date, Transaction Description, autofits).
   - Email it from Manny's Gmail to manny@wealcatchmd.com with the subject "Download Detail MT — YYYY-MM-DD". Send it in one step, with the file attached directly to the Gmail send (content passed as "$file:<path>.b64"), then delete the .b64. Confirm exactly one email went out, never send twice, and afterward run `python3 /workspace/common/sent_marker.py mark download-detail:YYYY-MM-DD`.
   - Afterward, delete the local files and the completed run in My Reports, but never the template.

(Manny removed the Monday AMS360 active-customers list on Oct 19, 2026; don't run it.)

Vertafore sign-in: use Manny's saved Vault login (Vault id 1035329, entry "login.apps.vertafore.com"), which he approved. If Vertafore or the reports site needs a password or sign-in, stop and hand back to the parent conversation. Connor then fills the saved Vault login in the box browser through the secure fill, and sends Manny the secure password form in chat only if that fill fails. If 2FA appears, the parent handles it with Manny (message him). Never guess, type or screenshot a password yourself.

When the jobs are done, write the memory fact "Desk-login AMS run done for YYYY-MM-DD" with the claims count and the Download Detail row counts. Stay silent in chat when everything succeeds (Manny's rule from Nov 5, 2026: routines stay quiet and only message him when something needs his attention). Message Manny in this Grok Bot chat only when something needs him: a sign-in he must help with, a two-step verification code, a claim email that failed, a report that failed or couldn't be sent, or anything else he must act on, in one or two short lines. The standing work emails above still go out as usual. If the gate stops the run, send nothing.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/desk-login-run-claims-download-detail.md for context.

FLAG: do not use this as the live prompt until the current verbatim reminder prompt is retrieved from Connor.

Current intended behavior (from Connor's Nov 12, 2026 handoff, not a verbatim saved prompt):
Gate with /workspace/common/routine_gate.py for weekdays (exit 10 = skip silently). If today is already done, stay silent.
Otherwise send Manny one short reminder in the Routines chat in Grok Bot asking him to reply "run ams now" so the Claims and Download Detail run can use his Vertafore Vault login while he is in chat. Do not try to sign in or run Claims or Download Detail from this scheduled reminder while he is not in chat. Message him only for that reminder, or if something failed.
```
