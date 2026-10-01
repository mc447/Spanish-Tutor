# Spanish Growth Hub

A single-file command center for Lucas's Spanish tutor search, built from Juan's brief.

`spanish-growth-hub.html` is published as a Claude artifact. It covers the whole run:

- **Command** — the mission requirements, today's action plan, MC's handoff checklist, a ready-to-post Upwork job post, six Upwork talent searches, and a daily update for Cherry generated from live pipeline counts.
- **Pipeline** — Sourcing → Screening → Interview → Trial Session → Mariaelena Review → Selected → Hired, drag-and-drop on desktop, one-tap advance on touch.
- **Candidates** — full profile per tutor, an 18-item screening scorecard where every row carries evidence and unknowns stay visibly unknown, the 9 red flags, the 11 interview questions with notes, and the 11-point trial evaluation with Lucas's and Mariaelena's feedback.
- **Mariaelena** — finalists only, each with strengths, concerns, interview notes and trial results, and four buttons: approve for trial, keep as backup, pass, select tutor.
- **Learning** — unlocks on hire. Current unit, upcoming quizzes and tests, vocabulary and grammar, a regular -ar/-er/-ir conjugation frame, weekly progress sparklines across eight skills, the homework upload workflow, and tutor notes.

## How the data works

State lives in the artifact's shared database (`db` capability) so MC, Cherry and Mariaelena
all see the same board. Everyone needs **Contributor or Editor** access for their changes to
save; file attachments on homework need Editor. Without the database the page falls back to
browser-local storage and says so in the footer.

Collections: `candidates`, `assignments`, and the documents `meta/search`, `meta/learning`,
`meta/board`.
