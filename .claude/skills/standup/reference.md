# Standup Skill Reference

## File Locations

```
inbox.md                          # Quick capture
projects/                         # Per-project tracking (*.md files)
journal/YYYY/goals.md             # Annual work objectives
journal/YYYY/MM/YYYY-MM-DD.md     # Daily work log
journal/YYYY/MM/week-WW.md        # Weekly reviews (optional)
decisions/                        # Technical/work decision records
people/                           # Colleagues and stakeholders
research/                         # Technical research docs
templates/                        # Templates
```

## Task Management

- **Quick capture:** `./inbox.md` — process into projects or decisions regularly, don't let it accumulate
- **Project tasks:** in the project file's Tasks section (`projects/name.md`)
- **Daily focus:** Focus section of the daily work log
- **Tasks live in both places** — when a project task is worked, update both the project file and the daily log

## Active Project Detection

A project is "active" when its file contains `Status: Active` in the frontmatter block. Check with Grep rather than reading every file:

```bash
grep -l "Status: Active" ./projects/*.md
```

## Optional: Calendar Integration (macOS)

Install `icalBuddy` to pull today's calendar events into standup:

```bash
brew install ical-buddy
```

Pull work calendar events for today:
```bash
icalBuddy -nc -nrd -eep "notes,location,url,attendees" -tf "%H:%M" -df "" -ic "Work" eventsToday
```

Useful for surfacing meetings that should appear in the day's Log.
