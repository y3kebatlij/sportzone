# sportzone

A live sports scores dashboard built with React + Vite, pulling game data from ESPN.

## Prerequisites

- [Node.js](https://nodejs.org/) 20+ and npm

## Running locally

```bash
npm install
npm run dev
```

This starts the Vite dev server with hot reload — edits to files in `src/` show up in the browser immediately. Open:

```
http://localhost:5173/sportzone/
```

(The `/sportzone/` suffix is required — it matches the `base` path set in `vite.config.ts` for GitHub Pages. If port `5173` is already in use, Vite picks the next free port and prints the actual URL in the terminal — use that instead.)

## Testing changes locally

There's no automated test suite in this repo yet. To verify a change before merging:

1. Run `npm run dev` and manually exercise the feature/screen you touched in the browser.
2. Run a production build to make sure it compiles cleanly:
   ```bash
   npm run build
   ```
3. Optionally preview the production build locally:
   ```bash
   npm run preview
   ```

If you add real tests down the line (e.g. Vitest), document the `npm test` command here.

## Deploying

Deploys happen automatically. Any push or merge to `main` triggers the
[`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) GitHub Actions workflow, which:

1. Installs dependencies
2. Runs `npm run build`
3. Publishes the built `dist/` folder to the `gh-pages` branch

GitHub Pages serves that branch at **https://y3kebatlij.github.io/sportzone**. Check the repo's **Actions** tab to confirm a deploy succeeded.

No manual deploy step is needed — just merge to `main`. (The `npm run deploy` script still exists as a manual fallback if you ever need to publish from a branch other than `main`.)

## Making changes

- Work on a feature branch, open a PR into `main`, and merge once it looks good — merging is what kicks off the deploy above.
- `src/App.jsx` holds most of the app's UI and logic; `src/main.tsx` is the entry point.
- The Vite `base` path (`vite.config.ts`) is set to `/sportzone/` to match the GitHub Pages URL — don't change this unless the deploy target changes too.
- This is a plain Vite + React project (JS/TS mixed) with no backend — all data comes from ESPN's public endpoints at runtime.
