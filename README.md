# R Markdown + Quarto for Reproducible Science — NIEHS Training

A one-day, hands-on workshop combining **R Markdown** and **Quarto** for NIEHS scientists. Designed to run on [Posit Cloud](https://posit.cloud) with zero local installation.

This is the **instructor edition** README. The student-facing landing page is `index.qmd`.

## Why this workshop is structured the way it is

R Markdown is in maintenance mode; Quarto is the modern, actively-developed successor. The skills transfer almost wholesale — same YAML/markdown/chunk model, same R packages (`ggplot2`, `kableExtra`, `DT`, `broom`, `patchwork`, `plotly`), nearly identical citation and equation syntax.

So the workshop teaches the foundation (R Markdown morning) and then dives deep into Quarto's distinctive features (afternoon), using a **25-minute explicit bridge** between them so students understand the migration path. Features that work identically in both tools (tables, figures, equations) are taught **once** — in Quarto, the modern tool — using NIEHS-flavored examples (PFOA biomonitoring, PFAS thresholds) that anchor the content in the audience's actual work.

**Time split: R Markdown ~80 min, Quarto ~3:55, capstone + wrap ~50 min.** Heavily Quarto-weighted because that's where development is happening, and because the morning's R Markdown skills are sufficient to read and maintain existing `.Rmd` files — the more important investment is in `.qmd`.

## Workshop schedule

| Time | Block | File | Duration |
|------|-------|------|---------|
| 09:00 – 09:05 | Posit Cloud verification | `00_setup.qmd` | 5 min |
| 09:05 – 09:30 | **R Markdown basics** | `morning_rmarkdown/01_rmarkdown_basics.Rmd` | 25 min |
| 09:30 – 10:00 | **Code chunks + inline code** | `morning_rmarkdown/02_code_chunks.Rmd` | 30 min |
| 10:00 – 10:15 | Break | | 15 min |
| 10:15 – 10:40 | **Bridge: R Markdown → Quarto** | `bridge/rmd_to_quarto_bridge.qmd` | 25 min |
| 10:40 – 11:10 | Quarto 1 — your first `.qmd` | `afternoon_quarto/01_first_document.qmd` | 30 min |
| 11:10 – 12:10 | Quarto 2 — code chunks + tables | `afternoon_quarto/02_code_chunks_and_tables.qmd` | 60 min |
| 12:10 – 13:10 | Lunch | | 60 min |
| 13:10 – 13:55 | Quarto 3 — figures & visualizations | `afternoon_quarto/03_figures_and_visualizations.qmd` | 45 min |
| 13:55 – 14:40 | Quarto 4 — equations, cross-refs, citations | `afternoon_quarto/04_equations_crossrefs_citations.qmd` | 45 min |
| 14:40 – 14:55 | Break | | 15 min |
| 14:55 – 15:25 | Quarto 5 — revealjs presentations | `afternoon_quarto/05_revealjs_presentations.qmd` | 30 min |
| 15:25 – 15:50 | Quarto 6 — parameterized reports | `afternoon_quarto/06_parameterized_reports.qmd` | 25 min |
| 15:50 – 16:10 | Quarto 7 — projects + themes + publishing | `afternoon_quarto/07_projects_themes_publishing.qmd` | 20 min |
| 16:10 – 16:35 | Capstone | `capstone.qmd` | 25 min |
| 16:35 – 17:00 | Wrap-up + next steps | `next_steps.qmd` | 25 min |

Total: 6 hours of contact + 30 min breaks + 60 min lunch.

## File structure

```
rmarkdown_quarto_niehs/
├── README.md                                  ← This file (instructor edition)
├── _quarto.yml                                ← Quarto website project config
├── index.qmd                                  ← Student-facing landing page
├── 00_setup.qmd                               ← Posit Cloud verification
├── capstone.qmd                               ← End-of-day capstone exercise
├── next_steps.qmd                             ← Post-workshop local-install guide
├── styles.scss                                ← Site theme layer (NIEHS palette overlay)
├── references.bib                             ← Sample bibliography
├── nature.csl                                 ← Local citation style (avoids render-time network fetch)
├── rmarkdown_quarto_training.Rproj            ← Posit Cloud / RStudio project marker
│
├── morning_rmarkdown/                         ← R Markdown training (Burke's existing materials)
│   ├── 01_rmarkdown_basics.Rmd
│   ├── 02_code_chunks.Rmd
│   ├── quick_reference.Rmd
│   └── slides/
│       ├── slides_01_welcome_and_basics.Rmd   ← ioslides
│       ├── slides_02_code_chunks.Rmd          ← ioslides
│       └── rmd_slides_style.css
│
├── bridge/
│   ├── rmd_to_quarto_bridge.qmd               ← 25-min bridge module
│   └── slides/
│       └── bridge_deck.qmd                    ← revealjs
│
├── afternoon_quarto/                          ← Quarto modules
│   ├── 01_first_document.qmd
│   ├── 02_code_chunks_and_tables.qmd          ← Tables migrated from old Module 03
│   ├── 03_figures_and_visualizations.qmd      ← NEW from old Module 04
│   ├── 04_equations_crossrefs_citations.qmd   ← Equations from old Module 05
│   ├── 05_revealjs_presentations.qmd
│   ├── 06_parameterized_reports.qmd           ← NEW from old Module 05
│   ├── 07_projects_themes_publishing.qmd      ← Themes/CSS from old Module 06
│   ├── quartobot_bonus.qmd                    ← Optional bonus
│   └── slides/                                ← revealjs decks (01–07)
│       └── niehs-theme.scss
│
├── instructor/
│   └── exercise_solutions.Rmd                 ← Reference solutions, students don't see
│
├── optional/
│   └── rmarkdown_capstone_homework.Rmd        ← Take-home R Markdown capstone
│
├── data/                                      ← (empty; for student uploads if needed)
└── images/                                    ← (drop niehs-logo.png here before delivery)
```

## Pre-workshop checklist

### 1 week before

- [ ] **Create a Posit Cloud workspace** ([posit.cloud](https://posit.cloud)) and a project from this folder. Pin it as the workshop template.
- [ ] **Render the entire project once** on the Posit Cloud workspace to make sure every notebook compiles and there are no missing packages. (See "Validation" below.)
- [ ] **Drop the NIEHS logo** at `images/niehs-logo.png` (referenced by every afternoon slide deck). A 200×200 transparent PNG is fine.
- [ ] **Test the firewall** if you plan to demo `quartobot` — it hits Crossref / PubMed / arXiv at render time. NIEHS federal firewalls may block. Mitigation: pre-resolve references and ship a cached `references.json` if needed.
- [ ] **Confirm Quarto version** ≥ 1.9 on Posit Cloud (`quarto --version` in a terminal). Quarto 1.8+ is the minimum for the publishing module's content; 1.9 was current stable as of March 2026.
- [ ] **Pre-register attendees** in the workspace if Posit Cloud's free tier doesn't fit (paid Posit Cloud Workspaces handle group enrollment).

### Day of

- [ ] Open the Posit Cloud project in the browser ~15 min before start to warm up the container.
- [ ] Have backup laptop ready in case projector / screen-sharing fails.
- [ ] Pre-load `index.qmd` rendered (use Posit Cloud's preview pane).

## Pre-workshop email to students

Suggested template:

> **Subject:** Tomorrow's workshop — please complete in advance
>
> Hi everyone,
>
> A few things to do before tomorrow's 9 AM workshop:
>
> 1. **Create a free [Posit Cloud](https://posit.cloud) account** if you don't have one. The free tier is enough for today.
> 2. **Confirm you can log in** at [posit.cloud](https://posit.cloud) and see the dashboard.
> 3. **(Optional) Create a free [GitHub](https://github.com) account** — useful for the publishing module but not required.
>
> You don't need to install anything on your laptop. Everything runs in your browser. We start at 9 AM sharp in **\[room\]**. Bring a laptop (any OS, any browser) and a notepad.
>
> See you tomorrow,
> \[Instructor name\]

## Instructor teaching notes — module by module

### Morning (R Markdown)

**00 Setup (5 min) —** Have everyone open `00_setup.qmd` and click **Render**. If anyone gets a package error, that's the first signal they didn't pre-install — point them at the package install command in the notebook and have them re-render.

**01 R Markdown basics (25 min) —** Live-demo: open `01_rmarkdown_basics.Rmd`, scroll through, knit. Then have students edit YAML (change author to their name), re-knit. Cover: YAML header, markdown text, clean-session reproducibility (this is the most important takeaway — many R users don't realize knit runs in a fresh R session).

**02 Code chunks + inline code (30 min) —** Walk through chunk options live. The inline code example with simulated PFOA biomarker data is the *aha* moment for many — emphasize that every number in the example paragraph is from R code. Exercise 2.2 (the BPA dynamic paragraph) is the one to make sure everyone completes.

### Break (15 min)

### Bridge (25 min)

The bridge module is intentionally compact and visual. It shows the four side-by-side differences between R Markdown and Quarto: file extension, YAML `output:` → `format:`, chunk options syntax, and how to run a conversion. Have students keep their existing `02_code_chunks.Rmd` open and look at the equivalent `.qmd` version side by side.

If anyone is panicking that everything they know is changing, this is the place to reassure them: **same R code, same `library()` calls, same packages, same outputs**. Only the document syntax changes.

### Afternoon (Quarto)

**Quarto 1 — first .qmd (30 min) —** Move fast. The bridge already covered the migration. This module focuses on what's *new* in Quarto: callouts, panel tabsets, expanded YAML. Have everyone create a new `.qmd` from scratch in Posit Cloud (**File → New File → Quarto Document**) and add a callout.

**Quarto 2 — code chunks + tables (60 min) —** This is the longest module. The tables content (`kable`, `kableExtra`, `DT`, `broom`) is migrated from the old Module 03 — same content, `.qmd` syntax. The R/Python tabset is worth demoing live if you have any Python users in the audience.

**Lunch (60 min) — at 12:10 PM.**

**Quarto 3 — figures (45 min) —** Migrated from the old Module 04. Heavy on `ggplot2`. The patchwork section is where most students learn something new. The plotly example reliably gets a "wow" — demo it live with a hover. The `fig.width` → `fig-width` naming gotcha is worth pausing on — it bites people copying R Markdown chunks into Quarto.

**Quarto 4 — equations, cross-refs, citations (45 min) —** The equations content is migrated from the old Module 05. NIEHS-relevant equations (Hill model, HQ, LADD) ground the abstract LaTeX in real toxicology/exposure work. Cross-references are where Quarto genuinely improves on R Markdown (no `bookdown` dependency) — emphasize this. The citation section is short because it works the same as R Markdown.

**Break (15 min)**

**Quarto 5 — revealjs (30 min) —** The slide deck content is one of the most fun parts to teach because students see immediate results. Walk through the slides themselves as the demo — these slides are revealjs `.qmd` files.

**Quarto 6 — parameterized reports (25 min) —** This is the highest-ROI module for anyone doing recurring NIEHS reports. The PFOA/PFOS-by-site batch example shows what 12 reports from one source looks like. Even if students don't write parameterized reports tomorrow, plant the seed.

**Quarto 7 — projects + themes + publishing (20 min) —** Pace fast. Three sub-topics ≈ 7 min each. Projects → themes → publishing. The big point of publishing: **`quarto render` and email the HTML** is often enough for internal NIEHS work; don't oversell GitHub Pages / Quarto Pub if the audience is on a federal network with restricted external publishing.

**Capstone (25 min) —** Hand off — "build something of your own from scratch." Walk around, troubleshoot, encourage. The capstone template offers `biomarker_data`, `airquality`, `penguins`, or bring-your-own.

**Wrap-up + next steps (25 min) —** Walk through `next_steps.qmd` live: local Quarto install for Mac and Windows, VS Code / Positron / RStudio comparison, when to come back to the workshop materials. Hand out (or email post-workshop) the optional R Markdown capstone homework — `optional/rmarkdown_capstone_homework.Rmd`.

## What this workshop does NOT cover

Be explicit with students up-front about scope. We don't cover:

- **Shiny + Quarto** — interactive documents backed by a live R server.
- **Quarto Dashboards** — fluid-layout interactive dashboards (Quarto 1.4+).
- **Quarto Extensions** — community shortcodes, filters, custom formats.
- **Custom Pandoc filters / Lua filters** — when you need to bend the rendering pipeline.
- **Quarto Manuscripts deep dive** — the project type is mentioned but not used.
- **Deep Word/PDF customization** — `reference.docx` files, custom LaTeX templates.
- **Targets / drake integration** — pipelining `.qmd` renders inside larger reproducible workflows.
- **Bookdown migration** — for users who have multi-chapter `bookdown` projects, Quarto books are similar but the migration has its own quirks.

All of the above are linked from `next_steps.qmd` for follow-up.

## Customizing for a non-NIEHS audience

If you want to deliver this workshop at another institution:

1. **Search-and-replace `NIEHS`** across the project — most occurrences are in titles, footers, and prose framing.
2. **Change the brand color** `#205C40` (NIEHS forest green) in:
   - `styles.scss`
   - `afternoon_quarto/slides/niehs-theme.scss`
   - Inline references in slide decks
3. **Replace `biomarker_data`** with a domain-appropriate dataset. The dataset definition appears in:
   - `afternoon_quarto/02_code_chunks_and_tables.qmd` (setup chunk — the canonical definition)
   - `afternoon_quarto/03_figures_and_visualizations.qmd`
   - `afternoon_quarto/04_equations_crossrefs_citations.qmd`
   - `afternoon_quarto/01_first_document.qmd` (mentioned)
   - `capstone.qmd` (as the primary default option)
4. **Swap the NIEHS-specific equations** (Hill model, HQ, LADD) in `04_equations_crossrefs_citations.qmd` for domain-relevant formulas — biostatistics regression equations, pharmacokinetic equations, whatever fits.
5. **Update the logo** at `images/niehs-logo.png`.

## Quartobot caveat (if you use it)

`quartobot_bonus.qmd` introduces Sean Davis's [`quartobot`](https://seandavi.github.io/quartobot/) — a community tool that lets you write `@doi:10.21105/joss.01686` directly in prose, with no hand-curated BibTeX entry needed. It's marked as optional / bonus for three reasons:

1. **Maturity** — community-maintained, not Quarto-core. APIs may change.
2. **Network dependency** — hits Crossref/PubMed/arXiv at render time. NIEHS federal firewalls may block these calls and your render fails.
3. **Mitigation overhead** — you can pre-resolve references and ship a cached `references.json`, but that adds workflow complexity.

If you want to teach it, **test it on a Posit Cloud instance behind your institution's firewall before the workshop**.

## Validation before delivery

Before running the workshop, render every notebook end-to-end. From the project root on Posit Cloud:

```bash
quarto render
```

This compiles every `.qmd` file in the project (the morning `.Rmd` files are excluded via the `_quarto.yml` `render:` block; render those separately with R Markdown's Knit button to confirm).

Common issues to watch for:

- **Missing packages** — install all listed in `00_setup.qmd` before rendering.
- **Cross-reference resolution** — if `@fig-foo` renders as `?@fig-foo`, the label is missing or misspelled.
- **Bibliography misses** — if `[@key]` renders as `[@key]` (un-resolved), the entry is missing from `references.bib`.
- **Image paths** — slide decks reference `../../images/niehs-logo.png`; make sure that file exists.

I did NOT validate by rendering in this build because the sandbox doesn't have Quarto CLI available. **Render the project on Posit Cloud before delivery and fix anything that breaks.**

## Author's caveats

A few things I want to flag honestly:

- **The morning slides are ioslides; the afternoon slides are revealjs.** This is intentional (Burke's existing slides are ioslides; revealjs is Quarto-native) but the visual style will shift after the bridge module. Mention this to students once and move on — it's not worth re-doing the morning slides.
- **The R Markdown capstone (`optional/rmarkdown_capstone_homework.Rmd`) was originally a 20-min in-workshop exercise.** It's been re-purposed as homework with no other modification. The framing in its own README still assumes in-workshop delivery. Either edit it or just brief students on the new framing when handing it out.
- **`biomarker_data` is the canonical dataset for the Quarto afternoon**, but the airquality and penguins datasets remain as alternatives in the capstone. If you want a fully unified dataset experience, edit the capstone to drop those alternatives.
- **Posit Cloud free-tier hours are limited** (~25 hr/month at the free tier as of early 2026; verify current pricing at [posit.cloud/plans](https://posit.cloud/plans)). For a single day of workshop, this is fine for everyone, but heavy follow-up use may exhaust the tier.

## License

CC BY 4.0 — reuse with attribution. The R Markdown materials (modules 01, 02, capstone, exercise solutions, quick reference) are by R. Burke Squires. The Quarto materials are co-authored by Burke and Claude (Anthropic).

## Contact

R. Burke Squires — burke.squires@nih.gov
