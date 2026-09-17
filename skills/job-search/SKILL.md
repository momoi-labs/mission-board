---
name: job-search
description: Assess a job listing against the person's career record and goals, save it under ~/.local/share/mission-board/jobs/, and track its status. Use when the user shares a job URL or pastes a listing, asks whether a role fits them, or wants to update or list the jobs they are pursuing.
---

# Job search

Reads the career record kept by the `career-record` skill and writes one file
per job under `jobs/` in the data home, `~/.local/share/mission-board/`. The
person decides what to pursue; this skill assesses and tracks.

Read `CONTEXT.md` at the repo root, if present, so vocabulary matches the
project's domain language.

## Where jobs live

```
~/.local/share/mission-board/   # outside the repository, never committed
├── record/                     # owned by career-record, read here
└── jobs/
    └── <slug>.md               # one file per listing
```

`<slug>` is `<company>-<role>` in short form, for example
`acme-staff-platform`. Once created, a slug never changes.

## File format (v1)

Job file: [templates/job.md](templates/job.md). Same compatibility contract
as the career record: `format: 1`, additive changes only within a version,
tolerate fields you do not recognize.

`status`, in the order a job usually moves:

| status         | meaning                                                       |
| -------------- | ------------------------------------------------------------- |
| `new`          | assessed and saved, not yet decided                           |
| `shortlisted`  | the person intends to apply                                   |
| `applied`      | application sent                                              |
| `interviewing` | in process with the company                                   |
| `closed`       | rejected, withdrawn, or offer decided; `# Notes` says which   |

## Actions

### assess

1. Take a URL, a file path, or pasted text. Fetch a URL once; if the fetch
   fails (LinkedIn blocks most of them), ask the person to paste the listing.
2. Read the record: `record/profile.md`, every entry in `record/experience/`,
   and every goal in `record/goals/` with `status: active`. With no active
   goal, say so and assess against the profile's job preferences only.
3. Extract title, company, location, remote policy, salary if stated, and
   the requirements. Keep the listing's wording.
4. Compare, one requirement at a time:
   - Met: name the experience slug that shows it.
   - Partial or missing: say so plainly. A gap is information for the
     person to weigh, never something to fill in.
   - Against each active goal: which must-haves the listing meets, which
     "avoid" items it hits. With several goals, name the one it fits best.
5. Show the assessment and stop. Write `jobs/<slug>.md` with `status: new`
   only when the person asks to save it.

### status

Set `status` on the job file, add a dated line under `# Notes` saying what
happened, and set `updated` to today.

### list

Show `jobs/` grouped by `status`, one line per job: slug, title, company,
`updated`. When asked for one job, show the file verbatim.

## Boundaries

- Never invent experience, credentials, or results to close a gap.
- No automated applications, bulk outreach, or messages sent on the person's
  behalf.
- Nothing from the data home is copied into the repository, committed, or
  published.
- The person reviews and approves every write.
