---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

The design tokens live in src/theme/tokens.ts: a teal primary, a warm neutral scale and a small set of status colours. They are used through CSS variables.

Request: Replace our design system colours with a palette from another app.
