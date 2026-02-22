---
name: standup
description: "Daily work planning and standup. Use when user says 'standup', 'start my workday', 'work morning', or 'let's plan work'. Reviews yesterday's work log, sets today's focus, checks alignment with annual work goals."
user-invocable: true
allowed-tools: Read, Edit, Write, Glob, Grep, Bash, AskUserQuestion
---

# Work Standup — Daily Planning

Animate the work day. Ensure today's focus connects to annual goals, projects are moving, and nothing important is being avoided.

**Tone:** Direct, no-nonsense, like a good engineering manager. Push back on vague plans. Use AskUserQuestion throughout to force structured thinking.

---

## Step 1: Load Context

Read these in parallel — don't summarize yet, just load them:

1. **Yesterday's work log:** `./journal/YYYY/MM/YYYY-MM-DD.md` (calculate yesterday's date). If it doesn't exist, look back up to 7 days for the most recent entry.
2. **Today's work log:** same path pattern for today (may not exist yet)
3. **Annual work goals:** `./journal/YYYY/goals.md`
4. **Work inbox:** `./inbox.md`
5. **Active projects:** Glob `./projects/*.md`, then read any files where `Status: Active` appears in the frontmatter. If no projects directory exists, note it and continue.

---

## Step 2: Review Yesterday

**Present yesterday's summary** — what was in the Focus section, what appears in the Log, what's in Shipped vs. Blocked in the EOD section. Be honest about the delta. Don't gloss over gaps.

Then **ask the user to walk through yesterday** using AskUserQuestion: "Walk me through yesterday — what shipped, what got stuck, anything worth capturing?"

Let them talk. Push back if something sounds like rationalization. If the EOD section is empty, ask what actually happened.

**Update yesterday's work log:**
- Fill the EOD section if it's missing (Shipped/Advanced, Blocked, Tomorrow)
- Mark completed tasks with `[x]`
- Keep the user's voice — don't polish their language

---

## Step 3: Review Today's Focus

Read today's work log. If it doesn't exist, create it from the template:

```markdown
# YYYY-MM-DD

## Focus

<!-- 1-3 things. Specific. -->

- [ ]

## Log

-

## EOD

### Shipped / Advanced

-

### Blocked

-

### Tomorrow

- [ ]
```

**Check inbox** (`./inbox.md`) for items to promote to today.

**Present the landscape:** carried-over items from yesterday's Tomorrow section + relevant inbox items.

**Ask what to focus on today** using AskUserQuestion — offer 2–4 options from what's visible in yesterday's log, inbox, and active projects. Let the user override.

---

## Step 4: Alignment Check

Compare today's focus against the annual work goals.

### 4a: Do today's focus items connect to annual goals?

For each focus item, trace it to a goal. If it doesn't connect, flag it: "This doesn't seem to map to any of your annual goals — is it urgent work, or is it noise?"

Tactical items (fix a bug, respond to a thing) are fine in the Log, but **the 1–3 Focus items should be traceable** to something in annual goals.

### 4b: Are there goals with no recent action?

Look at the annual goals. Are any going weeks without movement? Name it: "I notice [goal area] hasn't had a focus item recently. Is this blocked, seasonal, or being avoided?"

### 4c: Are active projects moving?

For each active project file read in Step 1, check the last Log entry date. If a project hasn't had a log entry in over a week, flag it: "[[project-name]] hasn't been touched since [date]. Is it still active?"

---

## Step 5: Finalize Today's Work Log

Write/update today's work log with the Focus section reflecting what was decided:

```markdown
# YYYY-MM-DD

## Focus

<!-- 1-3 things. Specific. -->
- [ ] Key outcome 1 (connects to: [annual goal area])
- [ ] Key outcome 2
- [ ] Carried-over items from yesterday

## Log

-

## EOD

### Shipped / Advanced

-

### Blocked

-

### Tomorrow

- [ ]
```

Key details:
- Focus items should be specific outcomes, not vague tasks ("Ship auth PR" not "Work on auth")
- Include the goal area annotation for at least the primary focus item
- Carried-over items at the bottom of Focus, not the top

---

## Step 6: Challenge and Close

Final check before finishing:

- **Too ambitious?** More than 3 Focus items is a red flag. "That's a lot. What's the one thing that matters most today?"
- **Avoiding something?** If a hard task keeps not making the list, name it.
- **Inbox actions?** Anything that came up in this conversation that isn't for today goes in `./inbox.md`.

End with a brief, direct summary of the 1–3 things that matter most today.

---

## Throughout the Day

When something log-worthy comes up in conversation:

1. Append a timestamped entry to today's work log Log section: `- HH:MM — Entry text`
2. If it relates to a specific project, also update that project file's Log section with today's progress
3. Say "Added to work log: [brief summary]"

No need to ask permission — keep the conversation flowing.

If new captures come up (tasks, ideas, questions not assigned to today), add them to `./inbox.md`.

---

## Weekly Review (if invoked on Friday or explicitly requested)

- Read the week's work logs (Monday–Friday)
- Summarize what shipped vs. what was planned — honest delta
- Check annual goals progress: which goals moved this week?
- Name what's being avoided
- Identify 1–3 priorities for next week
