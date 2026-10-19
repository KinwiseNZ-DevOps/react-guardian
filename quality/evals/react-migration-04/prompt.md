---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

package.json has react 18.2, vite 3, vitest 0.25, typescript 4.8 and several libraries last released three years ago. The app currently builds and the tests pass.

Request: Upgrade dependencies that might be old even though we are not changing React.
