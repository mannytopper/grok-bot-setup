# Alfred · Bot Chief Advisor: routine handoff (2026-11-12, Manny approved sending this)
No secrets in this file. Each verbatim saved prompt is in its own file next to this one: alfred-<folder>.prompt.txt

## 1. weekly-company-grok-bot-improvement-review
- Name: Weekly Company & Grok Bot Improvement Review
- Schedule: CRON_TZ=America/New_York 0 10 * * 5 (Fri ~10:00 AM ET). Timing: flexible, earlyMinutes 15, lateMinutes 15.
- State: ENABLED
- Manny exempted it from Alfred's approve-first rule (Nov 9, 2026: "those do NOT need my approval"): it saves, prints, and sends the one-pager without asking.
- Connectors and accounts: none (no email). It reads other bots' transcripts through ReadTranscript (a scheduled run may not be able to; check this).
- Local execution: Manny's laptop WHI-LT-26-03 (machineId cc87a891-f809-4773-a01b-4755b0cc5cc6). It saves the PDF to C:\Users\Manny\Documents\Grok Work\Weekly Summary\ and prints once on the Brother HL-L2420DW (black and white).
- Scripts: /workspace/common/routine_gate.py --days Fri; /workspace/weekly/build.py (approved Oct 23 pilot, output /workspace/weekly-bot-summary-2026-10-23.pdf).
- Skills: Audit, Repair & Govern; Workflow & Automation Decision (these are Alfred's advisor workflows, not separate skill files); route-to-the-right-bot for ownership.
- Memory: closed or dropped follow-ups (Sophia Horowitz voicemail, Hanover SR-12606864, b52.com offer decision, Enhance S3XY support reply, Acura ZDX returned, Pheterson PACE and support@x.ai follow-ups dropped Oct 30); ownership split (usage to Usage Guard, team design to Alfred, skills and lessons to Dreamer); Bot Optomizer is deleted.
- Send permissions: delivers only in Alfred's chat (PDF plus summary). No email.

## 2. grokbot-dashboard-refresh
- Name: Grokbot dashboard refresh
- Schedule: CRON_TZ=America/New_York 50 8 * * 1 (Mon ~8:50 AM ET). Timing: flexible, 15/15.
- State: ENABLED. Also exempted from approve-first (Nov 9).
- The scheduled run only hands off. The real refresh happens in Alfred's main session (ReadTranscript of every bot, then a helper uses EditCanvas). It may not work when moved; Routines would need ReadTranscript plus edit access to canvas 0ba3ca83-b62a-426d-926c-fb5c27231fef.
- Files: /workspace/dash/dashboard.canvas.tsx (source), backups /workspace/dash/dashboard.pre-*.canvas.tsx.
- Scripts: /workspace/common/routine_gate.py --days Mon.
- Connectors, sends, local execution: none. It messages Manny only when the refresh fails or a routine was missed.
- Memory: no usage forecast (Nov 3); chat-history backups OFF (Oct 31); laptop has a "Grokbot dashboard" shortcut.

## 3. monthly-bot-portfolio-strategy-review
- Schedule: CRON_TZ=America/New_York 30 9 1 * * (1st of month ~9:30 AM ET). Timing: flexible, 15/15.
- State: PAUSED (keep paused).
- Connectors, scripts, local execution, sends: none. Skills: Audit, Repair & Govern; Workflow & Automation Decision. Messages only in chat when decisions are needed.

## 4. quarterly-company-ai-operating-model-review
- Schedule: CRON_TZ=America/New_York 0 10 1 1,4,7,10 * (quarterly ~10:00 AM ET). Timing: flexible, 15/15.
- State: PAUSED (keep paused).
- Connectors, scripts, local execution, sends: none. Skills: Grok Bot Organization Discovery & Architecture; Workflow & Automation Decision. Messages only in chat when decisions are needed.

## Shared by all four
- Read /workspace/shared-brain/INDEX.md at the start; passive (silent unless Manny needs to act); no Shabbat or Yom Tov runs; black-and-white printing.
