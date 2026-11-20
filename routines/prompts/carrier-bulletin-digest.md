# Carrier bulletin and rate-change digest (Manny picked this Nov 20, 2026, from the weekly routine ideas, #4)
Runs Tuesdays around 10:00 AM ET.
1. `python3 /workspace/common/routine_gate.py --days Tue`. Exit 10 means stop silently.
2. State file /workspace/routines/context/carrier-bulletin-state.json: {"last_checked": ISO time, "seen_ids": [...]}. If missing, use the last 7 days and create it.
3. With the Outlook connector (work mail, manny@wealcatchmd.com), search mail received since last_checked for carrier bulletins, agent notices, and rate, rule, underwriting-guideline, form, or appetite change announcements (Allstate, Chubb, Selective, and any other insurance carrier or MGA). Skip marketing, webinars, individual policy notices, and anything in seen_ids.
4. For each real change that affects personal-lines quoting, write one line: carrier, state/line, what changes, effective date, and a link to the email (webLink) if available. Read attachments only when the email body has no summary.
5. If at least one item: send Manny one message here titled "Carrier changes this week" with the lines, grouped by carrier. If none, stay silent.
6. Update last_checked and seen_ids. Read only: never reply, forward, move, or delete mail; never touch Y:\Company Forms_Rates; start no subagent; open at most 5 web pages.
