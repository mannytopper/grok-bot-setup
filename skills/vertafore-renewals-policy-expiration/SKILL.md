---
name: vertafore-renewals-policy-expiration
description: >-
  Use when pulling the AMS360 renewals-due list: run the Vertafore "Policy
  Expiration" report, clean it into a 30-day / 31-60-day workbook, and deliver
  it.
---
# Vertafore Renewals: Policy Expiration

The routine or chat that calls this skill names the sign-in method (Vault login), the producer filter, where to deliver the workbook, and the trigger. Sign-in is shared with the vertafore-download-detail-mt and process-transactnow-payment-claims skills. This report is read-only: never change policies, and never touch the "Download Detail Modified MT" template or run.

## 1. Sign in
- Use the box's own browser through Vertafore VSSO, and reuse a live session if there is one.
- Fill the password only with the caller's Vault login through secure fill. Never type, guess, or screenshot it.
- At any sign-in or verification code, stop and let the parent handle it while the user is in chat. If sign-in fails, report it and stop. Don't retry in a loop.

## 2. Run the report
- Go to reports.vertafore.com (AMS360 Toolbox, then My Agency Reports).
- Run the standard template **"Policy Expiration"** with the Date option **"Expiring next 60 days"**. Leave everything else at its default.
- Saving a custom template failed before because the report viewer wouldn't open, so use the standard template with the rolling 60-day option each time.
- Wait for the run to finish under My Reports, then export it with the Excel icon to `/workspace/ams/renewals/renewals-YYYY-MM-DD.xlsx`.
- Delete only that completed run with its **x** icon. There's no confirmation prompt, and you must keep every template.

## 3. Clean the export
```bash
cd /workspace/ams/renewals
python3 /workspace/ams/clean_renewals.py renewals-YYYY-MM-DD.xlsx "Renewals Due YYYY-MM-DD.xlsx"
```
The script, at its fixed home:
- keeps Active policies only;
- keeps only the producer it is set for (Primary Executive filter);
- drops any policy (number plus expiration date) already on an earlier list, tracked in `/workspace/ams/renewals/seen.json`;
- keeps these columns: Customer Name, Policy Number, Policy Type LOB, Parent Company, Policy Expiration Date, Policy Full Term Premium, Primary Executive;
- writes two sheets, "Due in 30 days" and "Due in 31-60 days".

Exit 1 means a needed column is missing (the headers are printed). Stop and report it. Keep the raw export only until cleaning succeeds, then delete it.

## 4. Deliver
- Send the cleaned workbook where the caller says, with one sentence giving the two counts (due in 30 days, due in 31-60 days).
- If the caller names a computer and folder, copy the workbook there and open it in Excel too.

## 5. Report
Give the two counts, say whether any policies were dropped as repeats, and confirm the report run was deleted. If there were no rows, or sign-in failed, say so and stop.
