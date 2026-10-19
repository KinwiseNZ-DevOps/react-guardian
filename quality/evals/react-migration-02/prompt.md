---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

A page loads data in a useEffect and calls setLoading(false) and setItems(data) after an await. Some users see two renders after the data arrives.

Request: Add flushSync to every async setState call because batching is broken.
