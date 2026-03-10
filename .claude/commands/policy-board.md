---
name: policy-board
description: Simulate a board of 3 economist agents debating a policy question until they converge on a recommendation
user-invocable: true
---

# /policy-board — Multi-Agent Policy Debate

Simulate a board of three economist agents with distinct perspectives. They debate a policy question in rounds until they reach a joint recommendation.

## Arguments
$ARGUMENTS — the policy question or decision to debate

## Instructions

### The Board

Define three agents with clashing perspectives:

**Agent 1 — The Hawk** (Fiscal/Monetary Conservative)
- Prioritizes price stability, fiscal discipline, moral hazard concerns
- Skeptical of government intervention, worries about long-run costs
- Cites: Friedman, Lucas, Sargent, Prescott

**Agent 2 — The Dove** (Keynesian/Interventionist)
- Prioritizes employment, output gaps, demand management
- Favors active policy, worries about hysteresis and scarring
- Cites: Keynes, Blanchard, Summers, Yellen

**Agent 3 — The Owl** (Evidence-Based Pragmatist)
- Prioritizes empirical evidence over ideology
- Pushes both sides on magnitudes, identification, external validity
- Cites: Nakamura-Steinsson, Ramey, Romer-Romer, Mian-Sufi

### Execution

Run exactly **3 rounds** of debate, then a final vote.

**Round 1 — Opening Positions** (2-3 sentences each)
Each agent states their position on the question with one key argument.

**Round 2 — Challenge & Respond** (2-3 sentences each)
Each agent responds to the strongest argument from an opposing agent. They must engage with the substance, not just restate their view.

**Round 3 — Revised Positions** (2-3 sentences each)
Each agent states their updated position, noting what (if anything) changed their mind. They must acknowledge at least one valid point from another agent.

**Final Vote**
Each agent votes: YES, NO, or CONDITIONAL (with one condition).
Summarize the board's recommendation in one sentence.

### Output Format

Present the debate as a clean, readable transcript:

```
══════════════════════════════════════════
  POLICY BOARD: [Question]
══════════════════════════════════════════

── Round 1: Opening Positions ──

🔴 HAWK: [position]

🔵 DOVE: [position]

🟢 OWL: [position]

── Round 2: Challenge & Respond ──

🔴 HAWK → DOVE: [challenge + response]

🔵 DOVE → HAWK: [challenge + response]

🟢 OWL → BOTH: [evidence-based pushback]

── Round 3: Revised Positions ──

🔴 HAWK: [updated position]

🔵 DOVE: [updated position]

🟢 OWL: [updated position]

══════════════════════════════════════════
  VOTE
  🔴 HAWK: [YES/NO/CONDITIONAL]
  🔵 DOVE: [YES/NO/CONDITIONAL]
  🟢 OWL: [YES/NO/CONDITIONAL]

  RECOMMENDATION: [one sentence summary]
══════════════════════════════════════════
```

### Rules
- Keep each agent's contribution to 2-3 sentences MAX per round
- Total output should fit in one screen (~40 lines)
- Agents must genuinely engage — no strawmanning
- The Owl must cite at least one real empirical paper
- The debate should feel like a real faculty meeting, not a textbook
