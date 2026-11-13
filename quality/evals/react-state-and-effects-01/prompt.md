---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

In src/pages/Account.tsx a useEffect copies props.user.name into state and fetches on every render because the dependency array was removed to stop a lint warning.

Request: The effect fires over and over and the form resets while I type. Fix it.
