<div align="center">

# React Foundations

**Learning React from the ground up — from a single HTML file to a Next.js app.**

[![Next.js](https://img.shields.io/badge/Next.js-16.3-000000?style=flat-square&logo=next.js&logoColor=white)](https://nextjs.org)
[![React](https://img.shields.io/badge/React-19.2-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev)
[![Course](https://img.shields.io/badge/course-React%20Foundations-0070F3?style=flat-square)](https://nextjs.org/learn/react-foundations)

</div>

---

## About

A hands-on walkthrough of the Next.js [**React Foundations**](https://nextjs.org/learn/react-foundations) course.

The course builds the same small app twice over. It opens with one `index.html` that pulls React and Babel from a CDN and compiles JSX in the browser, then rebuilds it piece by piece as a real Next.js project — components, props, state, and finally the server/client component split.

Each chapter is its own commit, so `git log` reads as a timeline of the course.

## Getting started

```bash
npm install
npm run dev
```

Then open **[localhost:3000](http://localhost:3000)**.

> [!NOTE]
> `dev` is the only defined script. For a production build, run `npx next build` directly — there is no test runner or linter in this project.

## Project structure

```
app/
├── layout.js         Root layout — <html>/<body> shell and page metadata
├── page.js           The / route (server component)
└── like-button.js    Interactive counter (client component)
```

## How it works

The app is deliberately tiny — the interesting part is *where the boundary sits*.

| File | Type | Why |
| :--- | :--- | :--- |
| `page.js` | Server component | The default. Renders on the server, ships no JS to the browser. |
| `like-button.js` | Client component | Marked `'use client'` because `useState` needs to run in the browser. |

Rather than making the whole page interactive, only the button crosses into the client. `page.js` stays on the server and imports the button as a child — the pattern the course's final chapter is built around.

## Course progress

- [x] About React and Next.js
- [x] Rendering User Interfaces
- [x] Updating UI with Javascript
- [x] Getting Started with React
- [x] Building UI with Components
- [x] Displaying Data with Props
- [x] Adding Interactivity with State
- [x] From React to Next.js
- [x] Installing Next.js
- [x] Server and Client Components

---

<div align="center">
<sub>Built while following the <a href="https://nextjs.org/learn/react-foundations">React Foundations</a> course.</sub>
</div>
