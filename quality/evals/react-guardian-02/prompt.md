---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

The app has about 80 components, a design token file at src/theme/tokens.ts, and its own button and input components used everywhere.

Request: Make every component use React.memo and rewrite all styling to your favourite UI kit.
