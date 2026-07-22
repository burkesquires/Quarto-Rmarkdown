# Instructor run of show

## Delivery principle

Prioritize a working cumulative report over coverage. When the room falls behind, drop bonus demonstrations in this order: Python, interactive widgets, PDF, deep theming, batch rendering, then advanced table styling.

## 8:30–9:00 — room and workspace check

- Open the exact student assignment from a non-instructor account.
- Edit and render `student_work/my_report.qmd`.
- Confirm the student copy is writable.
- Open the course site, the student report, and this run of show in separate tabs.
- Confirm the projector shows readable code at 125–150% zoom.
- Keep `student_work/checkpoints/` open in the Files pane.

## 9:00–9:15 — preflight

Stop the room after each step. Do not continue until most participants can render the learner report.

Success signal: each learner changes `YOUR NAME`, renders, and sees the 5.5 readiness result.

Common problems:

- **Change does not save:** learner opened the template, not an assigned copy.
- **Render invokes the website:** learner opened a course page instead of `student_work/my_report.qmd`.
- **Missing package:** move learner to a known-good copy or pair them while an assistant fixes the environment.
- **Path error:** confirm the learner opened the project root and did not move `my_report.qmd`.

## 9:15–10:00 — R Markdown

Required learner action:

1. Identify YAML, markdown, and chunks.
2. Knit from a restarted R session.
3. Edit `student_work/morning_report.Rmd`, control one chunk, and add one inline value.

Teaching emphasis: source order matters; objects created only in the Console do not exist during a clean render.

## 10:15–10:35 — bridge

Write the three changes on one slide or board:

- `.Rmd` → `.qmd`
- `output:` → `format:`
- chunk options → `#|` lines

Learners convert a copy of `student_work/morning_report.Rmd` and compare it with `student_work/checkpoints/bridge_converted.qmd`. Do not suggest that existing R Markdown files are obsolete.

## 10:35–11:10 — first Quarto report

Learners edit `student_work/my_report.qmd`:

- title and author,
- introduction paragraph,
- one callout,
- `code-fold: true`.

At 11:05, ask everyone to render. Offer `checkpoints/01_yaml_complete.qmd` to anyone who is blocked.

## 11:10–12:10 — tables

Required: one `knitr::kable()` table with a `tbl-` label and `tbl-cap`.

Demonstrate only after the room has a working core table:

- `kableExtra`,
- `broom`,
- `DT` with an explicit HTML-only warning.

At 12:00, render and use `checkpoints/02_table_complete.qmd` for recovery.

## 13:10–13:55 — figures

Required: one ggplot with:

- `fig-` label,
- `fig-cap`,
- `fig-alt`,
- clear axis labels,
- more than color alone to distinguish groups.

At 13:45, render and use `checkpoints/03_figure_complete.qmd` for recovery.

## 13:55–14:40 — cross-references and citations

Required:

- a prose reference to the table,
- a prose reference to the figure,
- one citation key.

Show equations briefly. Use author-date citation output first; demonstrate CSL changes second.

At 14:30, render and use `checkpoints/04_crossrefs_citations_complete.qmd` for recovery.

## 14:55–15:20 — Revealjs

Instructor demo plus one learner edit. Do not ask learners to create a full deck.

Suggested action: copy `my_report.qmd` to `my_slides.qmd`, change the copy to `format: revealjs`, and observe how level-2 headings form slides. Keep the cumulative report unchanged.

## 15:20–15:45 — parameters

Learners change one value in `student_work/parameter_demo.qmd`. Avoid batch loops unless the room is ahead.

Required concept: one source file can use a named input value. Not required: production automation.

## 15:45–16:20 — capstone

Learners continue `my_report.qmd`. Require a clean-session render first. Then they improve prose and remove clutter.

Completion standard: inline result, table, figure, alt text, cross-reference, and citation.

## 16:20–16:40 — projects and sharing

Teach three cases:

1. Website → share the complete `_site/` directory.
2. One portable HTML report → `embed-resources: true`.
3. Controlled internal work → institutionally approved authenticated platform.

Do not run a public publishing command with real or uncontrolled data.

## 16:40–17:00 — debrief

- Ask two volunteers to show a report.
- Have everyone export `student_work/`.
- Collect the three-question exit ticket.
- End with one realistic next action, not a list of every advanced feature.
