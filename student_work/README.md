# Student workspace

This directory is a small Quarto project separate from the read-only course website.

## Files you edit

- `morning_report.Rmd` — the cumulative R Markdown file used in the morning.
- `my_report.qmd` — the cumulative Quarto report used after the bridge.
- `bridge_converted.qmd` — a copy you create during the bridge exercise.
- `parameter_demo.qmd` — a small parameterized report used for one controlled edit.

## Files you normally do not edit

- `_quarto.yml` — keeps this learner project small and independent.
- `data/workshop_biomarkers.csv` — synthetic teaching data.
- `references.bib` — local citation source.
- `checkpoints/` — recovery copies showing completed stages.

## Render commands

From the workshop root:

```bash
Rscript -e 'rmarkdown::render("student_work/morning_report.Rmd")'
quarto render student_work/my_report.qmd
```

From inside `student_work/`:

```bash
Rscript -e 'rmarkdown::render("morning_report.Rmd")'
quarto render my_report.qmd
```

The Quarto output directory is `student_work/_output/`. R Markdown normally writes its HTML beside the `.Rmd` source unless another output directory is specified.

## Recovery

Checkpoint files are examples, not required starting points. Keep them in `checkpoints/`; open the closest one beside your learner file and copy only the relevant YAML, chunk, or section. Do not overwrite, move, or rename a checkpoint.

All data in this workspace are synthetic and intended only for training.
