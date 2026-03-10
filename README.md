# AI for Economists

Workshop materials for the Nova SBE faculty session on Claude Code and AI capabilities for economics research and teaching.

## Viewing the Slides

### Option 1: Open locally
```bash
open slides/index.html
```
The slides load reveal.js from a CDN — just open in any browser.

### Option 2: GitHub Pages
Once enabled, available at: `https://jbduarte.github.io/ai-for-economists/slides/`

### Option 3: Export to PDF
```bash
# Using decktape (best quality)
npx decktape reveal slides/index.html slides.pdf

# Or: open slides/index.html?print-pdf in Chrome → Print → Save as PDF
```

## Navigation
- **Arrow keys**: navigate slides
- **Space**: next slide
- **Esc**: overview mode
- **S**: speaker notes
- **F**: fullscreen

## Contents

```
├── slides/index.html                    # Main presentation (reveal.js)
├── examples/
│   ├── skills/robustness-check.md       # Example skill file
│   ├── agents/data-validator.md         # Example agent file
│   └── claude-md-templates/             # CLAUDE.md template for research
├── CLAUDE.md                            # Project instructions for Claude
└── README.md                            # This file
```

## Key References
- [How Boris Uses Claude Code](https://howborisusesclaudecode.com) — Boris Cherny (creator of Claude Code)
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Claude Agent SDK](https://github.com/anthropics/claude-code)
