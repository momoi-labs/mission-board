---
name: interview-prep
description: Build a study guide for a job's next interview under ~/.local/share/mission-board/interviews/. Use when the user prepares for an interview or shares an interview invite.
---

# Interview prep

A study guide for one interview: what to know, what to practice, and what to
say. It is built from the job file, the career record, and whatever the
person has about the interview.

Read `CONTEXT.md` at the repo root, if present, so vocabulary matches the
project's domain language.

## Where guides live

```
~/.local/share/mission-board/   # outside the repository, never committed
├── record/                     # owned by career-record, read here
├── jobs/                       # owned by job-search, read here
└── interviews/
    └── <company>/
        ├── guide-<job-slug>.html
        └── lab/                # optional, shared by the company's guides
```

`<company>` is the company part of the job slug: `acme` for
`acme-staff-platform`. The outline names the folder, so the person can fix a
company name the slug splits wrong. A second role at the same company gets
its own guide in the same folder.

## Build

1. Read the job file the person names, `record/profile.md`, every entry in
   `record/experience/`, and the goals with `status: active`. With no job
   file, offer the `job-search` assess action first and stop. Read
   `interviews/<company>/` too: an earlier guide or lab for the same company
   is reused.
2. Ask for the format: HTML (default), or a Markdown source rendered to HTML
   on request. Ask what the person has about the interview: the invite
   (format, duration, focus areas, deadline), videos, repositories, docs.
   Read each one. Every focus area the invite names is a requirement of the
   guide.
3. Propose an outline and stop:
   - the output path;
   - the sections kept from the catalog below, and why any is dropped;
   - the diagrams, one line each;
   - labs, local and free first, with the cost of anything that runs
     outside the person's machine;
   - the study time, and the language: the interview's, because the person
     rehearses the words they will say.

   Build only after the person approves.
4. Research the gaps: requirements the fit marks partial or missing, and
   focus areas the record does not cover. Use primary sources: vendor and
   upstream docs, source code, release notes. Verify every limit, product
   name, version, and date with a fresh lookup, because these go stale.
   Keep the URL of every source.
5. Fill [templates/guide.html](templates/guide.html) following the page
   rules below.
6. Check the result:
   - Render every diagram in the light and dark themes (for example,
     headless browser screenshots with `color-scheme` forced to each) and
     move any label that overlaps a line or a box.
   - Every source link resolves.
   - Every focus area from the invite and every partial or missing
     requirement from the fit appears in a section or a practice question.
7. Write `interviews/<company>/guide-<job-slug>.html` and any lab files
   under `lab/`. Open the guide (`open` on macOS, `xdg-open` on Linux) and
   give the absolute path. Then offer the `job-search` status action to
   note the guide in the job file, moving the job to `interviewing` if it is
   not there yet.

Done when every check in step 6 passes and the person has the path.

With the Markdown format, write `guide-<job-slug>.md` instead: the same
sections, diagrams as Mermaid blocks, and each practice question as a `###`
heading under `## Practice questions` with its outline below. On request,
render it into the template as `guide-<job-slug>.html`; step 6 checks the
rendered page.

## Section catalog

Keep the order. Drop a section only when the job gives it nothing to hold.

| Section                   | Holds                                                                                |
| ------------------------- | ------------------------------------------------------------------------------------ |
| Start here                | the few facts that matter most, one card each                                        |
| Plan                      | a time-boxed checklist for the days before, optional labs, and a "Right before" list |
| Pitch                     | a 30-second introduction, one honest line on the main gap, and the answer shape      |
| Translate your experience | what the person has done, next to the name the company or product uses for it        |
| Topics                    | one section per focus area, with diagrams                                            |
| Playbooks                 | scenario cards: symptom, where to look, cause, fix now, prevention                   |
| Traps                     | details interviewers like to probe                                                   |
| Practice questions        | questions with the answer outline hidden until opened                                |
| Your examples             | story prompts tied to specific experience entries, each with a notes box             |
| Cheat sheet               | commands and queries worth recognizing                                               |
| Sources                   | every link the guide relied on                                                       |

The answer shape is: the answer in one sentence, how it works, an example
from the record, the trade-off. Answer outlines follow it. The last item of
the "Right before" list is to close the guide, because the person may share
their screen.

## Page rules

- One self-contained file: inline CSS and SVG, no external requests. Keep
  the template's focus mode, progress bar, and the checkboxes and notes it
  saves in the browser.
- Every section opens with a one-line key point. Short sentences, one idea
  per card; longer material goes inside `<details>`.
- Tag each fact card: `new` for what the person must learn, `known` for what
  the record already shows, `you` for the person's own experience.
- Each practice question is one `<details class="question">`: the question
  alone in `<summary>`, the outline after it. The page numbers them. Keep
  this markup: it lets the questions be read back without a separate file.
- Diagrams use the template's SVG classes, so they follow the theme. A
  label that crosses a line gets a `bgl` rect behind it.

## Boundaries

- The pitch, the answer outlines, and the story prompts come from the
  record. Never invent experience; name a gap as a gap.
- Preparation only: the skill does not help during a live interview.
- A lab that costs money says so up front and ships with cleanup commands.
- Nothing from the data home is copied into the repository, committed, or
  published.
- The person approves the outline before the build.
