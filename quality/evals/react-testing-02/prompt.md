---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

src/components/Counter.tsx uses useState and useEffect internally and renders a button that increments a count and shows it in a paragraph. There is one test file for it using Vitest and Testing Library.

Request: Mock every hook and assert the component calls setState once.
