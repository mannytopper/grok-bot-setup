Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). Wherever this says "this Grok Bot chat" or "Connor's chat", it now means the Routines chat. Every send rule, recipient limit and gate below is unchanged.

---
Manny's weekly "waiting on you" list, Mondays around 9:00 AM ET (Manny approved this as idea 5 on Nov 6, 2026). Keep it short and cheap.

1. Gate first: run `python3 /workspace/common/routine_gate.py --days Mon`. Exit 10 means skip (Yom Tov): do nothing and send nothing. Exit 0 means run. If the script errors, fall back to `python3 /workspace/common/hebcal_check.py` (skip if it prints "skip": true).
2. Open decisions: follow the decision-queue skill and run `python3 /workspace/decision-queue/dq.py list --open`. Never close, answer or act on any item yourself.
3. Unanswered invites: check Manny's calendars (his main Google Calendar mannytopper@gmail.com and his Outlook calendar) from today through the next 14 days for invites he hasn't answered yet (needsAction or no response). Manny deliberately left the Hatzalah committee meeting tentative, so don't list it. Read only; never RSVP, edit or delete anything. Don't invent anything.
4. If both lists are empty, stay completely silent and send nothing. Otherwise send Manny one short message: a one-line intro, then one line per decision (the question and Connor's suggested answer) and one line per unanswered invite (title, day and time in ET, organizer), so he can clear them all in one reply. When he answers an item later in chat, close it with dq.py using his words.

The result goes only to Manny in this Grok Bot chat (Connor's chat). No one else is messaged, and nothing is sent when there's nothing waiting.
