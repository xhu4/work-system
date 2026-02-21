# Work

Work logging system. Inspired by Carmack's .plan files — log what you're doing, why it matters, and what's blocked.

Adapted from [davidhariri/life-system](https://github.com/davidhariri/life-system) for a work context.

---

## Locations

```
~/Documents/Work/inbox.md                          # Quick capture: ideas, tasks, questions
~/Documents/Work/projects/                         # Per-project tracking
~/Documents/Work/journal/YYYY/goals.md             # Annual work objectives
~/Documents/Work/journal/YYYY/MM/YYYY-MM-DD.md     # Daily work log
~/Documents/Work/decisions/                        # Technical and work decision records
~/Documents/Work/people/                           # Colleagues and stakeholders
~/Documents/Work/research/                         # Technical research docs
~/Documents/Work/templates/                        # Templates for all of the above
```

## Conventions

- **Projects** are the primary unit. Tasks and decisions live inside projects.
- **Inbox** is for capture only — process it into projects or decisions regularly.
- **Daily log** is standup-format: what I did, what I'm doing, what's blocked.
- **Wiki-links** connect files: `[[project-name]]`, `[[person-name]]`, `[[decision-name]]`.
  Resolve by searching the relevant directory for `name.md`.
- Log entries go on the project file, not just the daily file. Both get updated.
