Looking for more useful tools? Discover what else you can build with → [AllToolFree](https://alltoolfree.site)

# VisualBug Hunter

**Catch visual regressions before your users do.**

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg) ![Made by Sajidur](https://img.shields.io/badge/Created%20by-Sajidur-blue) ![No build required](https://img.shields.io/badge/Run-Open%20index.html-brightgreen)

## What problem it solves

Visual regression testing in the browser: upload a baseline and a new screenshot, compare pixels, highlight changed regions, and keep a run history.

## Why it exists

Developers and small teams need this check constantly, but most tools for it are paid, hosted, or collect your data. VisualBug Hunter runs entirely in your browser: no account, no server, no tracking. Your data stays in localStorage on your own machine.

## Main features

- Real, working core functionality — see "How it works" below. Nothing is faked.
- History stored locally in your browser, with JSON/CSV export where applicable.
- Responsive, clean light theme with its own visual identity.
- Works offline, except for features that fetch a URL or public API **you** enter.
- Creator attribution in the footer and About dialog, linking to [Sajidur](https://alltoolfree.site) and [AllToolFree](https://alltoolfree.site).

## How it works

Upload a baseline screenshot and a new screenshot. Set the threshold, click Compare, and inspect the red-highlighted diff canvas. Runs are saved locally.

## Screenshots

> Screenshots are not bundled yet — open `index.html`, run the tool once, and take a screenshot of your own run to add here. Do not use placeholder or stock screenshots.

## Architecture overview

A single self-contained web app. `index.html` holds the markup, styles and JavaScript; `brand.json` holds the central creator/brand configuration; there is no backend and no build step.

## Technology stack

- HTML + CSS + vanilla JavaScript (no framework, no build tool, no dependencies to install).
- Browser APIs only: `fetch`, `FileReader`, `canvas`, `localStorage`, `PerformanceObserver`, `WebCrypto` (where the feature needs them).
- Public APIs used only when you enter a URL/key: OSV (`api.osv.dev`), npm registry, GitHub API, Google DNS-over-HTTPS, and the LLM provider you choose. Each is documented in the app itself.

## Complete folder structure

```
visualbug-hunter/
├── index.html      # the whole app (markup + CSS + JS)
├── brand.json      # central brand configuration (creator, GitHub, website)
├── README.md       # this file
├── LICENSE         # MIT
└── .gitignore
```

## Prerequisites

Any modern browser (Chrome, Firefox, Safari, Edge). No Node, no Python, no database.

## Installation

```bash
git clone https://github.com/sajidurop/visualbug-hunter.git
cd visualbug-hunter
```

> The repository above is the intended repo name for this project. If you publish it under a different name, update the clone URL here and the "View source" link in `index.html` / `brand.json`.

## Local development

Just open the file:

```bash
# Option 1 — double-click index.html, or:
python3 -m http.server 8000
# then open http://localhost:8000
```

Edit `index.html` directly; reload the browser to see changes. There is no build step.

## Environment variables

None. API keys, where a feature offers a live model/API call, are entered in the app UI for that single session and are **never stored** — they are sent only to the provider you selected.

## Configuration

All creator/brand links live in one place: `brand.json` and the `BRAND` object at the top of the `<script>` in `index.html`. Change them there and every attribution in the app follows.

## API documentation

This project has no backend API of its own. Features that call an external API (OSV, npm registry, GitHub, Google DNS, your chosen LLM provider) call that provider's public API directly from the browser, only after you supply the URL or key.

## CLI commands

None — this is a browser app. History and results export as JSON/CSV from inside the app.

## Usage examples

1. Open `index.html`.
2. Follow the "How it works" steps above.
3. Export your results (JSON/CSV button in the app) to keep a record.

## Testing

Manual verification checklist (run before publishing):

1. Open `index.html` — the page loads with no console errors.
2. Run the core flow once with real input (see "How it works").
3. Reload the page — history from the previous run is still there (localStorage).
4. Click the footer links — "Created by Sajidur" and "More free tools" both open https://alltoolfree.site, and "View source on GitHub" opens the repo under github.com/sajidurop once it is created.
5. Export once — the downloaded file contains your real results.

## Docker setup

Not applicable — there is no server component. To self-host, copy this folder to any static host (GitHub Pages, Vercel, Netlify, Nginx, S3).

## Self-hosting and deployment

- **GitHub Pages:** push this folder to a repo, enable Pages, done.
- **Vercel / Netlify:** drag the folder in, or connect the repo — no build command needed.
- **Any static host:** serve the folder as-is.

## Security and privacy

- No credentials, tokens or secrets are committed or stored. API keys entered in the UI are kept in memory for that session only.
- No tracking scripts, no analytics, no external requests except the ones you trigger by entering a URL/API.
- Values that look like secrets are masked on screen where applicable (see the app).
- Cross-origin fetching is limited by the target site's CORS policy — that is a browser security feature, not a bug. Where a fetch is blocked, the app offers a paste-HTML/XML/JSON alternative.

## Known limitations

- Browser CORS rules mean some live URL checks only work for CORS-enabled sites; the app always offers a paste-based alternative.
- History lives in the browser's localStorage, so it does not sync across devices and is cleared if you clear site data.
- Features that need a paid/public API (LLM calls, OSV, npm registry) need internet access and, where applicable, your own key.
- No feature in this app fabricates results: if a live check cannot run, the app says so instead of showing made-up numbers.

## Roadmap

- [ ] Add real screenshots to this README.
- [ ] Add an optional shareable export format per run.
- [ ] Add keyboard shortcuts for the main action.

## Contributing

Issues and pull requests are welcome. Keep changes small, keep the app dependency-free, and keep the creator attribution intact.

## License

MIT — see [LICENSE](LICENSE).

## Credits

Created by [Sajidur](https://alltoolfree.site). More free tools: [AllToolFree](https://alltoolfree.site). Source code (once published): [github.com/sajidurop](https://github.com/sajidurop).
