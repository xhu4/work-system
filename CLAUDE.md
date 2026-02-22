# Work Repo — Claude Instructions

This supplements the global `~/.claude/CLAUDE.md`. Only work-specific overrides are here — global rules still apply.

---

## Co-Thinking Mode (Work Override)

The global co-thinking rules apply, with these work-specific adjustments:

- **Auto-log goes here:** `./journal/YYYY/MM/YYYY-MM-DD.md` — not the life journal
- **When working on a specific project:** also update that project file's Log section with today's progress
- **Actions from conversations** go in `./inbox.md` — not `~/Documents/Xiukun/inbox.md`
- **At end of a work session:** prompt to record to today's work log and/or the relevant project file

---

## File Locations

```
inbox.md                          # Quick capture
projects/                         # Per-project tracking
journal/YYYY/goals.md             # Annual work objectives
journal/YYYY/MM/YYYY-MM-DD.md     # Daily work log
decisions/                        # Technical/work decision records
people/                           # Colleagues and stakeholders
research/                         # Technical research docs
templates/                        # Templates
```

---

## Wiki-Links

Resolve `[[name]]` by searching these directories in order: `people/`, `projects/`, `decisions/`, `research/`, `journal/`. Use Glob to find `name.md`.

When working, add wiki-links to connect related content:
- Work logs link to projects and people: `Working on [[docker-base-image]] with [[alice]]`
- Decision docs link to projects and research: `See [[infra-migration]]`
- Project files link to people and decisions: `Owner: [[alice]], see [[auth-decision]]`

---

## Project Conventions

- When a project is mentioned in conversation, read its project file first before suggesting changes
- Tasks live on **project files** (`projects/name.md`) AND the daily log — update both when something moves
- Inbox is capture only — don't let it accumulate for more than a few days without processing into projects or decisions
- A project is "active" when its file contains `Status: Active` in the frontmatter
