---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

package.json has react 18.2.0, react-dom 18.2.0, react-router-dom 6.8, @testing-library/react 13, and 3 libraries that list react 18 as a peer dependency. There are 12 uses of forwardRef and 2 class components with legacy string refs.

Request: Plan an upgrade from React 18.2 to React 19 in this repository.
