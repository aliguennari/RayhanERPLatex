# AGENTS.md — RayhanERP LaTeX Report

## Build

```bash
latexmk -pdf main.tex   # automates multiple passes (TOC, minitoc, refs)
# or manually: pdflatex main.tex   # 2–3 runs
```

- After changing `Commands.tex` (title, author, etc.) or adding cross-references, recompile.
- `.gitignore` excludes all build artifacts (`*.aux`, `*.log`, `*.pdf`, `*.toc`, `*.mtc*`, `*.fdb*`, etc.).

## Structure

| Path | Purpose |
|---|---|
| `main.tex` | Entrypoint — loads the class, `Commands.tex`, graphics path, then `\input`s chapters |
| `Commands.tex` | **Metadata hub** — edit `\reportAuthor`, `\reportTitle`, `\reportSubject`, `\reportEncadrant`, `\reportEntreprise`, `\dateSoutenance`, jury names |
| `Isetta-PFE-Report-dissertation.cls` | Custom document class (extends `report`) — page geometry, chapter/section formatting, header/footer styles |
| `chapitres/` | 11 chapter files (`00-Page_de_garde` through `10-Verso_du_rapport`), numbered in order |
| `images/` | 67 raster/vector images; referenced without path (set via `\graphicspath{{images/}}`) |

## Key conventions

- **Language**: French — all content, table of contents labels, headings.
- **Font**: Times (`ptm`), double-spaced body (`\doublespacing`) via `setspace`.
- **Page numbering**: roman (i, ii, …) for front matter, arabic (1, 2, …) from chapter 1 onward.
- **TOC depth**: 3; **secnumdepth**: 5.
- Uses `minitoc` — `\dominitoc` in preamble, `\adjustmtc` before each list.

## Custom commands (defined in `Commands.tex`)

- `\reportAuthor`, `\reportAuthors`, `\reportTitle`, `\reportSubject`, `\reportEncadrant`, `\reportEntreprise`, `\dateSoutenance`, `\juryPresident`, `\juryMemberOne`, `\juryMemberTwo` (and their `*Desc` variants).

## Prerequisites

LaTeX distribution with the packages loaded in the `.cls` file (standard TeXLive distribution covers all).
