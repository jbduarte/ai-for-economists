# AI for Economists — Workshop Materials

## Project Purpose
45-minute faculty workshop at Nova SBE (Economics) on Claude Code and AI capabilities for research and teaching.

## Key Source Materials

### Primary References
1. **Boris Cherny** (Creator of Claude Code)
   - Site: https://howborisusesclaudecode.com
   - Key topics: parallel execution with worktrees, plan mode, CLAUDE.md best practices, skills/slash commands, subagents, hooks, MCP integrations, verification, custom agents
   - Local skill reference: `~/Library/CloudStorage/Dropbox/Claude_skills/boris/SKILL.md`

2. **Alex Imas** (Booth School of Business, University of Chicago)
   - Behavioral economist using AI extensively in research workflow
   - Active on X (@aleximas) sharing AI-for-research workflows
   - Focus: how AI transforms the research production function for economists

3. **Anthropic Official Documentation**
   - Claude Code docs: https://docs.anthropic.com/en/docs/claude-code
   - Claude Agent SDK: https://github.com/anthropics/claude-code/tree/main/packages/agent
   - Custom agents: `.claude/agents/*.md`
   - Custom skills: `.claude/commands/*.md`

### Supplementary References
4. **Sendhil Mullainathan** — "Machines and Minds" research agenda; AI as co-researcher
5. **Susan Athey** — ML/AI methods for causal inference; policy evaluation
6. **Anton Korinek** — "Generative AI for Economic Research" (working paper series)

## Presentation Architecture

### Format: reveal.js (HTML)
- File: `slides/index.html`
- Theme: custom dark theme with Nova SBE branding accents
- Serves via GitHub Pages or local file

### Slide Outline (45 minutes)

#### Part 1: The AI Moment (5 min)
- What frontier models can do today (Claude Opus 4.6)
- Why economists should care: research + teaching transformation
- The "compound returns" of investing in AI workflow

#### Part 2: Claude Code — Your AI Research Partner (10 min)
- What is Claude Code (CLI tool, agentic, tool-using)
- Live demo: reading a paper, writing code, analyzing data
- CLAUDE.md: teaching your AI about your project
- Why git matters: version control as the foundation

#### Part 3: Skills — Reusable AI Workflows (10 min)
- What is a skill (slash command)
- Anatomy of a skill file (frontmatter + instructions)
- Live example: building a `/lit-review` skill from scratch
- Real examples from the presenter's toolkit (30+ skills)

#### Part 4: Agents — Autonomous AI Workers (10 min)
- What is an agent (subagent with specific tools/permissions)
- Agent SDK architecture
- Live example: building a data-cleaning agent
- Swarm of agents: worktree parallelism explained
- Why git worktrees are crucial for parallel AI work

#### Part 5: Putting It All Together (7 min)
- The economist's AI stack: Claude Code + skills + agents + MCP
- Research workflow: from idea to paper with AI augmentation
- Teaching applications: automated grading, exercise generation
- Getting started: installation and first steps

#### Q&A (3 min)

## Code Examples to Include
- Simple skill file (complete, annotated)
- Simple agent file (complete, annotated)
- Worktree commands for parallel execution
- CLAUDE.md template for an economics research project
- Hook example for auto-formatting

## Style Guidelines
- Use concrete economics examples (IV estimation, DSGE, micro data)
- Show real terminal output / screenshots where possible
- Keep code examples short and self-contained
- Emphasize the "why" before the "how"
