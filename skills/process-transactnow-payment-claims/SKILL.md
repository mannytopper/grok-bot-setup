---
name: Process TransactNOW Payment Claims
description: >-
  Use when emailing unread Payment claims from Vertafore TransactNOW Claims and
  deleting them after send.
---
# Process TransactNOW Payment Claims

Assumes signed in to AMS360 / Vertafore VSSO on this computer’s browser. Agency and recipient are inputs from the caller (routine or chat).

## Inputs
- `{agency}` — AMS360 agency (e.g. Herman E. Wealcatch, Inc. 1011581-1)
- `{payment_claim_email_to}` — fixed To address for every Payment claim email

## Steps
1. Open AMS360 (https://www.ams360.com/). Complete VSSO login if needed (secure form for passwords; reuse session when still logged in). Confirm agency `{agency}`.
2. From AMS360 Home, open **TransactNOW** (sidebar). Wait for TransactNOW to load on the **Claims** tab (`https://transactnow.vertafore.com/Claim`). Do not use the eDocs & Messages tab for this workflow.
3. Work only claims whose Type is **Payment**. Ignore First Report of Injury and all other types.
4. For each Payment claim, one at a time (send **once** only):
   - Select that row (checkbox if present; otherwise click/select the row).
   - Open email via toolbar **Forward** (or envelope Email icon if present).
   - In **Claim Email**, leave pre-filled subject/body; set **To** to `{payment_claim_email_to}`, and UNCHECK the **CC Myself** checkbox (it is checked by default; the dialog has no Cc/Bcc text fields). Manny is never cc'd; the To address is the only recipient.
   - Click **Send** once. Treat dialog close as sent; do not resend that claim.
5. After all Payment claims for this run have been emailed once, select those same rows and use toolbar **Delete** → **Delete Selected Claim(s)** → confirm **Yes** on the delete prompt.
6. Report: Payment claims emailed count, To address, remaining claims count, failures.

## Do not
- Email non-Payment claims or resend the same claim in one run.
- Leave anyone in Cc or Bcc, especially Manny (any of his addresses).
- Delete claims that were not emailed in this run.
- Change policies.

## Confirm first
Sending/deleting is consequential on a first dry run; weekday routines with explicit send/delete instructions may proceed.
