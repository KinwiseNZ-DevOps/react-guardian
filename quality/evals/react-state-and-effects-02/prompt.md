---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

A to-do list renders items with key={index}. Users can delete and reorder rows, and typed text in an uncontrolled input jumps to the wrong row.

Request: Why does the text move to another row after I delete one?
