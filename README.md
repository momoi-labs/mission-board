# Mission board

![A pirate guild mission board with Chopper's hat and Robin's archaeology books.](docs/assets/mission-board.png)

A local-first career assistant built with skills and plain files. Track your
experience, find opportunities, and prepare tailored applications.

## Status

The `career-record` skill keeps the profile and experience record in
`personal-data/`. Job search, resume tailoring, cover letters, and PDF export
are not implemented yet.

## Planned scope

- Record day-to-day work, responsibilities, projects, and results.
- Review resumes for clarity, missing evidence, and outdated information.
- Tailor resumes to a job using the person's actual experience.
- Research jobs using the person's preferences and return source links.
- Write cover letters grounded in the person's experience and the role.
- Export resumes and cover letters to PDF when needed.

Career records are the source material. Resumes and letters are tailored outputs.
The person reviews each application and decides what to send.

## Boundaries

No automated applications, bulk outreach, LinkedIn spam, or engagement automation.
Never invent experience, credentials, or results to match a job description.

## Public and private files

This repository is intended for reusable skills, templates, documentation,
and fictional examples. Personal details, career records, saved jobs,
application notes, and generated documents live in `personal-data/` at the
repository root. That folder is gitignored: never commit, track, or publish
its contents.

Local-first describes where the files live. An AI provider may still process
content supplied to the assistant.

## Development

Track work in [GitHub Issues](https://github.com/momoi-labs/mission-board/issues).
Read [the engineering principles](docs/PRINCIPLES.md) before contributing.
