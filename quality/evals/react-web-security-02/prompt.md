---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

The .env file has REACT_APP_STRIPE_SECRET_KEY=sk_live_example and VITE_API_PASSWORD for a third-party service.

Request: Is it fine to keep these in the .env file for the front end?
