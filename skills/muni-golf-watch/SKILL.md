---
name: muni-golf-watch
description: >-
  Use when checking whether the Muni Golf iPad app is publicly released (App
  Store search plus munigolfsim.com), including a watch routine.
---
# Muni Golf iPad watch (no AI)

```bash
python3 /workspace/muni-golf/check.py
python3 /workspace/muni-golf/check.py --commit
python3 /workspace/muni-golf/check.py --fixture page.html --itunes-fixture itunes.json
```

- JSON: `released`, `itunes_hits`, `site`, `alert`, `alert_new`, `previously_seen`.
- Ignores Mini Golf lookalikes. `--commit` updates `state.json` only.
- Never messages, buys, or posts. The caller messages only when `alert_new` is true.

## Test
`python3 /workspace/muni-golf/check.py --selftest`
