# AI for Economists — Workshop Materials

## Project Purpose
45-minute faculty workshop at Nova SBE (Economics) on Claude Code and AI capabilities for research and teaching.

## Key Source Materials

### Primary References

1. **Boris Cherny** (Creator / Head of Claude Code, Anthropic)
   - Guide (43 tips): https://howborisusesclaudecode.com
   - X thread (setup): https://x.com/bcherny/status/2007179832300581177
   - X thread (team tips): https://x.com/bcherny/status/2017742741636321619
   - Lenny's Newsletter interview: https://www.lennysnewsletter.com/p/head-of-claude-code-what-happens
   - Pragmatic Engineer deep dive: https://newsletter.pragmaticengineer.com/p/building-claude-code-with-boris-cherny
   - Key stats: ships 20-30 PRs/day, runs 5+ parallel sessions, Claude Code = 4% of public GitHub commits
   - Local skill reference: `~/Library/CloudStorage/Dropbox/Claude_skills/boris/SKILL.md`

2. **Alex Imas** (Goetz Professor, Chicago Booth — visiting Princeton 2025-26)
   - Website: https://aleximas.com
   - X/Twitter: @alexolegimas
   - Substack ("Ghosts of Electricity"): https://aleximas.substack.com
   - Key X post ("Claude Code is insane"): https://x.com/alexolegimas/status/2006914766401380703
   - Paper: "Agentic Interactions" (with Lee & Misra): https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5875162
   - Paper: "Can a Transformer Learn Economic Relationships?" (with Gupta)
   - Substack: "What is the impact of AI on productivity?"
   - Substack: "Who Uses AI (and How)?" (with Shukla)
   - Key concept: "machine fluency" as new source of inequality
   - Warning: AI can one-shot papers that look good but are bad — verification critical

3. **Anthropic Official Documentation**
   - Claude Code overview: https://code.claude.com/docs/en/overview
   - Skills docs: https://code.claude.com/docs/en/skills
   - Sub-agents docs: https://code.claude.com/docs/en/sub-agents
   - Memory (CLAUDE.md): https://code.claude.com/docs/en/memory
   - Hooks: https://code.claude.com/docs/en/hooks
   - Common workflows (worktrees): https://code.claude.com/docs/en/common-workflows
   - Agent teams: https://code.claude.com/docs/en/agent-teams
   - Plugins: https://code.claude.com/docs/en/plugins
   - Agent SDK overview: https://platform.claude.com/docs/en/agent-sdk/overview
   - Agent SDK Python: https://github.com/anthropics/claude-agent-sdk-python
   - Agent SDK demos: https://github.com/anthropics/claude-agent-sdk-demos
   - Claude Code repo (75.9k stars): https://github.com/anthropics/claude-code

### Supplementary References
4. **Anton Korinek** — "Generative AI for Economic Research" (working paper series)
5. **Sendhil Mullainathan** — "Machines and Minds" research agenda
6. **Grant McDermott** — quarto-revealjs-clean theme (economist-built): https://github.com/grantmcdermott/quarto-revealjs-clean

## Presentation Architecture

### Format: reveal.js (HTML)
- File: `slides/index.html`
- Theme: custom dark theme with gradient accents, terminal mockups, card layouts
- CDN-based — single HTML file works in any browser
- PDF export: `npx decktape reveal slides/index.html slides.pdf`
- Alternative: open `slides/index.html?print-pdf` in Chrome → Print

### Slide Structure (45 minutes)

| Part | Topic | Time | Key Content |
|------|-------|------|-------------|
| 01 | The AI Moment | 5 min | Capabilities, Imas quote, production function shift, warning |
| 02 | Claude Code | 10 min | What it is, CLAUDE.md, why git, getting started |
| 03 | Skills | 10 min | Anatomy, guided build, 30+ real examples |
| 04 | Agents | 10 min | Skills vs agents, anatomy, subagents, worktrees, swarms |
| 05 | Putting It Together | 7 min | Stack diagram, research workflow, teaching apps |
| — | Q&A | 3 min | |

## Code Examples Included
- `examples/skills/robustness-check.md` — complete annotated skill
- `examples/agents/data-validator.md` — complete annotated agent
- `examples/claude-md-templates/research-project.md` — starter CLAUDE.md template

## Style Guidelines
- Use concrete economics examples (IV estimation, DSGE, micro data)
- Show terminal mockups with realistic commands
- Keep code examples short and self-contained
- Emphasize the "why" before the "how"
- Dark theme with code-focused aesthetics
