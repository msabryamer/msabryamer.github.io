---
name: sync-cv-website
description: Automatically synchronizes research, publications, and professional updates between the personal website markdown pages (_pages/research.md, _pages/about.md) and the LaTeX curriculum vitae (files/Mohamed Sabry Amer CV.tex) and recompiles the PDF.
---

# Sync CV & Website Skill

Follow these rules whenever the user asks for changes, additions, or updates to the website or the CV. Changes made to either one must be automatically reflected in the other.

## Core Principle: Bidirectional Synchronization

Whenever an update is requested:
1. **Website $\to$ CV**: If any change is made to `_pages/research.md`, `_pages/about.md`, or `_config.yml`, immediately update `files/Mohamed Sabry Amer CV.tex`, update the `Last update:` timestamp to the current day (e.g., `Month DD, YYYY`), and recompile the PDF.
2. **CV $\to$ Website**: If any change is made to `files/Mohamed Sabry Amer CV.tex`, immediately update `_pages/research.md` (and `_pages/about.md` if bio/education is affected) to keep them in sync.

---

## File Mappings

| Website Location | CV Location (`Mohamed Sabry Amer CV.tex`) | Description |
|---|---|---|
| `_pages/research.md` $\to$ `## Publications` | `\cvsection{Publications}` | Published, peer-reviewed articles. Title in quotes, journal in `\textit{...}`, volume, issue, year, page numbers, and hyperlinked DOI. |
| `_pages/research.md` $\to$ `## Working Papers` | `\cvsection{Working\\Papers}` | Working papers / papers under review. Numbered list with title in quotes and co-authors. |
| `_pages/research.md` $\to$ `## In Progress` | `\cvsection{In Progress}` | Projects in preparation / early stage. Numbered list with title in quotes, co-authors, and notes (e.g., Dataset). |
| `_pages/about.md` $\to$ Bio & Affiliations | `\cvsection{Education}` / `\cvsection{Research\\Experience}` | Degree progress, department, fellowships, and research roles. |
| `_config.yml` $\to$ Author links & Contact | `\cvsection{Contact\\Information}` | Email, homepage, GitHub, LinkedIn, location. |

---

## Formatting Conventions

### 1. Research Page (`_pages/research.md`)
- Section order: `## Publications`, `## Working Papers`, `## In Progress`.
- Titles are **bold**, co-authors link to personal/scholar websites, published titles link to DOI.
- Collapsible `<details><summary>Abstract</summary><p>...</p></details>` for published and working papers.

### 2. LaTeX CV (`files/Mohamed Sabry Amer CV.tex`)
- Section order:
  1. `Contact Information`
  2. `Education`
  3. `Publications`
  4. `Working Papers`
  5. `In Progress`
  6. `Research Experience`
  7. `Work Experience`
  8. `Grants and Awards`
  9. `Skills`
  10. `References`
- Multi-line section titles use `\smash{\parbox[t]{24.5mm}{\raggedright\scshape #1}}` inside `\cvsection` to eliminate baseline depth gaps.
- Dates: Always update `Last update: Month DD, YYYY` in the top right header whenever changes are made.
- Link color: `\definecolor{linkcolor}{HTML}{3333CC}`.

---

## Compilation Procedure

Whenever `Mohamed Sabry Amer CV.tex` is updated, always recompile the PDF immediately:

```bash
cd "files/build" && latexmk -g "../Mohamed Sabry Amer CV.tex" && cp "Mohamed Sabry Amer CV.pdf" ../
```

- All auxiliary files (`.aux`, `.log`, `.xdv`, `.fls`, `.fdb_latexmk`, `.out`) MUST remain exclusively inside `files/build/`.
- Only `Mohamed Sabry Amer CV.tex` and `Mohamed Sabry Amer CV.pdf` should reside directly in `files/`.
