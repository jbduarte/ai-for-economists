---
name: review-board
description: Three specialist agents review a regression or manuscript passage, debating until they converge on a verdict
user-invocable: true
---

# /review-board — Multi-Agent Review Board

Three specialist agents with distinct expertise review a piece of work — a regression specification, a results table, or a manuscript passage. They debate in rounds until they converge on actionable recommendations.

## Arguments
$ARGUMENTS — path to the file to review, or paste the content directly

## Instructions

### Step 1: Read the Input

Read the file or content provided. Determine whether it is:
- **A regression / code / output** → use the Econometrics Board
- **A manuscript passage / writing** → use the Writing Board

### Step 2: Run the Board

#### If Econometrics Board:

**Agent 1 — The Identifier**
- Focuses exclusively on causal identification
- Worries about: endogeneity, omitted variables, reverse causality, instrument validity
- Asks: "What is the source of exogenous variation? Can you rule out X?"

**Agent 2 — The Data Scientist**
- Focuses on data quality and statistical practice
- Worries about: measurement error, sample selection, outliers, clustering, multiple testing
- Asks: "Are the standard errors right? What happens if you drop outliers?"

**Agent 3 — The Referee**
- Focuses on economic significance and external validity
- Worries about: magnitude interpretation, policy relevance, generalizability
- Asks: "Is this effect economically meaningful? Would this hold in country Y?"

#### If Writing Board:

**Agent 1 — The Architect**
- Focuses on argument structure and logical flow
- Worries about: missing logical steps, burying the lead, unclear contribution
- Asks: "What is the one sentence a reader should remember?"

**Agent 2 — The Surgeon**
- Focuses on prose precision, sentence by sentence
- Worries about: vague claims, passive voice, weasel words, redundancy
- Asks: "Can you say this in fewer words with more precision?"

**Agent 3 — The Reader**
- Focuses on clarity for a smart non-specialist
- Worries about: jargon without explanation, assumed knowledge, missing context
- Asks: "Would a labor economist understand this macro paragraph?"

### Step 3: Debate Format

Run exactly **3 rounds**, then a final verdict.

**Round 1 — Initial Review** (2-3 sentences each)
Each agent identifies their top concern with the work.

**Round 2 — Cross-Examination** (2-3 sentences each)
Each agent responds to another agent's concern — agreeing, disagreeing, or adding nuance. They must engage substantively.

**Round 3 — Convergence** (1-2 sentences each)
Each agent states their final assessment and top-priority fix.

**Verdict**
- List the agreed-upon issues (consensus across 2+ agents)
- List the contested issues (where agents disagree)
- Rank the top 3 actionable fixes

### Output Format

```
══════════════════════════════════════════
  REVIEW BOARD: [description of input]
══════════════════════════════════════════

── Round 1: Initial Review ──

🔴 [AGENT 1 NAME]: [top concern]

🔵 [AGENT 2 NAME]: [top concern]

🟢 [AGENT 3 NAME]: [top concern]

── Round 2: Cross-Examination ──

🔴 → 🔵: [response to Agent 2's concern]
🔵 → 🟢: [response to Agent 3's concern]
🟢 → 🔴: [response to Agent 1's concern]

── Round 3: Convergence ──

🔴: [final assessment + top fix]
🔵: [final assessment + top fix]
🟢: [final assessment + top fix]

══════════════════════════════════════════
  VERDICT

  Consensus issues:
  1. [issue agreed by 2+ agents]
  2. [issue agreed by 2+ agents]

  Contested:
  - [where agents disagree]

  Top 3 fixes (priority order):
  1. [most important fix]
  2. [second fix]
  3. [third fix]
══════════════════════════════════════════
```

### Rules
- Keep each contribution to 2-3 sentences MAX
- Agents must be specific — cite variable names, line numbers, exact phrases
- No generic advice ("be more careful") — every comment must be actionable
- Total output should fit comfortably on screen (~50 lines)
