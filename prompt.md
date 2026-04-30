# Task: Merge 8 HTML files into a single tabbed web page

## Context

This directory contains 8 standalone HTML files that together form a retro terminal-style educational lexicon (Sales & Marketing, 2026). Each file is one "view" of the full lexicon. They share a VT323 monospace font and a CRT scanline aesthetic, but each has its own distinct color theme.

The files and their themes:

| File | Tab label | Color theme |
|------|-----------|-------------|
| `1-lexicon_index_page.html` | IDX | Orange `#FF6600` |
| `3-lexicon_f1_help.html` | F1 — HELP | Yellow `#FFFF00` |
| `2-lexicon_f2_all_terms.html` | F2 — ALL TERMS | White `#FFFFFF` |
| `4-lexicon_ch1_green.html` | F3 — CH 01 | Green `#33FF33` |
| `5-lexicon_ch2_amber.html` | F4 — CH 02 | Amber `#FFB000` |
| `6-lexicon_ch3_blue.html` | F5 — CH 03 | Blue `#5555FF` |
| `7-lexicon_ch4_cyan.html` | F6 — CH 04 | Cyan `#00FFFF` |
| `8-lexicon_ch5_magenta.html` | F7 — CH 05 | Magenta `#FF00FF` |

Each file already has a tab bar at the bottom (`.fkbar` / `.fk` divs). The currently active tab uses the `.ak` class; inactive tabs use `.dk`. There is no JavaScript — navigation between pages doesn't work yet.

## Goal

Create a new file `lexicon-tabbed.html` that merges all 8 views into a single working web page with functional tab navigation. **Do not modify the source files.**

## Required approach

1. **One shared tab bar** — render a single `.fkbar` at the bottom of the page, always visible. It must show all 8 tabs in their original order: `F1 — HELP`, `F2 — ALL TERMS`, `F3 — CH 01`, `F4 — CH 02`, `F5 — CH 03`, `F6 — CH 04`, `F7 — CH 05`, `IDX`.

2. **Content panels** — wrap each file's inner content (everything inside `.page`, excluding the `.fkbar`) in its own `<div class="tab-panel" data-tab="...">` and hide all panels except the active one (`display:none`).

3. **CSS isolation via dynamic injection** — each file's `<style>` block must only be active when that tab is visible. On tab switch: remove the previous tab's `<style>` tag from `<head>` and inject the new one. This keeps the color themes (border colors, `.dk`/`.ak` backgrounds, etc.) fully isolated and prevents bleed between views.

4. **Active tab highlight** — on switch, update the tab bar so the current tab has `.ak` and all others have `.dk`. The `.ak`/`.dk` styles are defined per-theme in each injected stylesheet, so they will automatically reflect the correct color for the active view.

5. **Default view** — open on the `IDX` tab (orange theme) on first load.

6. **No layout changes** — preserve every file's original HTML structure, class names, and inline styles exactly as-is inside its panel. The only structural change allowed is removing each file's own `.fkbar` (since there is now one shared bar) and wrapping the content in a `tab-panel` div.

## Output

A single self-contained file: `lexicon-tabbed.html`. No external dependencies beyond the Google Fonts import already in the source files. No build tools, no frameworks — vanilla HTML/CSS/JS only.
