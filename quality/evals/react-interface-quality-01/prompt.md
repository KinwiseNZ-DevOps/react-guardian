---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

```tsx
<table>
  <thead><tr><th>Date</th><th>Payee</th><th>Amount</th><th>Category</th><th>Notes</th></tr></thead>
  <tbody>{rows.map((r) => <tr><td>{r.date}</td><td>{r.payee}</td><td>{r.amount}</td><td>{r.category}</td><td>{r.notes}</td></tr>)}</tbody>
</table>
```

Request: The table overflows on narrow screens and cannot be used by keyboard. Clicking a row opens its details.
