# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A single self-contained static page, `code.html` — a Korean-language Claude Code beginner tutorial ("클로드 코드 첫걸음"). No build system, package manager, tests, or linter. To preview, open the file directly in a browser (e.g. `start code.html` on Windows).

## Structure of `code.html`

Everything (HTML, CSS, JS) is inline in one file; the only external resource is Google Fonts (Nanum Myeongjo, IBM Plex Sans KR, IBM Plex Mono).

- **Layout:** fixed left table of contents (`nav.toc`) + numbered lesson sections on the right; on mobile the TOC collapses to the top. Lessons are in learning order, so keep numbering sequential when adding/reordering.
- **Theming:** all colors are CSS custom properties on `:root`. Dark mode values are defined twice — under `@media (prefers-color-scheme: dark)` guarded by `:root:not([data-theme="light"])`, and under `:root[data-theme="dark"]`. Change both blocks together when touching dark colors.
- **Inline script (bottom of file)** wires three features:
  - OS tabs: `.tabs button[data-os]` toggles `[data-panel]` blocks; Windows tab (`#tab-win`) is auto-selected on Windows.
  - Copy buttons: `.copy` inside `.code` copies the `<pre>` text, stripping trailing `# comments` from each line.
  - Progress tracking: `.check input[data-lesson]` checkboxes persist to `localStorage` key `cc-tutorial-progress`; `data-lesson` must match a lesson section `id` so the matching TOC link (`nav.toc a[href="#id"]`) gets the `done` class. Updates `#progress-text` and `#progress-bar`.

## Conventions

- Content is written in Korean; `word-break: keep-all` is set on `body`.
- Keep the page dependency-free (no frameworks or bundlers).
