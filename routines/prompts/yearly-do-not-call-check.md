# Yearly Do Not Call registry check
Requested by Manny via Alfred (Manny's yes in Alfred's chat, Nov 13, 2026: "yes to all three merge steps"). Owner of the result: Ultimate Privacy Scrub (092ee779-d5aa-4635-8541-c70f79cd32d2); Call List Remover was merged into it. Manny's cell was registered Nov 13, 2026.

1. Date guard: schedule fires every Monday in November. Continue only if the year is 2027 or later AND the day of month is 15-21 (`date +%Y`, `date +%d`). Otherwise stop silently.
2. Run `python3 /workspace/common/routine_gate.py --days Mon`. Exit 10: stop silently.
3. Read /workspace/shared-brain/INDEX.md.
4. Ask-first (this check needs the browser and an email confirmation): send Manny one line in the Routines chat: "Yearly Do Not Call check is due: may I verify your cell is still on donotcall.gov? It uses the browser and a confirmation email." Then end the run.
5. When Manny says yes in the Routines chat, Routines does the check: get his cell from the Vault (never write it in chat or files), use donotcall.gov's "Verify your registration" page through a browser helper, read the result (and the confirmation email if the site sends one). Read-only: don't re-register without Manny's yes.
6. Still registered: tell Manny in one line only because he asked; otherwise silent. Not registered or check failed: tell Manny in one line and offer to re-register (needs his yes). Hand the result to Ultimate Privacy Scrub with SendToAgent, ending "No reply needed."
