---
status: accepted
date: 2026-09-17
supersedes: []
superseded_by: null
tags: [storage, privacy]
---

# Career data lives in a gitignored personal-data folder inside the repo

Career records are personal, but keeping them in a separate location splits
the assistant's inputs from its skills and needs path configuration. The
decision: personal data lives in `personal-data/` at the repository root,
gitignored except for a tracked `.gitkeep`, so every clone has the folder and
no personal content is ever tracked or published.

> **Append-only:** never edit an accepted ADR. To change this decision, write a
> new ADR and link it to the old one via `supersedes` / `superseded_by`.

## Considered options

- **Folder outside the repo (`~/.mission-board/`).** Rejected: needs an env
  var or path convention, and splits data from skills.
- **Sibling private repository.** Rejected for now: extra setup before the
  first skill is useful. Remains the fallback if the risks below start to
  hurt, because it also gives version history for the record.

## Consequences

- `git clean -x` deletes the folder. The person is responsible for backups.
- Every git worktree has its own `personal-data/`; records do not follow
  worktrees. Sessions that run in worktrees must not assume the main record
  is present.
