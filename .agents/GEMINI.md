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

## Git & Deployment
- **Branch**: `master`
- **Remote**: `origin` → GitHub
- **Deployment**: GitHub Pages auto-deploys from the `master` branch
- **Commit style**: Descriptive messages like "Update research and about pages"
