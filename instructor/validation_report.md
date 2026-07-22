# Build validation report

**Validation date:** July 20, 2026  
**Delivery target:** July 22, 2026

## Static checks passed

- 41 YAML-bearing files/configurations parsed successfully.
- 37 `.qmd`/`.Rmd` documents were checked for balanced fences, balanced R delimiters, duplicate executable chunk labels, and unsafe literal inline-R examples.
- Local Markdown links, website navigation entries, project render targets, bibliographies, CSL files, themes, logos, and CSS assets resolved to files in the project.
- No superseded file references or known stale technical claims were found.
- Core executable chunks do not load optional demonstration packages.
- The root and learner copies of the synthetic CSV are identical.
- The CSV contains 200 records, unique participant IDs, the required eight columns, and the three expected site values.
- The root and learner bibliography/CSL copies are identical; BibTeX keys are unique.
- All 45 `.qmd`, `.Rmd`, and `.md` sources parsed successfully with the installed Pandoc parser.
- No generated `_site`, `_output`, `_freeze`, cache, HTML, or temporary render files are included in the source package.

## Architecture checks passed

- The root website has an explicit render list containing course pages only.
- The root website does not render `student_work/`, instructor files, optional files, or slide sources.
- `student_work/` is a standalone default Quarto project with an explicit render list and `execute-dir: project`.
- Bridge and afternoon slide directories are independent Quarto projects.
- Global author/date metadata and the global CSL override were removed.

## Required delivery-environment smoke test

This build environment has Pandoc but does not contain R or the Quarto CLI, so execution and final HTML/slide appearance were not tested here. In the exact Posit Cloud student template, complete the commands in `README.md` and the acceptance checklist in `instructor/preflight_checklist.md` before class.
