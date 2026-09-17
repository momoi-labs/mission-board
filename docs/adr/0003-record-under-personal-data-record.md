---
status: accepted
date: 2026-09-17
supersedes: []
superseded_by: null
tags: [storage, layout]
---

# personal-data separates the person's record from per-job outputs

Skills after `career-record` write their own files: assessed jobs now,
tailored resumes and cover letters later. Mixing them with the record at the
root of `personal-data/` hides which files are the person's inputs and which
are derived from them. The decision: the record (`profile.md`, `experience/`,
`goals/`) lives under `personal-data/record/`, owned by `career-record`, and
every other skill writes to its own folder beside it, starting with `jobs/`
for `job-search`.

> **Append-only:** never edit an accepted ADR. To change this decision, write a
> new ADR and link it to the old one via `supersedes` / `superseded_by`.

## Considered options

- **Flat layout: `profile.md`, `experience/`, `goals/`, `jobs/` at the root.**
  Rejected: fine at four entries, but the line between inputs and outputs
  blurs as skills are added, and moving the record later means migrating a
  larger dataset.
- **`record/` plus one folder per skill output.** Chosen.

## Consequences

- Moving `profile.md` and `experience/` changes the layout that
  `career-record` published. Its `init` action migrates the old layout in
  place, so no one edits paths by hand.
- Skill output folders follow ADR-0002: Markdown with YAML frontmatter and a
  `format` version.
