---
name: inbox-digest-build
description: >-
  Use when building the daily inbox digest one-pager (PNG and PDF) from the
  user's mailboxes with /workspace/inbox-digest/render.py.
---
# Inbox digest build

Files: `/workspace/inbox-digest/render.py`, `README.md` (full JSON schema), daily JSONs `YYYY-MM-DD.json` (use a recent one as a template), output in `out/`. Usually run as one part of the morning-combined-run skill.

## Steps
1. **Collect** mail since the previous digest from the inboxes the routine names (Gmail, Outlook and the bot's own inboxes via their connectors/tools). Read only; change nothing in any inbox. Use only facts from the mail.
2. **Waiting on you:** run `python3 /workspace/decision-queue/dq.py list --open` and add each item to the `needs` section (see decision-queue).
3. **Write** `/workspace/inbox-digest/YYYY-MM-DD.json`: `date` (required), `title`, `coverage`, `inboxes` [{source,label}], `sections` with `id` of `needs` | `important` | `insurance` and items {sender, subject, source (gmail | outlook | grok | grok-insurance), summary, optional source_note, priority high|normal|low, status}, `rollup` chip groups, `footer`. Keep summaries to one or two sentences (200 character cap).
4. **Render:**
   ```bash
   python3 /workspace/inbox-digest/render.py /workspace/inbox-digest/YYYY-MM-DD.json --keep-html
   ```
   Optional `--out-dir DIR` (default `out/`). Outputs `out/digest-YYYY-MM-DD.png`, `.pdf`, and `.html` with `--keep-html`. Uses headless Chrome. It prints `fit: ok` when it fits one page; it shrinks the font and then trims items ("+N more not shown"). Exit 2 means it still overflows: shorten summaries or move items to the roll-up and rerun.
5. **Deliver** as the routine says: post the PNG and PDF in chat; copy the HTML to the user's computer only if approved, to the path the routine names. If emailed, pass attachments as `"$file:<path>.b64"` made with `base64 -w0`, never pasted base64.
6. **Print in color.** The digest is an exception to the black-and-white printing rule.
