# Mission board

[English](README.md) | [Português (Brasil)](README.pt-BR.md) | [Español (España)](README.es-ES.md)

![A pirate guild mission board with Chopper's hat and Robin's archaeology books.](docs/assets/mission-board.png)

A local-first career assistant built with skills and plain files. Track your
experience, find opportunities, and prepare tailored applications.

## Status

The `career-record` skill keeps the profile, experience record, and career
goals in `~/.local/share/mission-board/`. The `job-search` skill assesses a
listing the person brings against that record and tracks its status. The
`job-snapshot` skill renders those jobs as one shareable HTML page.
Searching job boards, resume tailoring, cover letters, and PDF export are not
implemented yet.

## Available skills

[Ideal work](.agents/skills/ideal-work/SKILL.md) guides a conversation about the
work you enjoy, how you want to collaborate, and your next career objectives.
Choose a short description, a few paragraphs, or a fuller personal reflection.

To start, ask your agent to use `ideal-work` in this repository. For example:

> Use ideal-work to help me figure out how I want to work and what to explore next.

The exercise stays in the conversation unless you ask to save it in
`~/.local/share/mission-board/`, outside this repository.

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
application notes, and generated documents live in
`~/.local/share/mission-board/`, outside the repository: never copy them into
the repo, commit, or publish them.

Local-first describes where the files live. An AI provider may still process
content supplied to the assistant.

## Development

Track work in [GitHub Issues](https://github.com/momoi-labs/mission-board/issues).
Read [the engineering principles](docs/PRINCIPLES.md) before contributing.
