# Work

Work logging system. Inspired by Carmack's .plan files — log what you're doing, why it matters, and what's blocked.

Adapted from [davidhariri/life-system](https://github.com/davidhariri/life-system) for a work context.

---

## Getting Started

### 1. Clone or fork this repo

If you want your own version-controlled copy:

```bash
# Fork on GitHub first, then clone your fork
gh repo fork <original-repo> --clone
```

Or start fresh from this structure without the history:

```bash
gh repo clone <original-repo> my-work-system
cd my-work-system
rm -rf .git
git init && git add . && git commit -m "Initial work system"
gh repo create my-work-system --private --source=. --push
```

### 2. Open in Claude Code

```bash
cd /path/to/your/clone
claude
```

The skills and `CLAUDE.md` are picked up automatically from `.claude/` when Claude Code opens in the repo root.

### 3. Fill in your goals

Edit `journal/YYYY/goals.md` to set your annual work objectives, or open Claude Code in the repo and talk through your goals — Claude can help you think them through and write the file. The `standup` skill uses this file to check alignment every day — it's not useful until it reflects real goals.

### 4. Start your first day

Say **"standup"** to Claude. It will create today's log, walk through setup, and get you going.

---

## Locations

```
inbox.md                          # Quick capture: ideas, tasks, questions
projects/                         # Per-project tracking
journal/YYYY/goals.md             # Annual work objectives
journal/YYYY/MM/YYYY-MM-DD.md     # Daily work log
decisions/                        # Technical and work decision records
people/                           # Colleagues and stakeholders
research/                         # Technical research docs
templates/                        # Templates for all of the above
```

## Conventions

- **Projects** are the primary unit. Tasks and decisions live inside projects.
- **Inbox** is for capture only — process it into projects or decisions regularly.
- **Daily log** is standup-format: what I did, what I'm doing, what's blocked.
- **Wiki-links** connect files: `[[project-name]]`, `[[person-name]]`, `[[decision-name]]`.
  Resolve by searching the relevant directory for `name.md`.
- Log entries go on the project file, not just the daily file. Both get updated.

## Claude Skills

Two skills animate the daily workflow. Invoke them by name in Claude Code (opened from the repo root).

| Skill | Invoke with | What it does |
|---|---|---|
| `standup` | "standup", "start my workday", "let's plan work" | Reviews yesterday's log, sets today's focus, checks alignment with annual goals, flags stale projects |
| `eod` | "eod", "end of day", "wrap up work" | Presents Focus vs. what happened, fills the EOD section, updates project files, captures to inbox |

**Auto-logging:** During any conversation, Claude will append timestamped entries to today's work log and say "Added to work log: [summary]". No need to ask.

**Inbox routing:** Actions and captures from conversations go to `inbox.md`, not the personal life inbox.
