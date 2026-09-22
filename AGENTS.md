# Mission board

Read `README.md` for the project scope and boundaries before changing behavior.
Read `docs/PRINCIPLES.md` when choosing an implementation approach.
Personal career data lives in `~/.local/share/mission-board/`, outside the
repository: never copy it into the repo, commit, or publish its contents.

## Skills

Skills live in `skills/` and `.agents/skills/`. Each skill defines its formats
and boundaries in its `SKILL.md`; read it before changing that skill's behavior.

## Agent skills

### Ideal work

When helping someone discover how they want to work, define their next career
objectives, or describe their ideal role, use
[ideal-work](.agents/skills/ideal-work/SKILL.md).

### Issue tracker

Issues and specs live in GitHub Issues. See `docs/agents/issue-tracker.md`
when creating, reading, or updating tickets.

### Triage labels

Use the default triage labels. See `docs/agents/triage-labels.md` when triaging issues.

### Domain docs

This is a single-context repository. Read `docs/agents/domain.md` before
exploring domain concepts or decisions.

### Commit convention

Create commits with `my-commit` (conventional commits). PR titles and commit
messages are validated by the `conventional-commits` workflow; merges use
rebase-and-merge.
