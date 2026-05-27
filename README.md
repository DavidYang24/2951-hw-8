# What factors have the greatest impact on the performance in the Premier League, UK?

## Project Overview

This project analyzes factors associated with team performance in the English Premier League from the 2019/2020 through 2024/2025 seasons. We examine two main areas: disciplinary behavior, measured through yellow and red cards, and financial/squad-related factors, including transfer spending, squad value, and average squad age.

The main research question is:

**What factors have the greatest impact on team performance in the Premier League?**

## Data Sources

The data used in this project came from two main sources:

-   **FBref**: team and player performance data, including points, league ranking, player positions, yellow cards, and red cards.
-   **Transfermarkt**: financial and squad-related data, including transfer spending, transfer income, net spending, squad value, and average squad age.

FBref data was manually exported as CSV/Excel files because direct scraping was not available. Transfermarkt data was used for club financial and squad value information.

## Repository Structure

``` text
.
├── report.qmd                 # Main final report
├── appendices.qmd             # Data cleaning appendix
├── data/
│   ├── Question 2/            # Raw and cleaned data for spending/squad analysis
│   ├── Question 3/            # Raw FBref team/player data for discipline analysis
│   ├── Player_Stats/          # Raw player-season Excel files
│   └── analysis/              # Analysis-ready datasets written by appendices.qmd
├── renv.lock                  # R package environment lockfile
├── README.md                  # Project overview and reproduction instructions
└── .Rprofile                  # renv activation file, if included
```

## Main Analysis Files

-   `report.qmd`: Contains the main project report, including research question, data description, analysis, significance evaluation, interpretations, and conclusion.

-   `appendices.qmd`: Contains the data cleaning process and writes the analysis-ready datasets to CSV files.

-   `renv.lock`: Records the R package versions used in the project so the computational environment can be restored.

### Main Datasets

The appendix creates the final datasets used in the report:

-   `team_season_data.csv`: Team-season dataset combining performance, transfer spending, squad value, average squad age, and disciplinary totals.

-   `discipline_by_position.csv`: Position-level disciplinary dataset with yellow and red cards by team, season, and position.

## How to Reproduce the Project

1.  Open the project in RStudio or Positron.

2.  Restore the R package environment:

```{r}
renv::restore()
```

3.  Render the appendix first to generate the analysis-ready datasets:

```{r}
quarto::quarto_render("appendices.qmd")
```

4.  Render the main report:

```{r}
quarto::quarto_render("report.qmd")
```

The rendered appendix should write the cleaned datasets to the `data/analysis/` folder.

## Required R Packages

The main packages used in this project include:

```{r}
infer
tidyverse
httr2
jsonlite
readxl
stringr
readr
purrr
scales
broom
gt
```

Package versions are tracked in `renv.lock`.