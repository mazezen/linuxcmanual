# Project knowledge

This file gives Codebuff context about your project: goals, commands, conventions, and gotchas.

## What this project is

A Chinese-language (zh) **mdbook** reference on Linux C programming functions. Each source file documents one C function (e.g., `isalpha`, `malloc`, `fopen`, `socket`). The book is organized into 16 chapters covering categories like character testing, string conversion, memory, date/time, math, file I/O, processes, signals, networking, etc.

- **Book config:** `book.toml` (src = "." — SUMMARY.md lives in project root, source .md files in `src/`)
- **Book source:** `src/*.md` — one file per C function
- **Table of contents:** `SUMMARY.md` (defines chapter structure and navigation)
- **Preface:** `preface.md`
- **Pre-built HTML output:** `book/` directory (already built)

## Commands

- **Build the book:** `mdbook build` (requires `mdbook` CLI — install via `cargo install mdbook`)
- **Serve with live reload:** `mdbook serve` (serves at `http://localhost:3000`)
- **Watch & rebuild on changes:** `mdbook watch`

Note: `mdbook` is **not currently installed** on this system. Install with `cargo install mdbook` if you need to build or serve.

## Repo & Upstream

- Git repo: `https://github.com/wa-lang/wabook`
- The book content was originally from the `wa-lang/wabook` repository's `testdata/` directory (see edit URL template in book.toml).

## Conventions

- All content is in **Chinese** (Simplified).
- Each `.md` file in `src/` covers exactly one C function, named as `functionname_chapter_page.md`.
- Some entries have companion `.d` directory files (e.g., `iscntrl_1_4.d/` and `iscntrl_1_4.d.html` in output).
- Chapters 1-16 are covered, with a few structural quirks (chapter 6 uses `chapter_29.md` as filename, chapter 13 uses `chapter_13,md`).
- The pre-built `book/` directory contains the rendered HTML. If you modify source `.md` files, rebuild with `mdbook build` to regenerate.
