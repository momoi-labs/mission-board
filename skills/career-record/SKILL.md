---
name: career-record
description: Maintain the person's career record as plain Markdown files in ~/.local/share/mission-board/record/. Use when the user wants to set up or update their profile, import experience from a LinkedIn URL or a resume PDF, record and review work experience, or define and revise career goals.
---

# Career record

The career record is the source material for every other skill in this repo:
job search, resume tailoring, cover letters. It is personal data; the skills
are reusable. Keep that split: skills and templates stay in the repo, record
contents stay in `~/.local/share/mission-board/`, called the data home below.

Read `CONTEXT.md` at the repo root, if present, so vocabulary matches the
project's domain language.

## Where the record lives

```
~/.local/share/mission-board/   # outside the repository, never committed
└── record/                     # the person's inputs; skills write beside it
    ├── profile.md
    ├── experience/
    │   └── <slug>.md
    └── goals/
        └── <slug>.md
```

Paths below are relative to `record/` in the data home.

`<slug>` is a short, stable identifier: one role or project in `experience/`
(for example `acme-backend-2023`), one direction in `goals/` (for example
`staff-platform-remote`). Once created, a slug never changes.

## File formats (v1)

All formats are compatibility contracts. Every file declares `format: 1` in
its frontmatter. Additive changes (new optional fields) stay in version 1;
removing, renaming, or retyping a field requires version 2, and version 2
readers must still read version 1. Tolerate frontmatter fields you do not
recognize.

- Profile: [templates/profile.md](templates/profile.md). Its "Job
  preferences" section holds the hard filters: roles, locations, remote
  policy, salary range.
- Experience entry: [templates/experience.md](templates/experience.md)
- Goal: [templates/goal.md](templates/goal.md). One direction the person is
  pursuing: where they want to go, what a role must have, what they avoid,
  which companies or industries they target. Several goals can be active at
  once; a person exploring two paths keeps two files.

## Actions

### init

1. If the repository has a `personal-data/` folder holding a record (either
   `profile.md` at its root or under `record/`), move the record into
   `record/` in the data home and delete `personal-data/`.
2. Create `record/` with `experience/` and `goals/` if missing.
3. Create `profile.md` from the template if missing.

### Import from LinkedIn URL or resume PDF

Bootstrap the record from material the person already has.

1. Ask for a LinkedIn profile URL, a PDF or other file path, or pasted text.
   LinkedIn blocks most automated fetching: try once, and if it fails ask the
   person to paste the profile text or export it as PDF.
2. Extract roles, companies, dates, skills, and job preferences. Record where
   each entry came from in its `source` frontmatter field.
3. Summarize what you understood, entry by entry, in the person's language.
   Mark anything uncertain as an explicit question rather than filling it in.
   Never invent or embellish experience, credentials, or results.
4. Stop. Let the person expand, correct, and confirm each entry. Nothing is
   written to the record before confirmation.
5. Write confirmed entries as files under `experience/`, and merge extracted
   skills and preferences into `profile.md`.

### Set goals

1. Ask what the person wants next: the direction for the next one to three
   years, what a role must have, what would be nice, what they avoid, and
   which companies or industries they target. One goal per distinct
   direction.
2. Draft the goal in the person's words and show it. Where they were vague,
   ask instead of guessing.
3. Write `goals/<slug>.md` after the person confirms.

### Update

- Profile: edit `profile.md`, keep existing frontmatter fields intact, set
  `updated` to today.
- Experience: edit the entry file, or add a new one for a new role or
  project. One concern per file. Respect the person's wording; suggest
  improvements, do not apply them unasked.
- Goals: edit the goal file, set `updated` to today. When a goal no longer
  applies, set `status` to `paused` or `done` instead of deleting the file:
  past goals explain past applications.

### Read

Other skills consume the record: `profile.md`, every file in `experience/`,
and the goals in `goals/` with `status: active` unless asked for all of them.
When asked for the record, show the files verbatim instead of paraphrasing.

## Boundaries

- Never invent experience, credentials, or results to fill gaps.
- Nothing from the data home is copied into the repository, committed, or
  published.
- The person reviews and approves every write.
