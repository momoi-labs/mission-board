---
status: accepted
date: 2026-09-17
supersedes: ["ADR-0001"]
superseded_by: null
tags: [storage, privacy]
---

# Career data lives in ~/.local/share/mission-board, outside the repo

ADR-0001 put personal data in a gitignored `personal-data/` folder inside the
repository so that every clone had the folder without path configuration. In
practice every git worktree gets its own empty copy, and the editor workflow
creates a worktree per session, so the record diverged across worktrees within
a day. The decision: all personal data lives in
`~/.local/share/mission-board/`, a fixed path with no override, and the
repository holds no personal folder at all.

> **Append-only:** never edit an accepted ADR. To change this decision, write a
> new ADR and link it to the old one via `supersedes` / `superseded_by`.

## Considered options

- **Keep `personal-data/` and symlink it to a shared folder.** Rejected:
  every worktree needs the symlink created by hand, and git sees a symlink
  where it tracks a directory.
- **Path override through an environment variable.** Rejected: a second
  location to check. One person, one fixed path.
- **`~/.mission-board/`.** Rejected: one more dotfolder in the home root.
- **`~/.config/mission-board/`.** Rejected: XDG reserves `~/.config` for
  configuration, and dotfiles repositories often publish it. The record is
  data.
- **`~/.local/share/mission-board/`, the XDG data home, fixed.** Chosen.

## Consequences

- Every session and worktree reads and writes the same record.
- `git clean -x` no longer touches personal data. The folder can become a
  private git repository for history and backup.
- ADR-0003's split between `record/` and per-skill output folders carries
  over unchanged under the new root.
- `career-record` `init` migrates a `personal-data/` folder from either
  earlier layout into the new root and removes it.
