# Weekly bot scorecard (moved from Dreamer, folder weekly-bot-scorecard, 2026-11-12)

Original enabled: True
Schedule: 45 9 * * 5 (America/New_York), Flexible schedule with a 15-minute window either side.

Context: goals and watch items live in /workspace/dreamer/goals.md (replaces Dreamer's memory). Any 'memory' or 'journal' step means /workspace/dreamer/goals.md or /workspace/dreamer/journal.md. Never touch Usage Guard.

## Prompt for the Routines copy

Moved here from Bot Optomizer on Nov 5, 2026, at Manny's request.

At the start of this run, run python3 /workspace/common/routine_gate.py --days Fri. Exit 10 means skip and send nothing; exit 0 means run. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip). Then read /workspace/shared-brain/INDEX.md and open bots.md, routines.md, skills.md, lessons.md, and decisions.md. Apply anything relevant.

Score each of Manny's current Grok Bots out of 10 for how well it is doing its job this week. Use usage, routine health, recent chat work, shared-brain ownership, and whether it followed passive/Shabbat rules. For each bot: score /10, one concrete miss, and one suggested fix. Rank or list every active bot. Change nothing: do not create, edit, pause, or delete routines, skills, bots, or files that alter behavior. Do not tell other bots to change anything.

This weekly scorecard is a standing report he asked for, so always send it to Manny in the Routines chat in Grok Bot. Outside that report, stay silent unless something failed.

## Original prompt (verbatim)

Moved here from Bot Optomizer on Nov 5, 2026, at Manny's request.

At the start of this run, run python3 /workspace/common/routine_gate.py --days Fri. Exit 10 means skip and send nothing; exit 0 means run. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip). Then read /workspace/shared-brain/INDEX.md and open bots.md, routines.md, skills.md, lessons.md, and decisions.md. Apply anything relevant.

Score each of Manny's current Grok Bots out of 10 for how well it is doing its job this week. Use usage, routine health, recent chat work, shared-brain ownership, and whether it followed passive/Shabbat rules. For each bot: score /10, one concrete miss, and one suggested fix. Rank or list every active bot. Change nothing: do not create, edit, pause, or delete routines, skills, bots, or files that alter behavior. Do not tell other bots to change anything.

This weekly scorecard is a standing report he asked for, so always send it to Manny in this Dreamer chat. Outside that report, stay silent unless something failed.
