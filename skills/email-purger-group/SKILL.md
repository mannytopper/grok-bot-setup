---
name: email-purger-group
description: >-
  Use when building an inbox cleanout proposal from a fetched message list JSON:
  group by sender domain, apply safe default actions, and exclude starred,
  important and preserved senders. Proposal only, never modifies mail.
---
# Email cleanout grouper (no AI)

```bash
python3 /workspace/email-purger/scripts/group_messages.py messages.json [--rules rules.json] [--out proposal.json]
```

- Input: `{messages:[...]}` or a bare list with `id`, `from`, `subject`, `labelIds`.
- Output proposal: `groups`, `excluded`, `totals`, `nothingChanged: true`, `awaitingApproval: true`.
- High-volume promotions (20 or more) default to `unsubscribe_then_archive`; forums default to `ask`.
- Does not verify List-Unsubscribe, send, delete, archive, or unsubscribe. Every action still needs the user's yes.

## Test
`python3 /workspace/email-purger/scripts/group_messages.py --selftest`
