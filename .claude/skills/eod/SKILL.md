---
name: eod
description: "End-of-day work wrap-up. Use when user says 'eod', 'end of day', 'wrap up work', or 'workday done'. Fills today's EOD section, updates project files, captures tomorrow's items."
user-invocable: true
allowed-tools: Read, Edit, Write, Glob, Grep, AskUserQuestion
---

# EOD — End-of-Day Work Wrap-Up

Close the day with an honest accounting. Don't let "shipped a lot" hide that the one thing that mattered didn't move.

**Tone:** Honest, brief, no-nonsense. This should take 5 minutes, not 30.

---

## Step 1: Load Today's Work Log

Read `./journal/YYYY/MM/YYYY-MM-DD.md` (today's date).

If it doesn't exist, note it and create a stub — today happened even if it wasn't logged.

---

## Step 2: Present the Delta

Show side by side:

- **Planned (Focus section):** what was set as today's focus items
- **What happened (Log section):** what's actually recorded

Be direct about the gap. Don't editorialize — just present it clearly so the user can see it.

---

## Step 3: Ask What's Worth Capturing

Use AskUserQuestion: "What's worth capturing from today? What shipped, what's stuck, what's carrying over to tomorrow?"

Let them talk. Don't interrupt with structure yet. If something sounds like a blocker or a decision point, note it.

---

## Step 4: Fill the EOD Section

Update today's work log EOD section based on the conversation:

```markdown
## EOD

### Shipped / Advanced
- [specific thing completed or meaningfully moved forward]

### Blocked
- [what's stuck and why, if known]

### Tomorrow
- [ ] [specific carry-over or next action]
```

Rules:
- "Shipped / Advanced" means real progress — not "worked on it"
- Blocked should name the blocker, not just the task
- Tomorrow items should be specific enough to act on without re-reading context
- Keep the user's language — don't sanitize it

Mark completed Focus items as `[x]`. Leave uncompleted ones as `[ ]`.

---

## Step 5: Update Project Files

For any project mentioned during today's conversation or in the log entries:

1. Read the project file at `./projects/[project-name].md`
2. Append today's progress to the project's Log section:
   ```markdown
   ### YYYY-MM-DD
   - [what happened, what changed, what you learned]
   ```
3. Update the Tasks section if items moved from In Progress to Done

Only update projects that were actually touched today — don't create empty log entries.

---

## Step 6: Capture to Inbox

If anything came up during the conversation that isn't assigned to today or a specific project — ideas, follow-ups, questions, things to investigate — add them to `./inbox.md` under the appropriate section (Ideas, Tasks, or Questions).

---

## Step 7: Friday Check

If today is Friday (or if explicitly requested), prompt:

"It's the end of the week — want a quick weekly summary? I can look at what shipped vs. what was planned and flag anything to carry into next week."

If yes: read Monday–Friday work logs, summarize what moved, what didn't, and suggest 1–3 priorities for next week.
