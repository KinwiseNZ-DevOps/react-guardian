---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

```tsx
<div className="modal-backdrop" onClick={onClose}>
  <div className="modal">
    <div className="modal-title">Delete account</div>
    <div className="modal-body">This cannot be undone.</div>
    <div className="modal-close" onClick={onClose}>x</div>
    <div className="btn" onClick={confirm}>Delete</div>
  </div>
</div>
```

Request: Make this modal accessible without changing its appearance more than needed.
