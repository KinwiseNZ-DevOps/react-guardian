---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

The codebase has 12 forwardRef wrappers. Some are used by a shared library that still passes refs the old way; others are only used inside the app.

Request: Can we delete every forwardRef while upgrading to React 19?
