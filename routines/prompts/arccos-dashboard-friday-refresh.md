# Arccos Dashboard Friday refresh (requested by Manny via Spackler, Nov 20, 2026: "refresh every friday")
1. Run `python3 /workspace/common/shabbat_gate.py`. Exit 10 means Shabbat/Yom Tov: stop silently.
2. If it's past 12:00 PM America/New_York, stop silently.
3. Do exactly one thing: SendToAgent to Spackler - Golf Practice (id a5449afd-2cea-4036-9aed-4842e7919063), priority true:
   "Weekly Arccos refresh: pull the latest Arccos data and update the Arccos Dashboard Page. No reply needed."
4. Send Manny nothing on success. Message him in one line only if the SendToAgent call fails.
Manny's explicit request is his yes for this weekly handoff; no per-run ask. Start no subagent, open no web pages.
