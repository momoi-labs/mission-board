---
status: accepted
date: 2026-09-17
supersedes: []
superseded_by: null
tags: [format, compatibility]
---

# Career record files are Markdown with YAML frontmatter, versioned

Career record files (`profile.md` and `experience/<slug>.md`) use YAML
frontmatter with a `format: 1` field and a Markdown body. Frontmatter was
chosen over a plain-heading contract because later skills (job search, resume
tailoring) need to parse structured fields such as dates and source links,
while the body stays prose the person can edit freely.

> **Append-only:** never edit an accepted ADR. To change this decision, write a
> new ADR and link it to the old one via `supersedes` / `superseded_by`.

## Consequences

- Each file format is a compatibility contract (Principle 3): new optional
  fields may be added within version 1; removing, renaming, or retyping a
  field requires version 2, and version 2 readers must still read version 1
  files.
- Readers must tolerate frontmatter fields they do not recognize.
