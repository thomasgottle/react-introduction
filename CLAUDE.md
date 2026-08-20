# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

A learning project following the Next.js [React Foundations](https://nextjs.org/learn/react-foundations) course. The course starts from a single HTML file that loads React and Babel from a CDN, then incrementally migrates the same app to Next.js (installing `next`/`react`/`react-dom`, moving markup into `app/page.js`, adding components, props, state, and finally server vs. client components).

Because the course is incremental, the toolchain here changes as the project progresses. When adding code, follow the stage the course is at rather than jumping ahead to a full framework setup.

## Current stage

Through "Displaying Data with Props" — still the pre-Next.js, CDN-only stage.

## Running

No package manifest, no build step, no tests. Open the file directly:

```
open index.html
```

Everything is compiled in the browser at load time; there is nothing to install and no dev server.

## Architecture

`index.html` is the entire application:

- An **import map** in `<head>` resolves bare specifiers (`react`, `react-dom/client`, `react/jsx-runtime`) to `https://esm.sh/...?dev` builds.
- **Babel standalone** from unpkg compiles the inline `<script type="text/babel" data-type="module" data-presets="react">` block in the browser. The `data-type="module"` attribute is what makes the import map apply; without it the `import` statements fail.
- All components live as plain functions inside that single inline script, which ends by mounting `<HomePage />` into `#app` via `createRoot`.

When the course reaches the Next.js migration, this file gets replaced by a real project (`package.json`, `app/`), and this section should be rewritten with the actual `next dev` / `next build` commands.

## Commit convention

One commit per course section, with the section's title as the message (e.g. "Displaying Data with Props").
