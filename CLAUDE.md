# AI for Economists — Workshop Materials

## Project Purpose
45-minute interactive faculty workshop at Nova SBE (Economics). Hands-on from the first slide. Joao's own experiences and toolkit.

## Presentation Format
- **Format**: reveal.js (HTML) — `slides/index.html`
- **Style**: dark theme, terminal mockups, code blocks, card grids
- **Approach**: interactive — live demos marked with [LIVE] tags throughout
- **PDF export**: `npx decktape reveal slides/index.html slides.pdf`

## Workshop Structure (45 min — PhD audience)

Slide deck `slides/index.html` now has 10 sections plus opening/closing. Principles-first pedagogy: PhD students must internalize the *why* (compound learning, critic/fixer separation, honesty rule, citation integrity as tooling) before the *what* (slash commands, skills, agents).

| Section | Slides | Focus |
|---------|--------|-------|
| **Title + Access** | 2 | Claude Pro/Max setup, one-command install |
| **01 Claude Code** | 5 | Agentic AI, CLAUDE.md, git, MCP |
| **02 Memory & Plan Mode** | 6 | 3-layer memory, learning loop, "prompt engineering is dead" |
| **03 Skills** | 5 | What/how/anatomy, skill-creator meta-skill |
| **04 Agents** | 6 | Skills vs agents, subagents, auto-agents, teams |
| **05 Worktrees** | 3 | Parallel isolation, Boris Cherny quote |
| **06 Integrations** [NEW] | 5 | Git/Overleaf/Obsidian/Zotero — principles, not plumbing |
| **07 Principles & Guardrails** [NEW] | 7 | Compound learning, critic/fixer, honesty, durable state, Markus Academy, risks |
| **08 Built-in Power Tools** | 6 | /init, /memory, /batch, /simplify, hooks, plugins |
| **09 My Workflow** | 10 | Full picture, skills map, pipeline, stress-test loop, learning modes, when-to-use-what |
| **10 Live Demos** | 8 | Data→table, build skill, polish, build agent, review-board, teaching app |
| **Closing** | 2 | Key takeaways, Q&A |

### Live demos (run from this repo)
- `/polish` — use `.claude/commands/polish.md`
- `/review-board` — use `.claude/commands/review-board.md`
- Data→LaTeX table — `data/country_gdp_panel.csv`
- Build skill — create `.claude/commands/country-report.md` live
- Build agent — reference `examples/agents/data-validator.md`
- Solow app — one prompt, Chart.js single file

### External reference (cited on slide 07.5)
- Goldsmith-Pinkham, Markus Academy, "Claude Code for Applied Economists" (29 Mar 2026): https://markusacademy.substack.com/p/claude-code-for-applied-economists

## Key References
- Boris Cherny guide: https://howborisusesclaudecode.com
- Claude Code docs: https://code.claude.com/docs/en/overview
- Skills: https://code.claude.com/docs/en/skills
- Agents: https://code.claude.com/docs/en/sub-agents
- Worktrees: https://code.claude.com/docs/en/common-workflows

## Joao's Skill Inventory (30+ skills across categories)
- **Productivity**: /done, /ai-weekly, /prompt
- **Writing**: /polish, /intro-abstract-writer, /section-architect, /paper-architect, /referee-response, /devils-advocate, /manuscript-review, /ai-audit, /precision-auditor, /lucas-carvalho-style
- **Analysis**: /stata-regression, /r-econometrics, /python-panel-data, /local-projections-r, /local-projections-stata, /latex-tables, /econ-visualization
- **Data**: /stata-data-cleaning, /api-data-fetcher
- **Literature**: /lit-review-assistant, /research-ideation
- **Presentations**: /beamer-presentation
- **Workflow**: /worktree-planner, /paper-architect, /section-architect, /review-plan
- **Other**: /social-post, /youtube-prep, /pdf-search, /copy
