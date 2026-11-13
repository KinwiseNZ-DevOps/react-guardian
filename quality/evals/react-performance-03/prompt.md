---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

The first load of ledger-web takes six seconds on mobile. The main bundle is large and the hero image is a 3 MB photo.

Request: Speed up the first load.
