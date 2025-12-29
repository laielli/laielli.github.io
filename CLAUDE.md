# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static GitHub Pages personal website with educational resources (coding patterns, ML concepts, computer vision research) and personal documentation (travel, recipes).

## Development

**No build system** - pure HTML/CSS/JavaScript served directly.

To run locally:
```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`

**Deployment**: Push to `main` branch; GitHub Pages serves automatically.

## Architecture

- **Per-section structure**: Each topic (coding, machine-learning, computer-vision, etc.) has its own directory with an `index.html` landing page
- **Flashcard apps**: Interactive JavaScript apps in `coding/flashcards.html` (YAML-based) and `machine-learning/flashcards.html` (CSV-based)
- **Data files**: YAML files in `coding/patterns/` and `coding/problems/` define algorithm patterns and practice problems

## External Dependencies (CDN)

- **latex.now.sh**: CSS styling framework
- **MathJax**: LaTeX math rendering (use `$...$` syntax)
- **js-yaml**: YAML parsing for flashcard app

## Conventions

- Dark mode toggle implemented on all pages via JavaScript
- Consistent header/navigation structure across pages
- 2-space indentation in HTML
- Class-based JavaScript components
