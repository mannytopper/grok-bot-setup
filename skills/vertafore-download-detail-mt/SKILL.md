---
name: vertafore-download-detail-mt
description: >-
  Use when running, exporting, cleaning and emailing the AMS360 "Download Detail
  Modified MT" report from Vertafore, or answering questions about its date
  range or filters.
---
# Vertafore Download Detail MT

The routine that calls this skill names the agency, the sign-in method (Vault login), the recipient, and the trigger. Sign-in and the desk-login run are shared with the process-transactnow-payment-claims skill; do the claims part with that skill and only this report here. Do not run Claims Docs, eDocs or TransactNOW from this skill, and do not change policies.

## 1. Sign in
- Run on the box's own browser through Vertafore VSSO. Reuse a live session if there is one.
- Fill the password only with the routine's Vault login through secure fill. Never type, guess or screenshot it. If the fill fails, ask through the secure form. If sign-in fails, tell the user and stop this run; no retry loop.

## 2. Run the report
- reports.vertafore.com (AMS360 Toolbox, then My Agency Reports): run the saved template "Download Detail Modified MT".
- Date range (Eastern time). Get it from `python3 /workspace/ams/dd_date_range.py` (JSON: `run`, `mode` current_date or custom, `from`, `to`; `run: false` on weekends):
  - Tuesday to Friday: choose the **"Current date"** option (today to today).
  - Monday: from the prior Saturday through today, inclusive.
- Wait for the run to finish under My Reports, then export it with the Excel icon on the completed run. Save the file to a dated folder such as `/workspace/ams/YYYY-MM-DD/`.

## 3. Clean the export
```bash
python3 /workspace/ams/clean_download_detail.py INPUT.xlsx OUTPUT.xlsx
```
(The fixed home of the script. Needs openpyxl.) It, in order:
1. drops rows whose Transaction Description is "Renew policy", "Policy change" or "Renewal quote" (case and spacing ignored);
2. removes duplicate Policy Numbers, keeping the first;
3. sorts A to Z by Transaction Description;
4. keeps only Parent Company, Customer Name, Policy Number, Line of Business, Primary Executive, Transaction Effective Date, Transaction Description;
5. widens columns to fit.

It prints `raw_rows`, the three `removed_*` counts, `after_category_filter`, `duplicates_removed`, `final_rows`, `output`. Exit 1 means a needed column is missing (headers are printed): stop and report. Wrong arguments exit 2.

## 4. Email
- Gmail to the recipient the routine names, subject like `Download Detail MT — YYYY-MM-DD`, the cleaned xlsx attached.
- Never send twice: `python3 /workspace/common/sent_marker.py check download-detail:YYYY-MM-DD` (exit 1 = already sent, stop) and also check Sent for today's subject. After a successful send run `sent_marker.py mark download-detail:YYYY-MM-DD`.
- Attachment: `base64 -w0 OUTPUT.xlsx > OUTPUT.b64`, then pass the attachment content as the whole string `"$file:/path/OUTPUT.b64"`. Never read or paste the base64.

## 5. Clean up
- In My Reports, delete the completed run with its **x** icon. There is no confirmation prompt, so click only that run's x. Keep the saved template.
- Delete the Excel files from the box once the email is sent.

## 6. Report
Tell the user the date range and the before/after row counts (raw, each filter, duplicates, final). If there were no rows or sign-in failed, say so and stop. Log one fact that the run is done for the date so a second trigger skips it.
