# How every bot uses the shared brain (2026-11-05, Connor, per Manny)

Manny's instruction (Nov 5, 2026): "move everything my bots should know into a shared brain folder; make sure each bot reads that on every task to see if it can apply something from the shared brain."

## At the start of every task
1. Read /workspace/shared-brain/INDEX.md.
2. Open any file whose topic fits the task (for example, rules.md before any send, people-and-accounts.md before writing to someone, lessons.md before an email attachment or Vertafore run).
3. Apply what fits. If the shared brain and your own memory disagree, follow the newer dated entry and tell Manny about the conflict if it matters.

## When you learn something lasting
- Append it to the right file as one line: `- (YYYY-MM-DD, BotName) fact or lesson`.
- Only add things another bot could use: standing rules from Manny, fixes, new scripts, ownership changes.
- Edit in place when a fact changes. Mark the old line "(replaced YYYY-MM-DD)" instead of deleting it silently.
- Keep INDEX.md under about 80 lines. Change its top 10 only when Manny gives a new top-level rule.

## Never store here
Passwords, tokens, API keys, card numbers, one-time codes, home addresses, phone numbers, or login details. Write "in the vault" instead.

## Permissions
The folder is world-readable on the box. Run `chmod -R a+rX /workspace/shared-brain` after editing.
