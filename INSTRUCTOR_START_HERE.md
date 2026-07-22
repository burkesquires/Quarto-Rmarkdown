# Instructor start here

**Delivery:** Wednesday, July 22, 2026, 9:00 AM–5:00 PM

This project is designed around one rule: **the course website is read-only; learners work only in `student_work/`.**

## Before opening the room

1. Create the Posit Cloud assignment from this project and open it from a non-instructor account.
2. Run the checks in `instructor/preflight_checklist.md`.
3. Render the root website once:

   ```bash
   quarto render
   ```

4. Test the two editable learner files independently:

   ```bash
   Rscript -e 'rmarkdown::render("student_work/morning_report.Rmd")'
   cd student_work
   quarto render my_report.qmd --to html
   quarto render parameter_demo.qmd --to html
   cd ..
   ```

5. Render the slide decks you plan to use. The complete command set is in `README.md`.
6. Keep these files open during delivery:
   - `instructor/run_of_show.md`
   - `instructor/preflight_checklist.md`
   - `student_work/checkpoints/`

## What learners edit

| Block | Learner file |
|---|---|
| Morning R Markdown | `student_work/morning_report.Rmd` |
| Bridge | A copy saved as `student_work/bridge_converted.qmd` |
| Quarto modules and capstone | `student_work/my_report.qmd` |
| Parameters | `student_work/parameter_demo.qmd` |

Learners should not edit the root `_quarto.yml`, lesson notebooks, slide sources, `capstone.qmd`, or files inside `student_work/checkpoints/`.

## Safe preview commands

For the instructor website:

```bash
quarto preview --no-watch-inputs --no-browse
```

For a learner report, change into the learner project first:

```bash
cd student_work
quarto preview my_report.qmd --no-watch-inputs --no-browse
```

The learner project is a standalone default project with an explicit render list. Previewing `my_report.qmd` will not ask Quarto to update the course website or `capstone.qmd`.

## Completion standard

A learner is finished when `student_work/my_report.qmd` renders from a restarted R session and contains:

- one inline result,
- one captioned `knitr::kable()` table,
- one captioned `ggplot2` figure,
- `fig-alt`,
- one working cross-reference,
- and one citation.

Do not delay the room for Python, interactive widgets, PDF, deep styling, batch rendering, or public publishing. Those are demonstration or reference topics.

## Recovery sequence

1. Read the first useful error and identify its file and line.
2. Confirm the learner is editing a file in `student_work/`.
3. Restart R and render the complete learner file.
4. Compare the most recent change with the nearest checkpoint.
5. Copy only the relevant section from a checkpoint; keep checkpoint files in place.
6. Move the learner to a known-good project copy when the environment—not their code—is broken.

## Data and publishing boundary

All workshop biomarker records are synthetic. Public hosting demonstrations must use only content approved for public release. Controlled, sensitive, personally identifiable, protected-health, unpublished, or otherwise restricted information belongs only on institutionally approved systems.
