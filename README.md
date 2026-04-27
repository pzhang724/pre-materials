# pre-materials

External presentation materials managed with [Quarto](https://quarto.org/).

## Folder Convention

Each presentation lives in its own folder named:

```
YYYY-MM-DD-[Conference Name]/
```

**Examples:**
```
2026-04-27-UseR2026/
2026-09-15-PositConf/
2025-11-03-PyData/
```

## Repository Structure

```
pre-materials/
├── template/               # Starter template — copy this for new talks
│   ├── _quarto.yml
│   └── index.qmd
└── YYYY-MM-DD-Conference/  # One folder per talk
    ├── _quarto.yml
    ├── index.qmd
    └── ...
```

## Creating a New Presentation

1. Copy the `template/` folder and rename it:
   ```bash
   cp -r template/ 2026-06-10-MyConference
   ```
2. Edit `_quarto.yml` to set the title, author, and theme.
3. Write slides in `index.qmd`.
4. Render with:
   ```bash
   quarto render 2026-06-10-MyConference/
   ```
   or preview live:
   ```bash
   quarto preview 2026-06-10-MyConference/
   ```

## Rendered Outputs

HTML and PDF outputs are tracked in this repo for easy sharing. To re-render all presentations:

```bash
for d in [0-9][0-9][0-9][0-9]-*/; do quarto render "$d"; done
```

## Requirements

- [Quarto](https://quarto.org/docs/get-started/) ≥ 1.4
- R or Python (depending on slide content)
