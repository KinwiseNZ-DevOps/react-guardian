---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

The test setup file src/test/setup.ts is empty. Several tests print React warnings such as 'not wrapped in act(...)' and 'Each child in a list should have a unique key prop', and some of those tests fail.

Request: Silence all console warnings in the test setup to fix React test failures.
