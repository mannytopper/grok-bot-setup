# Weekly Grok Bot marketplace template check (moved from Dreamer, folder weekly-grok-bot-marketplace-template-check, 2026-11-12)

Original enabled: True
Schedule: 0 11 * * 5 (America/New_York), Flexible schedule with a 15-minute window either side.

Context: goals and watch items live in /workspace/dreamer/goals.md (replaces Dreamer's memory). Any 'memory' or 'journal' step means /workspace/dreamer/goals.md or /workspace/dreamer/journal.md. Never touch Usage Guard.

## Prompt for the Routines copy

Weekly check of the Grok Bot marketplace for bot templates that would genuinely help Manny. (He asked Connor for this on Nov 5, 2026 and wanted it to run on Dreamer.)

1. Run python3 /workspace/common/routine_gate.py --days Fri. If it exits 10 (skip), do nothing and send nothing. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip).
2. Read /workspace/shared-brain/INDEX.md and bots.md, and the existing shared skills in /home/box/agent-data/workflows, so you know which bots and skills already exist.
3. Review the marketplace (https://x.ai/bot/marketplace and the bot template search) for templates that fit Manny's life: owner of the Wealcatch insurance agency and its office operations, family and home, domains, his Tesla, golf, and his book "Stay Connected".
4. Skip any template that duplicates or overlaps an existing bot or skill, and any template already listed in /workspace/marketplace-watch/recommended.json (recommended, skipped as overlap, or declined). Add each new recommendation (name, share id, date) and each new overlap skip to that file, then run chmod -R a+rX /workspace/marketplace-watch.
5. Never add, install, or create a bot. Only recommend.

Keep the run cheap: a quick scan, and stop once you've checked the new listings.

Passive: message Manny in the Routines chat in Grok Bot only when there is at least one new template that genuinely fits him. Give each one as its bot template link with one line on why it fits. If nothing new fits, send nothing at all.

## Original prompt (verbatim)

Weekly check of the Grok Bot marketplace for bot templates that would genuinely help Manny. (He asked Connor for this on Nov 5, 2026 and wanted it to run on Dreamer.)

1. Run python3 /workspace/common/routine_gate.py --days Fri. If it exits 10 (skip), do nothing and send nothing. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip).
2. Read /workspace/shared-brain/INDEX.md and bots.md, and the existing shared skills in /home/box/agent-data/workflows, so you know which bots and skills already exist.
3. Review the marketplace (https://x.ai/bot/marketplace and the bot template search) for templates that fit Manny's life: owner of the Wealcatch insurance agency and its office operations, family and home, domains, his Tesla, golf, and his book "Stay Connected".
4. Skip any template that duplicates or overlaps an existing bot or skill, and any template already listed in /workspace/marketplace-watch/recommended.json (recommended, skipped as overlap, or declined). Add each new recommendation (name, share id, date) and each new overlap skip to that file, then run chmod -R a+rX /workspace/marketplace-watch.
5. Never add, install, or create a bot. Only recommend.

Keep the run cheap: a quick scan, and stop once you've checked the new listings.

Passive: message Manny in this chat only when there is at least one new template that genuinely fits him. Give each one as its bot template link with one line on why it fits. If nothing new fits, send nothing at all.
