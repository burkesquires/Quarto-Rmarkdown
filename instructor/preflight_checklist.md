# Preflight checklist

## Workspace

- [ ] Assignment creates a writable copy for each participant.
- [ ] A non-instructor account can edit and save `student_work/morning_report.Rmd` and `student_work/my_report.qmd`.
- [ ] The root website and nested `student_work` project are both detected correctly.
- [ ] The student report renders without rendering the website.
- [ ] `morning_report.Rmd`, `parameter_demo.qmd`, and all checkpoint files render from the student workspace.

## Software

- [ ] `quarto --version` succeeds.
- [ ] `quarto check knitr` finds R and knitr.
- [ ] Core packages installed: `rmarkdown`, `knitr`, `dplyr`, `ggplot2`.
- [ ] Demonstration packages installed only as needed: `kableExtra`, `DT`, `broom`, `patchwork`, `plotly`, `quarto`.
- [ ] Python is not required for core exercises.
- [ ] PDF is not required for core exercises.

## Rendering

- [ ] `quarto render` succeeds at the course root.
- [ ] Both morning lesson `.Rmd` files and `student_work/morning_report.Rmd` knit from clean sessions.
- [ ] Both morning slide decks, the bridge deck, and all Quarto Revealjs decks render.
- [ ] No broken local file references remain.
- [ ] No duplicate author appears in rendered metadata.
- [ ] Citations in Module 4 render author-date before the CSL demonstration.
- [ ] Every core figure has `fig-alt`.

## Teaching assets

- [ ] Slide titles and durations match the revised schedule.
- [ ] Projector zoom makes code readable.
- [ ] Synthetic-data disclaimer is visible.
- [ ] Minimum-success capstone callout is visible.
- [ ] Student export instructions are tested.

## Security

- [ ] No exercise asks learners to upload real sensitive data.
- [ ] Public publishing is framed as public-release-only.
- [ ] No instruction recommends bypassing endpoint protection.
- [ ] No instruction describes an external private repository as automatically approved.
