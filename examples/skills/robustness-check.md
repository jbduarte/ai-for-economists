---
name: robustness-check
description: Generate comprehensive robustness checks for IV regressions in Stata
user-invocable: true
---

# /robustness-check — IV Robustness Suite

Generate a complete set of robustness checks for an instrumental variables regression.

## Arguments
$ARGUMENTS — path to the main Stata .do file containing the IV regression

## Instructions

### Step 1: Read the Specification
Read the provided .do file. Identify:
- Dependent variable
- Endogenous variable(s)
- Instrument(s)
- Control variables
- Fixed effects
- Clustering level
- Sample restrictions

### Step 2: Generate Robustness Checks

Create a new .do file `robustness/robustness_iv.do` with:

1. **First-stage diagnostics**
   - F-statistic (Kleibergen-Paap if clustered)
   - Anderson-Rubin confidence sets
   - Effective F-statistic (Olea-Pflueger)

2. **Alternative instruments**
   - Drop each instrument one at a time (if overidentified)
   - Lag structure variations

3. **Subsample analysis**
   - Drop each decile of the instrument
   - Pre/post period splits
   - Geographic subsamples

4. **Control sensitivity**
   - Oster (2019) bounds for selection on unobservables
   - Sequential addition of controls
   - Altonji-Elder-Taber ratio

5. **Inference alternatives**
   - Wild bootstrap (if few clusters)
   - Randomization inference
   - Conley standard errors (if spatial)

6. **Placebo tests**
   - Placebo outcomes (pre-determined variables)
   - Permutation of instrument across units

### Step 3: Output
- Save all results using `estout` to `tables/robustness/`
- Create a summary table of coefficients across all specifications
- Flag any specification where results differ qualitatively
