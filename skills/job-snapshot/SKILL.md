---
name: job-snapshot
description: Render the job search as one shareable HTML page from the job files under ~/.local/share/mission-board/jobs/. Use when the user asks for a snapshot, a status summary, or a recap of the job search to share or to resume later.
---

# Job snapshot

One self-contained HTML page that answers three questions: what is in
progress, who still owes a reply, and what to do next. It is a report, not a
task tracker: no checkboxes, no saved state, nothing to maintain between
runs. The job files are the source; the snapshot never replaces them.

Read `CONTEXT.md` at the repo root, if present, so vocabulary matches the
project's domain language.

## Where snapshots live

```
~/.local/share/mission-board/   # outside the repository, never committed
├── jobs/                       # owned by job-search, read here
└── snapshots/
    └── <YYYY-MM-DD>.html       # one file per day; a rerun overwrites it
```

## Render

1. Read every file in `jobs/` and the goals in `record/goals/` with
   `status: active`. A snapshot with no job files is empty; say so and stop.
2. Group by `status`:
   - **In progress**: `interviewing`, then `applied`.
   - **Waiting for a reply**: `shortlisted` jobs whose last `# Notes` line
     is an outreach (a message, an email, a referral). For each, name the
     contact and count the days since that note's date.
   - **Closed**: `closed`, with the outcome from `# Notes`.
   Other `shortlisted` and `new` jobs go under In progress, last.
3. Derive **Next** from the notes: unanswered outreach older than a week
   gets a follow-up; a referral that names a next person gets a contact
   task; anything the conversation added as pending goes in too. Order by
   what to do first. Every item names the company and what counts as done.
4. Fill [templates/snapshot.html](templates/snapshot.html). The lead is
   two short paragraphs: the state in one sentence, then what changed
   since the previous snapshot in `snapshots/`, if one exists. Each card's
   note is the last dated line of that job's `# Notes`, shortened. Keep
   the listing URL on the card when the job file has one.
5. Write the page in the conversation language, with `<html lang>` set to
   match. Keep the template's colors and layout; add nothing decorative.
6. Write `snapshots/<today>.html`, open it (`open` on macOS, `xdg-open` on
   Linux), and give the person the absolute path.

Done when every job file appears exactly once on the page, every card
shows status, date, and last note, and the Next list has at least one
item per unanswered outreach older than a week.

## Boundaries

- The snapshot reports what the job files say. Missing information is
  shown as missing, never guessed.
- Nothing from the data home is copied into the repository, committed, or
  published.
- The page is meant to be shared; it stays in the data home until the
  person sends it.
