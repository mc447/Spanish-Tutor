# Spanish Growth Hub

A single-file command center for Lucas's Spanish tutor search, built from Juan's brief.

`spanish-growth-hub.html` is published as a Claude artifact, built on the **Juan UI/UX
standard** (reference build: Madera Well Dashboard) so it reads as one family with the
other Twin Home artifacts: sticky header, left tab rail, cards and status chips, the
sage/water/clay palette, Source Serif 4 headings over Public Sans.

Navigation is one rail in two groups. **Work**: Today, Pipeline, Candidates, Mariaelena,
Learning. **Reference**: Job post, Upwork searches, Daily update, The mission. Badges show
live counts (Today's done/total, finalists waiting on Mariaelena) and the chosen
destination is remembered per viewer.

It covers the whole run:

- **Today** — the eight moves and MC's handoff checklist, under a lead card restating the
  objective. **Job post**, **Upwork searches**, **Daily update** and **The mission** (the
  requirements plus who does what) sit under Reference.
- **Pipeline** — Sourcing → Screening → Interview → Trial Session → Mariaelena Review → Selected → Hired, drag-and-drop on desktop, one-tap advance on touch.
- **Add tutor** — a primary button in the sticky header, so a tutor can be logged from
  any view. It opens a quick-add form (name, Upwork URL, rate, time zone) that stays open
  after each save and counts what you have added, so a sourcing run becomes one pass
  instead of one trip through the drawer per tutor. Enter saves, Escape closes, a repeated
  name is flagged but never blocked, and "Add and open profile" jumps straight into the
  full record.
- **Candidates** — full profile per tutor, an 18-item screening scorecard where every row carries evidence and unknowns stay visibly unknown, the 9 red flags, the 11 interview questions with notes, and the 11-point trial evaluation with Lucas's and Mariaelena's feedback.
- **Mariaelena** — finalists only, each with strengths, concerns, interview notes and trial results, and four buttons: approve for trial, keep as backup, pass, select tutor.
- **Learning** — unlocks on hire. Current unit, upcoming quizzes and tests, vocabulary and grammar, a regular -ar/-er/-ir conjugation frame, weekly progress sparklines across eight skills, the homework upload workflow, and tutor notes.

## Filling a tutor in from Upwork

Open a tutor in the hub and press **Paste the profile**. Paste everything from their
Upwork profile (or drop a screenshot) and Claude fills the form, quoting the line each
answer came from. Nothing is saved until you tick it and press Apply.

A profile **link on its own cannot work**, for three separate reasons:

1. The artifact's network is blocked by CSP — it can reach no external host, ever.
2. Upwork profiles require a signed-in session; an anonymous fetch sees nothing.
3. The only route that could read a logged-in page is the Claude desktop app's browser,
   which is owner-only, desktop-only, and whose tool schemas cannot be read at runtime
   (`describeTool` rejects for `host:` servers), so the call shape would be a guess.

Pasting the link alone is detected and answered with what to do instead.

Design rules the reader follows:

- The prompt forbids inference and requires a verbatim quote under 150 characters for
  every claim. Anything that cannot be quoted is omitted rather than guessed.
- Facts and ratings arrive ticked; **red flags arrive unticked**, since a flag is an
  accusation and deserves a deliberate tick.
- Criteria the text did not cover are listed explicitly as left unknown, and stay
  unknown. A tutor is still only "qualified" once all six core must-haves are assessed.
- Each error code gets its own copy (rate limit, oversized paste, declined consent)
  rather than one generic failure banner.

## Working together

The hub is live for whoever has it open at the same time:

- **Presence** — an avatar stack in the header shows who else is in the hub and which
  tab they are on; a badge on a candidate card and a line in the drawer show who else
  is looking at that tutor, so two people don't screen the same person blind.
- **Nudge** — on a finalist card or in the drawer, pings everyone who currently has the
  hub open. It reaches nobody who is away, and the button says so and disables itself
  when you are alone.
- **Discuss** — opens claude.ai's own comment composer anchored to that tutor. Threads
  live in the artifact's comment panel, not in the page; the page only opens the box.

Presence is advisory and never gates anything: anyone can set it, so nothing is locked
on the strength of it.

## How the data works

State lives in the artifact's shared database (`db` capability) so MC, Cherry and Mariaelena
all see the same board. Everyone needs **Contributor or Editor** access for their changes to
save; file attachments on homework need Editor. Without the database the page falls back to
browser-local storage and says so in the footer.

Collections: `candidates`, `assignments`, and the documents `meta/search`, `meta/learning`,
`meta/board`.

Capabilities declared: `db`, `user` (profile scope, for names), `assets` (homework
attachments), `room` (presence, with the `nudge` topic open to Contributors), and
`comments` in composer-only form so no consent prompt is ever shown, and `sample`
(the viewer's own Claude usage) for the Upwork profile reader.
