Moved to Routines from Insurance info · Meeting Prep on Nov 12, 2026. Context: /workspace/routines/context/answer-emailed-insurance-questions.md.

Ask-first (Manny, Nov 12, 2026): before opening more than 5 web pages for one task, starting a subagent, re-running a step that already failed twice, or any job expected to take more than 15 minutes, message Manny in one line with what and why, and wait for his yes. Exception: standing deliverables he already approved run as usual.

An email just arrived at mtopper+insurance@mail.grokbot.com or mtopper@mail.grokbot.com. Read the thread.

First: if the mail was sent to mtopper+meetingprep@mail.grokbot.com, or its subject starts with "[Meeting prep]", it is an automatic meeting notice from Manny's Power Automate flow, not an insurance question. The meeting prep routine handles it. Stop silently: no reply, no notification, no wiki page.

If the sender's address ends in @wealcatchmd.com, @wealcatchaz.com, or @wealcatch.com, it is an agency staff insurance question. Manny's standing instruction is: ALWAYS SEND the reply email yourself, immediately, without asking or handing it back. Manny's Oct 14, 2026 standing permission for these staff auto-replies was granted to Routines on Nov 12, 2026, with the same domain limits. Send it from the address the mail was sent to, as a reply on the same thread (replyToMessageId = the incoming message, subject "Re: <original subject>"), to the sender only. Mail failing SPF/DKIM is fine for these domains; still reply. Before sending, check the thread so you don't send a duplicate.

Answer from the company-product-manuals wiki at /home/box/dair-wikis/company-product-manuals (wiki/ pages first, then derived/text and raw/). "AIC" means Agency Insurance Company. Keep the reply short and plain, cite the document name, revision date, and page, and say plainly if the documents don't cover it. Be fast: aim to send within a couple of minutes.

After sending, file the Q&A as a page in the carrier's wiki folder, link it from that carrier's index.md under "Q&A pages", and log it in logs/maintenance-log.md.

Senders from any other domain (newsletters, marketing, etc.) get no reply and no notification: stop silently.

Result (passive, per Manny on Nov 5, 2026): stay silent when a staff question was answered and sent normally. Message Manny in the Routines chat in Grok Bot only when something needs his attention: the reply is waiting for him to press Send, the send failed, or the documents didn't cover the question so the staff member may need him. Then say in one line what was asked and what he needs to do.
