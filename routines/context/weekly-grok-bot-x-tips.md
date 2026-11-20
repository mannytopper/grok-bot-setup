# Weekly Grok Bot X tips (moved from Dreamer, folder weekly-grok-bot-x-tips, 2026-11-12)

Original enabled: True
Schedule: 0 9 * * 5 (America/New_York), Flexible schedule with a 15-minute window either side.

Context: goals and watch items live in /workspace/dreamer/goals.md (replaces Dreamer's memory). Any 'memory' or 'journal' step means /workspace/dreamer/goals.md or /workspace/dreamer/journal.md. Never touch Usage Guard.

## Prompt for the Routines copy

Moved here from Bot Optomizer on Nov 5, 2026, at Manny's request.

At the start of this run, run python3 /workspace/common/routine_gate.py --days Fri. Exit 10 means skip and send nothing; exit 0 means run. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip). Then read /workspace/shared-brain/INDEX.md and open any file whose topic fits.

Scan X for the past week for practical tips Manny can use with Grok Bot (setup, routines, skills, connectors, usage savings, workflows). Use Grok Bot's public X search and related reads; his X account isn't needed. Prefer concrete how-tos over hype. Put the candidates in a JSON file and drop ones already reported with python3 /workspace/bot-audit/x_tips_dedupe.py check candidates.json (the x-tips-dedupe skill), then run its append command for the tips you report, so /workspace/bot-audit/x-tips-seen.md stays current.

Passive delivery: if you find useful new tips, send Manny a short ranked list in the Routines chat in Grok Bot (each tip: one line, why it helps him, and the post link). If nothing useful is new, stay silent. Message on failure only when he needs to act. Do not create routines, skills, or bots from the tips unless he asks.

## Original prompt (verbatim)

Moved here from Bot Optomizer on Nov 5, 2026, at Manny's request.

At the start of this run, run python3 /workspace/common/routine_gate.py --days Fri. Exit 10 means skip and send nothing; exit 0 means run. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip). Then read /workspace/shared-brain/INDEX.md and open any file whose topic fits.

Scan X for the past week for practical tips Manny can use with Grok Bot (setup, routines, skills, connectors, usage savings, workflows). Use Grok Bot's public X search and related reads; his X account isn't needed. Prefer concrete how-tos over hype. Put the candidates in a JSON file and drop ones already reported with python3 /workspace/bot-audit/x_tips_dedupe.py check candidates.json (the x-tips-dedupe skill), then run its append command for the tips you report, so /workspace/bot-audit/x-tips-seen.md stays current.

Passive delivery: if you find useful new tips, send Manny a short ranked list in this Dreamer chat (each tip: one line, why it helps him, and the post link). If nothing useful is new, stay silent. Message on failure only when he needs to act. Do not create routines, skills, or bots from the tips unless he asks.
