---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

src/pages/Accounts.tsx fetches GET /api/accounts/ in a useEffect, stores the result in state, and shows a loading state, an error message and a list. There are no tests for it yet.

Request: Our React component calls a REST endpoint and the same task needs regression tests.
