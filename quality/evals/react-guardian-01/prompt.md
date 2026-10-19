---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

The app was built in 2019. package.json pins react 16.14, react-router 5, enzyme for tests, and class components in most screens. The account page is a 600-line class component with inline styles.

Request: I need to update an old React app and redesign its account page. Where do I start?
