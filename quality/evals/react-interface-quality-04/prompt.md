---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

src/pages/Settings.tsx is mostly semantic HTML already: a main element, a nav with links, a form with labelled inputs and two buttons, and a few decorative divs and icons.

Request: Add ARIA roles to every element in this page.
