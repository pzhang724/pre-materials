# pre-materials — Claude Code Context

## Environment Setup

Before rendering presentations, verify both Quarto and LaTeX are installed:

```bash
quarto --version
xelatex --version
```

**Install Quarto** (Ubuntu/Debian, if missing):

```bash
curl -fsSL https://github.com/quarto-dev/quarto-cli/releases/download/v1.6.42/quarto-1.6.42-linux-amd64.deb -o /tmp/quarto.deb
sudo dpkg -i /tmp/quarto.deb
```

**Install LaTeX** (Ubuntu/Debian, required for PDF/beamer output, if missing):

```bash
sudo apt-get install -y texlive-latex-base texlive-fonts-recommended texlive-latex-extra texlive-xetex
```

Quarto 1.6.42 is the tested version for this repo. After installing, run `quarto check` to verify.

This repo stores external presentation slides built with [Quarto](https://quarto.org/).

## Folder & File Naming Convention

Each talk lives in its own folder following this pattern:

| Item | Convention |
|------|-----------|
| Folder | `YYYY-MM-DD-[Conference Name]/` |
| Source file | `Slides-YYYY-MM-DD-[Conference Name].qmd` |
| Output (PDF) | `Slides-YYYY-MM-DD-[Conference Name].pdf` (in folder root) |

Use hyphens in the conference name (no spaces). There is no separate output directory — the PDF sits at the root of the presentation folder alongside the `.qmd`.

## Folder Structure Per Presentation

```
YYYY-MM-DD-Conference/
├── _quarto.yml                          # Format config (beamer/metropolis)
├── Slides-YYYY-MM-DD-Conference.qmd    # Slide content
├── Slides-YYYY-MM-DD-Conference.pdf    # Rendered output
└── raw/                                # Source materials
    ├── figures/                        # Charts, images, diagrams
    └── data/                           # Datasets used in slides
```

## Output Format

PDF only (Beamer with Metropolis theme, 16:9). Configured in `_quarto.yml`.  
Do **not** set `format:` in the `.qmd` front matter.

## Template

`template/` is the canonical starting point for every new presentation.  
Copy it and rename the folder and `.qmd` file before editing:

```bash
cp -r template/ 2026-06-10-MyConference
mv 2026-06-10-MyConference/Slides-YYYY-MM-DD-Conference.qmd \
   2026-06-10-MyConference/Slides-2026-06-10-MyConference.qmd
```

Then update the title, subtitle, date, and author block in the `.qmd` front matter.

## Quarto Commands

```bash
# Render a single presentation
quarto render YYYY-MM-DD-Conference/

# Preview (note: PDF preview opens in system viewer)
quarto preview YYYY-MM-DD-Conference/

# Render all presentations
for d in [0-9][0-9][0-9][0-9]-*/; do quarto render "$d"; done
```

## Key Files Per Presentation

| File | Purpose |
|------|---------|
| `_quarto.yml` | Beamer/Metropolis format settings |
| `Slides-YYYY-MM-DD-Conference.qmd` | Slide content in Quarto Markdown |
| `raw/` | Source materials (figures, data) |
