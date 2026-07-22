# R Markdown + Quarto for Reproducible Science — Instructor Edition

Start with [`INSTRUCTOR_START_HERE.md`](INSTRUCTOR_START_HERE.md). A detailed change record is in [`REVISION_NOTES.md`](REVISION_NOTES.md).

Classroom-ready project for the NIEHS one-day workshop. The revised design keeps the training website read-only and gives every participant a separate cumulative Quarto project in `student_work/`.

## Delivery target

**Wednesday, July 22, 2026, 9:00 AM–5:00 PM**

The most important learning outcome is not coverage of every Quarto feature. It is that each participant can render a report from a clean session containing narrative, an inline result, a table, a figure, a caption, a cross-reference, and a citation.

## Why the project is structured this way

Quarto websites manage a collection of documents as one project. A student who edits a lesson page inside that website can encounter a failure in another project page during preview. The revised project avoids that failure mode:

- `index.qmd`, lesson notebooks, and slide sources are instructor/course materials.
- `student_work/` is a standalone Quarto project with its own `_quarto.yml`.
- The Quarto slide directories are also small nested projects, so previewing a deck does not invoke the course website.
- Students edit `student_work/morning_report.Rmd` in the morning and `student_work/my_report.qmd` after the bridge.
- Morning, bridge, and four cumulative Quarto checkpoints provide rapid recovery.
- `capstone.qmd` tells learners to finish the report they already built rather than starting over.

R Markdown is presented as mature and supported, not as deprecated. Quarto is introduced as an additional, multi-language publishing option with useful built-in features.

## Revised schedule

| Time | Focus | Delivery |
|---|---|---|
| 09:00–09:15 | Setup and student workspace | Everyone renders `student_work/my_report.qmd` |
| 09:15–10:00 | R Markdown anatomy, clean render, chunks, inline code | One cumulative exercise |
| 10:00–10:15 | Break | |
| 10:15–10:35 | R Markdown → Quarto bridge | Convert one small file |
| 10:35–11:10 | First Quarto report | YAML, callout, code folding |
| 11:10–12:10 | Code options and tables | Everyone builds one `kable()` table; advanced tables are demonstrations |
| 12:10–13:10 | Lunch | |
| 13:10–13:55 | Figures | One ggplot, caption, alt text, and label |
| 13:55–14:40 | Cross-references and citations | Equations are a brief demonstration |
| 14:40–14:55 | Break | |
| 14:55–15:20 | Revealjs | Instructor demo plus one learner edit |
| 15:20–15:45 | Parameters | Instructor demo plus one parameter change |
| 15:45–16:20 | Cumulative capstone | Polish the report already built |
| 16:20–16:40 | Projects and safe sharing | No live theme-editing exercise |
| 16:40–17:00 | Debrief, troubleshooting, exit ticket | Export work and state one next action |

Contact time is 6 hours 30 minutes, plus two 15-minute breaks and a 60-minute lunch.

## Learning tiers

### Everyone does

- Render from a clean R session.
- Edit YAML.
- Use a setup chunk and an inline result.
- Produce one `knitr::kable()` table.
- Produce one `ggplot2` figure.
- Add captions, a figure label, alt text, and a cross-reference.
- Add one citation.

### Instructor demonstrates

- Revealjs.
- Parameters.
- DOCX output.
- Project configuration.
- Standalone HTML versus a complete website.
- Safe internal versus public publishing.

### Bonus/reference

- Python and `reticulate`.
- `DT`, `plotly`, `patchwork`, `broom`, and deep `kableExtra` styling.
- PDF/LaTeX.
- SCSS customization.
- Batch rendering and public publishing.
- Citation automation tools that depend on external services (optional archive material).

## File structure

```text
rmarkdown_quarto_niehs/
├── README.md
├── INSTRUCTOR_START_HERE.md
├── REVISION_NOTES.md
├── _quarto.yml
├── index.qmd
├── 00_setup.qmd
├── capstone.qmd
├── next_steps.qmd
├── data/
│   ├── workshop_biomarkers.csv
│   └── README.md
├── student_work/
│   ├── _quarto.yml
│   ├── README.md
│   ├── morning_report.Rmd
│   ├── my_report.qmd
│   ├── parameter_demo.qmd
│   ├── references.bib
│   ├── nature.csl
│   ├── data/workshop_biomarkers.csv
│   └── checkpoints/
│       ├── morning_report_complete.Rmd
│       ├── bridge_converted.qmd
│       ├── 01_yaml_complete.qmd
│       ├── 02_table_complete.qmd
│       ├── 03_figure_complete.qmd
│       └── 04_crossrefs_citations_complete.qmd
├── morning_rmarkdown/
├── bridge/
├── afternoon_quarto/
├── instructor/
│   ├── run_of_show.md
│   ├── preflight_checklist.md
│   ├── validation_report.md
│   └── exercise_solutions.qmd
└── optional/
```

## Data

`data/workshop_biomarkers.csv` is synthetic and generated with a fixed seed. It contains 200 records with age, sex, site, serum PFOA, serum PFOS, BMI, and cholesterol. The generator intentionally creates a modest positive PFOA–cholesterol relationship so a trend is visible in class.

Every page that uses the data should explicitly state:

> These data are simulated solely for teaching. Generated relationships must not be interpreted as evidence about PFAS exposure or health outcomes.

## Pre-workshop requirements

### Before class

- Create the managed Posit Cloud assignment/template.
- Require participants to create accounts and complete MFA before Wednesday.
- Ensure each participant receives a writable copy rather than the instructor source project.
- Preinstall the core packages: `rmarkdown`, `knitr`, `dplyr`, and `ggplot2`.
- Preinstall demonstration packages only if you plan to execute those demonstrations: `kableExtra`, `DT`, `broom`, `patchwork`, `plotly`, and `quarto`.
- Do not make Python, TinyTeX, or a system LaTeX installation prerequisites for the core class.
- Confirm the supplied NIEHS logo renders in every slide deck.
- Render the website and every slide deck from the exact student template.
- Test from a non-instructor account.

### Day of class

- Open the workspace before participants arrive.
- Keep `instructor/run_of_show.md` open.
- Project the lesson notebook or a verified slide deck; do not improvise from stale output.
- Have `student_work/checkpoints/` visible in the Files pane.
- Keep one untouched participant copy for troubleshooting.
- Have a local copy of the final ZIP available in case a cloud assignment must be recreated.

## First 15 minutes

Do not begin lecture content until participants can all answer yes to these:

1. I am in my own writable project copy.
2. `quarto --version` prints a version.
3. `student_work/my_report.qmd` renders.
4. The four core R packages are installed.

Avoid live package installation for the entire room. Move a participant to a known-good copy or pair them with a neighbor while an assistant troubleshoots.

## Teaching notes

### Morning

The morning lesson pages are read-only. Learners edit one cumulative file, `student_work/morning_report.Rmd`, because they need to recognize and maintain existing `.Rmd` content. Keep the message neutral: R Markdown remains supported; Quarto is a strong option for new work and for built-in cross-references, projects, and multi-language publishing.

### Bridge

Use `student_work/morning_report.Rmd` as the safe conversion source. Make only three syntax changes memorable:

1. `.Rmd` → `.qmd`
2. `output:` → `format:`
3. Chunk options move to `#|` lines

Everything else should be framed as transfer, not relearning.

### Tables

Require only `knitr::kable()`. Demonstrate `kableExtra`, `DT`, and `broom` after everyone has a working table. Do not require interactive widgets for multi-format reports.

### Figures

Require an informative caption and `fig-alt`. Use shape as well as color when groups are distinguished. Remind learners that synthetic relationships are teaching devices.

### Cross-references and citations

Use author-date output for the explanation because learners can see the difference between narrative and parenthetical citation syntax. Demonstrate that a CSL file changes formatting after the basic citation works.

### Presentations and parameters

These are demonstrations with one small learner edit. They are not additional capstones.

### Capstone

Students continue `my_report.qmd`. The minimum-success callout is the completion standard. Stretch goals are optional.

## Publishing and data safety

Public services are for content approved for public release. Do not imply that a private external repository is automatically approved for agency information. Do not advise participants to disable endpoint protection, restore quarantined files, or move work to personal devices.

Teach three distinct sharing cases:

1. A website is shared as the complete `_site/` directory.
2. A single portable report uses `embed-resources: true`.
3. Internal controlled sharing uses an institutionally approved platform and authorization process.

## Validation commands

Run these from the project root in the delivery environment:

```bash
quarto render
```

Then render both editable learner files and the standalone learner project:

```bash
Rscript -e 'rmarkdown::render("student_work/morning_report.Rmd")'
Rscript -e 'rmarkdown::render("student_work/checkpoints/morning_report_complete.Rmd")'
cd student_work
quarto render my_report.qmd --to html
quarto render parameter_demo.qmd --to html
quarto render checkpoints/bridge_converted.qmd --to html
quarto render checkpoints/01_yaml_complete.qmd --to html
quarto render checkpoints/02_table_complete.qmd --to html
quarto render checkpoints/03_figure_complete.qmd --to html
quarto render checkpoints/04_crossrefs_citations_complete.qmd --to html
cd ..
```

Render slide decks explicitly:

```bash
quarto render bridge/slides/bridge_deck.qmd
for f in afternoon_quarto/slides/[0-9]*.qmd; do quarto render "$f"; done
Rscript -e 'rmarkdown::render("morning_rmarkdown/slides/slides_01_welcome_and_basics.Rmd")'
Rscript -e 'rmarkdown::render("morning_rmarkdown/slides/slides_02_code_chunks.Rmd")'
```

Knit the two morning R Markdown files in RStudio or run:

```r
rmarkdown::render("morning_rmarkdown/01_rmarkdown_basics.Rmd")
rmarkdown::render("morning_rmarkdown/02_code_chunks.Rmd")
```

Finally, restart R and render `student_work/my_report.qmd` without running any chunks manually.

## Known environment limitation of this package build

The project was statically checked for YAML, paths, stale references, duplicate labels, and unsafe inline R examples. The package still requires a final smoke test in the actual Posit Cloud template because this build environment does not contain R or the Quarto CLI.
