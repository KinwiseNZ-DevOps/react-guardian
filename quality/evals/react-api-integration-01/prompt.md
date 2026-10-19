---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

src/api/client.ts exports get(path) and post(path, body) that call fetch with an access token from memory. When the token expires the API returns 401 with a JSON body; server errors return 500 with a JSON error body. A refresh endpoint POST /api/auth/refresh/ exists.

Request: Handle expired authentication and server errors in our React API client.
