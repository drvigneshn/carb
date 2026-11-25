# Carb Companion — project context

Type 1 diabetes carb counter + insulin dose calculator for Indian foods. Part of the
PediaOS Companion series (Code Blue Companion = cbc.pediaos.com, Pediatric ER Companion = er.pediaos.com).
Single page, no build step — plain HTML/CSS/JS in `index.html`. Decision support only.

## Hosting
- Live at **https://carb.pediaos.com** — GitHub Pages from the `main` branch, root folder.
- `CNAME` holds `carb.pediaos.com`; DNS is a CNAME at Hostinger (`carb` → `drvigneshn.github.io`).
- Deploy = push to `main`. Always `git fetch` first; never clobber newer work.

## Files
- `index.html` — the whole app. Data stays in the user's browser (`localStorage` keys `t1d_set`, `t1d_log`).
- `sw.js` — offline cache. `manifest.webmanifest` + `icon.svg` — PWA install.

## Versioning (every change)
Bump in both places and keep in sync: footer line in `index.html` (`Carb Companion · vX.Y.Z`)
and `sw.js` `const CACHE = 'carb-vX.Y.Z';` (this pushes updates to installed users).
`sw.js` must only delete its own `carb-` caches. Small change → patch, new feature → minor.

## Testing
No test suite. After JS edits, extract the inline `<script>` and run `node --check`.
