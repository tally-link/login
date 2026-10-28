# Tally-Link Login

Minimal redirect page for Tally-Link. It sends visitors straight to the Tally-Link web app:

**https://tally-link.swiftcom-web.workers.dev/**

## How it works

`index.html` is a single self-contained file with three layers of redirection:

1. **JavaScript** — `window.location.replace()` fires first and carries the incoming `?query` and `#hash` through to the app.
2. **Meta refresh** — `<meta http-equiv="refresh" content="0; ...">` catches visitors with JavaScript disabled.
3. **Fallback link** — a "Continue to Tally-Link" button in case both are blocked.

`location.replace()` is used so the redirect page does not sit in the browser back history.
The page is marked `noindex, nofollow` and points its `canonical` at the app, so search engines index the app and not this redirect.

## Hosting

Served with **GitHub Pages** from the `main` branch (root).

Live URL: https://tally-link.github.io/login/

## Editing

The destination appears in three places in `index.html` — keep them in sync:

- `<link rel="canonical">`
- `<meta http-equiv="refresh">`
- `TARGET` inside the `<script>` block
