# AGENTS.md

## Project Snapshot
- Single Astro site (not a monorepo app layout despite `pnpm-workspace.yaml`): main code is under `src/`.
- Global shell is `src/layouts/Layout.astro`; every page route uses this layout.
- Main routes currently: `src/pages/index.astro` and `src/pages/proyectos/ModuTuring.astro`.

## Verified Commands
- Install deps: `npm install` (a `package-lock.json` is present and current).
- Dev server: `npm run dev` (Astro default: `http://localhost:4321`).
- Production build: `npm run build`.
- Preview build: `npm run preview`.
- Astro CLI passthrough: `npm run astro -- <args>`.

## Toolchain / Styling Quirks
- Tailwind CSS v4 is wired through Vite plugin in `astro.config.mjs` (`@tailwindcss/vite`).
- Global Tailwind load is only `@import "tailwindcss";` in `src/styles/global.css`.
- `tsconfig.json` extends `astro/tsconfigs/strict`.

## High-Value Edit Notes
- `src/layouts/Layout.astro` contains:
  - shared page chrome (sidebar + responsive offsets), and
  - inline DOM script that toggles mobile sidebar classes (`hidden`/`flex`) and main blur.
- If changing layout/sidebar behavior, verify both breakpoints:
  - mobile (`<640px`): open/close buttons, outside-click close, link-click close.
  - desktop (`>=640px`): sidebar remains visible and no unwanted blur toggling.

## What Not To Assume
- No repo-configured lint/test/typecheck scripts exist in `package.json`; do not claim they were run.
- `README.md` is mostly Astro starter boilerplate; trust actual config/scripts over README text.
