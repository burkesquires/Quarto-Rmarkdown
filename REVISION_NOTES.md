# Classroom-ready revision notes

Prepared July 20, 2026 for the July 22, 2026 NIEHS workshop.

## Delivery architecture

- Restricted the root website to an explicit list of course pages.
- Removed learner files, slide projects, instructor files, and optional material from the root website render.
- Created a standalone `student_work/` Quarto project with its own output directory, execution directory, and explicit render list.
- Created independent Quarto projects for the bridge deck and afternoon slide decks.
- Added a cumulative morning `.Rmd`, cumulative afternoon `.qmd`, parameter demonstration, and staged recovery checkpoints.
- Changed the capstone from “start a new report” to “finish the report already built.”

## Curriculum and schedule

- Reframed R Markdown as mature and supported rather than deprecated.
- Set one observable end-of-day success criterion.
- Divided topics into required learner work, instructor demonstrations, and bonus/reference material.
- Revised the schedule to 6 hours 30 minutes of contact time, two 15-minute breaks, and a 60-minute lunch.
- Reduced the required package surface to `rmarkdown`, `knitr`, `dplyr`, and `ggplot2`.
- Made Python, interactive widgets, PDF, deep table styling, SCSS, batch rendering, and public publishing optional.

## Technical corrections

- Replaced unsafe literal inline-R examples with `knitr::inline_expr()` where needed.
- Removed duplicate global author/date metadata.
- Corrected stale and missing lesson, slide, theme, logo, and checkpoint paths.
- Corrected the distinction between execution caching and project `freeze`.
- Corrected standalone HTML guidance to use `embed-resources: true` and distinguished it from sharing a complete website directory.
- Replaced a nonexistent DOCX-output helper with `knitr::pandoc_to("docx")`.
- Marked mixed R/Python execution as optional because knitr uses `reticulate` for that workflow.
- Corrected citation examples so the rendered author-date style matches the lesson.
- Removed manual “Table 1” and “Figure 1” text from captions.
- Added static fallbacks for HTML-only widgets.

## Data, accessibility, and scientific boundaries

- Standardized all core examples on one fixed, 200-row synthetic biomarker dataset.
- Added PFOA, PFOS, BMI, age, sex, site, and cholesterol consistently.
- Added prominent language that generated relationships are teaching devices, not scientific evidence.
- Required informative captions and `fig-alt` for the learner figure.
- Used shape in addition to color in the completed figure checkpoint.
- Added clear public-release and institutionally approved sharing language.

## Instructor support

- Replaced stale solutions with a completed cumulative report.
- Added `INSTRUCTOR_START_HERE.md`, a timed run of show, and a preflight checklist.
- Added exact website, learner-project, checkpoint, and slide validation commands.
- Added recovery instructions that keep checkpoint files unmodified.

## Validation performed in the build environment

- Parsed all YAML front matter and all `_quarto.yml` files.
- Checked all Markdown fence pairs.
- Checked executable R chunks for balanced delimiters and duplicate labels.
- Checked for unsafe literal inline-R examples.
- Checked local Markdown links, navigation targets, render targets, bibliography files, CSL files, themes, logos, and CSS.
- Checked for stale file references and superseded technical claims.
- Checked that core executable chunks do not load optional packages.
- Confirmed the root and learner CSV files are identical, contain 200 unique records, and have the required columns and site values.
- Confirmed bibliography and CSL copies match.
- Parsed all 45 `.qmd`, `.Rmd`, and `.md` sources successfully with Pandoc.

The build environment does not contain R or the Quarto CLI. A final clean-session render in the exact Posit Cloud student template remains required; the commands and acceptance criteria are in `README.md` and `instructor/preflight_checklist.md`.
