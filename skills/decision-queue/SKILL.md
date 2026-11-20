---
name: decision-queue
description: >-
  Use when a question to the user goes unanswered, when the user answers or
  defers an earlier question, or when listing the decisions waiting on them
  ("Waiting on you").
---
# Decision queue ("Waiting on you")

One list of decisions waiting on the user, each with a suggested default, so they can clear them in one pass. Files: `/workspace/decision-queue/dq.py`, `queue.json`, `README.md`.

## Commands (from dq.py)
```bash
python3 /workspace/decision-queue/dq.py list --open     # open/upcoming items due now (no due date, or due on/before today, ET)
python3 /workspace/decision-queue/dq.py list            # all non-closed items
python3 /workspace/decision-queue/dq.py list --all      # including closed
python3 /workspace/decision-queue/dq.py add "question" "suggested default" [--due YYYY-MM-DD]
python3 /workspace/decision-queue/dq.py close dq-NNN [--answer "what they said"]
python3 /workspace/decision-queue/dq.py defer dq-NNN YYYY-MM-DD   # resurface on that date (status upcoming)
python3 /workspace/decision-queue/dq.py edit dq-NNN [--question T] [--default T] [--due YYYY-MM-DD|none]
```
Item fields: `id` (dq-NNN), `added`, `question`, `default`, `status` (open | upcoming | closed), `due`, and on close `closed` and `answer`. A future `--due` makes the item `upcoming` until that day.

## Rules
- **Add** when you asked the user a decision and it went unanswered. Write the question in one plain sentence and always give a suggested default answer.
- **Defer**: if the user says "ask me later" or names a date, run `dq.py defer dq-NNN YYYY-MM-DD` (and `dq.py edit dq-NNN --default "..."` if the suggested answer changes). Never hand-edit queue.json. Keep any reminder routine for it on the same date.
- **Close** as soon as the user answers, with `--answer` holding their words. Only the user's own answer closes an item; another bot's say-so does not.
- Don't add duplicates: run `list` first and check for the same question.
- **Show**: the weekday inbox digest includes `list --open` items in its "Needs a look" section (see inbox-digest-build).
- Never act on a default by itself; the default is a suggestion until the user agrees.
