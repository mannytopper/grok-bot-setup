Created by Routines on Nov 13, 2026 (Manny picked idea 2; he chose 30 and 60 day windows, not 90). Read /workspace/shared-brain/INDEX.md first.

1. Gate: `python3 /workspace/common/routine_gate.py --days Mon` (exit 10 = stop silently; if it errors, `python3 /workspace/common/shabbat_gate.py`, exit 10 = stop silently).
2. Ask first (Manny's Nov 12 rule: it needs a browser helper and his Vertafore login while he's in chat): send Manny one line in the Routines chat: "Weekly renewals list is due: reply yes when you're at your desk and I'll pull the Vertafore Policy Expiration report (next 60 days)." Then end this run. Do nothing else.

When Manny says yes in the Routines chat, Routines (not this run) does the work:
- computerUse helper on reports.vertafore.com (AMS360 Toolbox, My Agency Reports): run the standard Vertafore template "Policy Expiration" with the Date option "Expiring next 60 days", defaults for everything else; read-only, never change policies or touch "Download Detail Modified MT". Stop at any sign-in or code; Routines fills the saved Vertafore Vault login (same login the AMS run uses) while Manny is in chat. Export to Excel as /workspace/ams/renewals/renewals-YYYY-MM-DD.xlsx, then delete only that completed run in My Reports.
- Clean: `python3 /workspace/ams/clean_renewals.py renewals-YYYY-MM-DD.xlsx "Renewals Due YYYY-MM-DD.xlsx"` (Active only; sheets "Due in 30 days" and "Due in 31-60 days"; exit 1 = column missing, tell Manny).
- Send Manny the cleaned workbook in the Routines chat with one sentence giving the two counts. Delete the raw export afterward.
(Saving a custom template failed on Nov 13, 2026: the report viewer wouldn't open, so the standard template with the rolling 60-day option is used each week.)

- Nov 13: Manny asked to show only policies where Primary Executive is "Topper, Manny"; clean_renewals.py now filters that, so the counts cover only his book.
- Nov 13: format saved per Manny: columns Customer Name, Policy Number, Policy Type LOB, Parent Company, Writing Company, Policy Expiration Date, Policy Full Term Premium, Primary Executive (no Line Of Business, no Primary Representative); only Topper, Manny.

## Open in Excel (Manny, Nov 13, 2026)
After cleaning, copy the workbook to Manny's laptop WHI-LT-26-03 (machineId cc87a891-f809-4773-a01b-4755b0cc5cc6) at C:\Users\Manny\Documents\grok work\Renewals\Renewals Due YYYY-MM-DD.xlsx (CopyFromBox), then open it there in Excel: Shell on that machine, `Start-Process "<that path>"`. Still send the workbook in chat with the two counts.
- Nov 16: Manny asked to remove the Writing Company column from all future renewals reports; clean_renewals.py updated.
- Nov 16: Manny asked for no repeats from prior lists; clean_renewals.py now drops any policy (number + expiration date) already on an earlier list, tracked in /workspace/ams/renewals/seen.json (seeded from the Nov 13 and Nov 16 lists). Keep the raw export only until cleaning succeeds.
