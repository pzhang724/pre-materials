# pre-materials — Claude Code Context

## Environment Setup

Before rendering presentations, verify Quarto is installed:

```bash
quarto --version
```

If not installed (Ubuntu/Debian):

```bash
curl -fsSL https://github.com/quarto-dev/quarto-cli/releases/download/v1.6.42/quarto-1.6.42-linux-amd64.deb -o /tmp/quarto.deb
sudo dpkg -i /tmp/quarto.deb
```

Quarto 1.6.42 is the tested version for this repo. After installing, run `quarto check` to verify.

This repo stores external presentation slides built with [Quarto](https://quarto.org/).

## Folder Convention

Each talk lives in `YYYY-MM-DD-[Conference Name]/`.  
Use hyphens in the conference name (no spaces).

## Template

`template/` is the canonical starting point for every new presentation.  
Copy it and rename the folder before editing.

## Quarto Commands

```bash
# Preview a single presentation (live reload)
quarto preview YYYY-MM-DD-Conference/

# Render a single presentation
quarto render YYYY-MM-DD-Conference/

# Render all presentations
for d in [0-9][0-9][0-9][0-9]-*/; do quarto render "$d"; done
```

## Slide Format

Default format is **RevealJS** (HTML). Change `format:` in `_quarto.yml` to `beamer` (PDF) or `pptx` (PowerPoint) as needed.

## Key Files Per Presentation

| File | Purpose |
|------|---------|
| `_quarto.yml` | Project settings, theme, footer, dimensions |
| `index.qmd` | Slide content in Quarto Markdown |
