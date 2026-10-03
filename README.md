# CoreForge Studio

Describe a project in plain English, pick a backend stack and database, and get a small, working backend — an entrypoint, routes, a data model, a dependency manifest, and a README. Review the files, ask for changes, and export the result as a ZIP ready to commit.

## Files

- `index.html` — the entire app: landing page, splash screen, and the generator itself, in one self-contained file.

## What's in it

- **Landing page** with an interactive stack preview (click a stack to see its real file layout), a typewriter line cycling through example project descriptions, scroll-triggered reveals, a gradient background with drifting parallax accents, and a custom logo mark.
- **Login / guest entry** — "Log in" reads the identity your Claude account already has on this artifact (your name if you're a recognized member, otherwise guest); there's no separate password system.
- **Generator** — six stacks (Express, NestJS, FastAPI, Django, Spring Boot, Fiber), four databases (PostgreSQL, MongoDB, MySQL, SQLite), optional features (auth, validation, error handling, Docker, tests), live generation progress, a "Refine" step to iterate without starting over, local per-browser history, and ZIP export.

## Important: this runs on Claude.ai, not as a standalone static site

The AI generation, refine step, login, and download/ZIP features are powered by `window.claude`, a runtime the page only gets when opened as a **published Claude Artifact** inside claude.ai. Opened directly in a browser (or hosted as-is on GitHub Pages), the landing page and animations render, but:

- **Generate / Refine** will report that AI generation isn't available.
- **Log in** will fall back to guest.
- **Download file / Download ZIP** will report downloads unavailable.

To keep the app itself working after publishing to GitHub, you have two options:

1. **Keep it as a Claude Artifact** and use this repo for source history / collaboration, linking to the live artifact for the working version.
2. **Wire it to your own backend**: replace the `claude.use('sample')`, `claude.use('user')`, and `claude.use('downloads')` calls in `index.html` with your own API (e.g. a small server proxying the Anthropic API's `/v1/messages` endpoint), your own auth, and a `Blob` + `<a download>` flow. This makes it a fully standalone static site.

## Local preview

No build step — open `index.html` directly to check the landing page and layout. The generator itself needs the Claude Artifact runtime (see above).

## License

MIT — see `LICENSE`.
