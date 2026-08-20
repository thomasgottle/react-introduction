# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

A learning project following the Next.js [React Foundations](https://nextjs.org/learn/react-foundations) course. The course starts from a single HTML file loading React and Babel from a CDN, then incrementally migrates the same app to Next.js.

The migration is complete: the project is now a Next.js App Router app, and the course has reached its final chapter, "Server and Client Components". `index.html` is gone; its markup lives in `app/page.js`.

Because the project tracks a tutorial, prefer the course's incremental approach over introducing tooling it never covers (no TypeScript, linter, test runner, or CSS framework has been added).

## Commands

```
npm run dev      # the only defined script — Next.js dev server on :3000
```

There is no `build`, `start`, `lint`, or `test` script in `package.json`, and no test runner is installed. Use `npx next build` if you need a production build.

## Architecture

Next.js 16 App Router (Turbopack) with React 19. Three files make up the whole app:

- `app/layout.js` — root layout exporting `metadata` and the `<html>`/`<body>` shell. Required by the App Router; every page renders as its `children`.
- `app/page.js` — the `/` route. A **server component** (no directive), holding both `HomePage` and a local `Header` component.
- `app/like-button.js` — the **only client component**, marked `'use client'`. It exists solely because `useState` requires the client boundary; `page.js` stays a server component and imports it.

That server/client split is the point of the current course chapter — keep interactive state in `like-button.js` (or new `'use client'` files) rather than adding `'use client'` to `page.js`.

## Repo hygiene

`.gitignore` contains only `node_modules`, so the `.next/` build directory is committed — the "Installing Next.js" commit added ~173k lines of generated output, and dev-server runs keep dirtying the working tree. Adding `.next` to `.gitignore` (and `git rm -r --cached .next`) is worth doing before the next commit.

## Commit convention

One commit per course section, with the section's title as the message (e.g. "Server and Client Components").
