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

Each talk lives in its own folder and source file following this pattern:

| Item | Convention |
|------|-----------|
| Folder | `YYYY-MM-DD-[Conference Name]/` |
| Source file | `Slides-YYYY-MM-DD-[Conference Name].qmd` |
| Output (HTML) | `_output/Slides-YYYY-MM-DD-[Conference Name].html` |
| Output (PDF) | `_output/Slides-YYYY-MM-DD-[Conference Name].pdf` |

Use hyphens in the conference name (no spaces).

## Output Formats

Every presentation renders **both HTML (RevealJS) and PDF (Beamer)** by default.  
Formats are configured in `_quarto.yml` — do not set `format:` in the `.qmd` front matter.

## Template

`template/` is the canonical starting point for every new presentation.  
Copy it and rename the folder and `.qmd` file before editing:

```bash
cp -r template/ 2026-06-10-MyConference
mv 2026-06-10-MyConference/Slides-YYYY-MM-DD-Conference.qmd \
   2026-06-10-MyConference/Slides-2026-06-10-MyConference.qmd
```

Then update the title, subtitle, date, and footer in `_quarto.yml`.

## Quarto Commands

```bash
# Preview a single presentation (live reload)
quarto preview YYYY-MM-DD-Conference/

# Render a single presentation (produces HTML + PDF)
quarto render YYYY-MM-DD-Conference/

# Render all presentations
for d in [0-9][0-9][0-9][0-9]-*/; do quarto render "$d"; done
```

## Key Files Per Presentation

| File | Purpose |
|------|---------|
| `_quarto.yml` | Project settings, both format configs, footer, dimensions |
| `Slides-YYYY-MM-DD-Conference.qmd` | Slide content in Quarto Markdown |
