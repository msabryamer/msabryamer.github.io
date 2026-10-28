# Website Structure & Conventions

This is **Mohamed Sabry Amer's** personal academic website, built with **Jekyll** using the [academicpages](https://github.com/academicpages/academicpages.github.io) theme. It is hosted on GitHub Pages at `https://msabryamer.github.io`.

## Key Files to Edit

| Purpose | File |
|---|---|
| **Homepage / About** | `_pages/about.md` — Bio, background, contact info. Permalink: `/` |
| **Research** | `_pages/research.md` — Publications, working papers, in-progress projects. Permalink: `/research/` |
| **Site Config** | `_config.yml` — Site title, author info, social links, navigation, theme settings |
| **Navigation Menu** | `_data/navigation.yml` — Top navigation bar links |
| **Author Sidebar** | `_config.yml` → `author:` section — Avatar, name, location, social/academic links |
| **Profile Photo** | `images/profile.png` |

## Site Structure

```
_pages/           → Markdown/HTML pages (about, research, CV, etc.)
_config.yml       → Jekyll site configuration & author profile
_data/            → Data files (navigation.yml, etc.)
_includes/        → Reusable HTML partials (header, footer, author-profile, etc.)
_layouts/         → Page layout templates
_sass/            → SCSS stylesheets
assets/           → CSS and JS assets
images/           → Site images (profile photo, etc.)
files/            → Downloadable files (CV PDF, etc.)
```

## Research Page Structure (`_pages/research.md`)

The research page has three sections in order:
1. **Publications** — Published, peer-reviewed papers (with DOI links and expandable abstracts)
2. **Working Papers** — Papers under review or in progress (with conference presentations listed as sub-bullets and expandable abstracts)
3. **In Progress** — Early-stage projects (title + coauthors only)

### Conventions
- Paper titles are **bold** and linked to their DOI when published
- Coauthor names link to their Google Scholar or personal pages
- Abstracts use `<details>/<summary>` HTML for collapsible sections
- Styling uses `var(--global-link-color)` for link colors

## Automatic CV & Website Synchronization
Whenever changes are made to the website research page (`_pages/research.md`), homepage/bio (`_pages/about.md`), or author links (`_config.yml`):
- **Automatically synchronize the CV**: Update `files/Mohamed Sabry Amer CV.tex` with corresponding additions, citations, DOIs, or status updates.
- **Update Timestamp**: Update `Last update: Month DD, YYYY` in `Mohamed Sabry Amer CV.tex` with the current day.
- **Auto-recompile PDF**: Run `latexmk "Mohamed Sabry Amer CV.tex"` inside `files/` (or `cd files/build && latexmk -g "../Mohamed Sabry Amer CV.tex" && cp "Mohamed Sabry Amer CV.pdf" ../`) so auxiliary files stay in `build/` and the PDF in `files/` is updated immediately.
- **Vice-versa**: If updates are made to `files/Mohamed Sabry Amer CV.tex`, automatically reflect them on the website pages.
- **Auxiliary Isolation**: Keep all auxiliary build files inside `files/build/`. Outside `files/build/`, only `Mohamed Sabry Amer CV.tex` and `Mohamed Sabry Amer CV.pdf` should exist.

## Git & Deployment
- **Branch**: `master`
- **Remote**: `origin` → GitHub
- **Deployment**: GitHub Pages auto-deploys from the `master` branch
- **Commit style**: Descriptive messages like "Update research and about pages"

