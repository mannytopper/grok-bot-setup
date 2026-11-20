---
name: x-tips-dedupe
description: >-
  Use when a weekly X-tips routine has candidate post URLs and must drop ones
  already in the seen log before messaging, or append newly reported ones.
---
# X tips dedupe (no AI)

```bash
python3 /workspace/bot-audit/x_tips_dedupe.py check candidates.json
python3 /workspace/bot-audit/x_tips_dedupe.py append candidates.json
```

- Candidates: a list of URLs or `{url, id?, title?}` objects.
- Seen log defaults to `/workspace/bot-audit/x-tips-seen.md` (override with `X_TIPS_SEEN`).
- Normalizes twitter.com to x.com and matches status ids.
- Never posts to X. `append` writes only new lines.

## Test
`python3 /workspace/bot-audit/x_tips_dedupe.py --selftest`
