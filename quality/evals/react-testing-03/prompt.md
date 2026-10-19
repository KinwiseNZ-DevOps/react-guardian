---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

```tsx
it('shows the result', async () => {
  render(createElement(Accounts));
  await new Promise((r) => setTimeout(r, 2000));
  expect(screen.getByText('Everyday account')).toBeInTheDocument();
});
```
The request is made with fetch to /api/accounts/.

Request: Our UI test is flaky because it waits two seconds before checking the network result.
