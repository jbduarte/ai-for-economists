# [Project Name] — CLAUDE.md

## Project Overview
[One paragraph: what question are you answering and why it matters]

## Data
- Main dataset: `data/raw/[filename]`
- Additional sources: [list]
- Sample: [units, period, frequency]
- Key variables:
  - Y: [outcome variable] (`var_name`)
  - X: [treatment/regressor] (`var_name`)
  - Z: [instrument, if applicable] (`var_name`)

## Identification Strategy
[Brief description: IV, DiD, RDD, RCT, structural, etc.]
[Key assumptions and why they hold]

## Code Conventions
- Primary language: [Stata 18 / R 4.x / Python 3.12]
- Data cleaning: `src/clean/`
- Analysis: `src/analysis/`
- Tables: `tables/` (generated via [estout/stargazer/etc.])
- Figures: `figures/` (generated via [ggplot/matplotlib/etc.])
- Always [cluster SEs at X level / use HAC / etc.]
- Use [reghdfe/fixest/linearmodels] for fixed effects

## File Structure
```
├── data/
│   ├── raw/          # Never modify these files
│   ├── clean/        # Cleaned datasets
│   └── codebook.md   # Variable definitions
├── src/
│   ├── clean/        # Data preparation scripts
│   ├── analysis/     # Main estimation
│   └── robustness/   # Robustness checks
├── tables/           # LaTeX tables
├── figures/          # PDF/PNG figures
├── paper/            # LaTeX manuscript
└── notes/            # Research notes, lit reviews
```

## Important Rules
- Never overwrite raw data
- All regressions must report clustered SEs
- Tables must be publication-ready (no raw Stata output)
- Document every sample restriction in code comments
- Use relative paths in all scripts
