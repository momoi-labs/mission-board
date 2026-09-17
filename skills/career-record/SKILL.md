---
name: career-record
description: Maintain the person's career record as plain Markdown files in personal-data/. Use when the user wants to set up or update their profile, import experience from a LinkedIn URL or a resume PDF, or record and review work experience.
---

# Career record

The career record is the source material for every other skill in this repo:
job search, resume tailoring, cover letters. It is personal data; the skills
are reusable. Keep that split: skills and templates stay in the repo, record
contents stay in `personal-data/`.

Read `CONTEXT.md` at the repo root, if present, so vocabulary matches the
project's domain language.

## Where the record lives

```
personal-data/            # gitignored, never committed except .gitkeep
├── .gitkeep
├── profile.md
└── experience/
    └── <slug>.md
```

`<slug>` is a short, stable identifier for one role or project, for example
`acme-backend-2023`. Once created, a slug never changes.

## File formats (v1)

Both formats are compatibility contracts. Every file declares `format: 1` in
its frontmatter. Additive changes (new optional fields) stay in version 1;
removing, renaming, or retyping a field requires version 2, and version 2
readers must still read version 1. Tolerate frontmatter fields you do not
recognize.

- Profile: [templates/profile.md](templates/profile.md)
- Experience entry: [templates/experience.md](templates/experience.md)

## Actions

### init

1. Ensure `personal-data/` exists with its `.gitkeep`, and that `.gitignore`
   ignores the contents but not the `.gitkeep`.
2. Create `profile.md` from the template if missing.
3. Create `experience/` if missing.

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
   written to `personal-data/` before confirmation.
5. Write confirmed entries as files under `experience/`, and merge extracted
   skills and preferences into `profile.md`.

### Update

- Profile: edit `profile.md`, keep existing frontmatter fields intact, set
  `updated` to today.
- Experience: edit the entry file, or add a new one for a new role or
  project. One concern per file. Respect the person's wording; suggest
  improvements, do not apply them unasked.

### Read

Other skills consume the record: `profile.md` plus every file in
`experience/`. When asked for the record, show the files verbatim instead of
paraphrasing.

## Boundaries

- Never invent experience, credentials, or results to fill gaps.
- Nothing inside `personal-data/` is committed, tracked, or published, except
  `.gitkeep`.
- The person reviews and approves every write.
