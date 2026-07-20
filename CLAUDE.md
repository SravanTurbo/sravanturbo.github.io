# sravanturbo.github.io

Personal writing site for Sravan Turibilli — a backend engineer writing about decisions, systems, and what actually happened. Minimal, typographic, no JS frameworks.

## Structure

```
index.html          — homepage (profile photo + curated post list)
archive.html        — all posts grouped by year
posts/*.html        — individual post pages
css/style.css       — single stylesheet using CSS custom properties
js/header.js        — injects <header> with nav + theme toggle; applied via <script src> in <body>
js/footer.js        — injects <footer>; applied via <script src> at end of <body>
images/avatar.jpg   — profile photo
```

## Design system

All colors and spacing flow through CSS custom properties in `:root` (and `[data-theme="dark"]`):

| Variable     | Light        | Dark         |
|--------------|--------------|--------------|
| `--text`     | `#1a1a1a`    | `#e8e8e8`    |
| `--muted`    | `#666`       | `#888`       |
| `--border`   | `#e0e0e0`    | `#2e2e2e`    |
| `--bg`       | `#ffffff`    | `#111111`    |
| `--code-bg`  | `#f0f0f0`    | `#1e1e1e`    |
| `--max`      | `680px`      | same         |

Fonts: `--sans` (UI), `--serif` (prose body), `--mono` (code).

## Dark mode

- Toggle button rendered by `header.js` (sun/moon SVG icons, `.theme-toggle`)
- Preference stored in `localStorage` under key `theme` (`"light"` or `"dark"`)
- Each HTML file has an inline `<script>` after the stylesheet link to apply the saved theme before paint (prevents flash)
- Tag pill colors have dedicated dark overrides via `[data-theme="dark"] .post-tag[data-tag="..."]`

## Tags

Four tag types with color-coded pills:

| Tag slug          | Description              |
|-------------------|--------------------------|
| `startup-series`  | Orange — startup journey posts |
| `technical`       | Blue — engineering deep-dives |
| `leadership`      | Purple — people/management |
| `number`          | Grey — series number pill (e.g. #1) |

## Adding a new post

1. Create `posts/<slug>.html` — copy an existing post as template
2. Add the anti-flash script after the stylesheet link (line 9)
3. Add entry to `index.html` post list if it's featured ("Worth reading")
4. Add entry to `archive.html` under the correct year group

## Conventions

- No JS frameworks — vanilla only
- No build step — static files served directly
- Max content width: 680px centered
- `header.js` and `footer.js` are injected via inline `<script src>` tags, not imports
- The `<html>` element carries `data-theme="light"|"dark"` for theme switching
