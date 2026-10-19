---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

```tsx
function ContactForm({ onSubmit }) {
  const [email, setEmail] = useState('');
  const [error, setError] = useState('');
  async function handle(e) {
    e.preventDefault();
    if (!email.includes('@')) { setError('Enter a valid email'); return; }
    await onSubmit(email);
  }
  return createElement('form', { onSubmit: handle }, createElement('label', null, 'Email', createElement('input', { value: email, onChange: (e) => setEmail(e.target.value) })), error && createElement('p', { role: 'alert' }, error), createElement('button', { type: 'submit' }, 'Send'));
}
```

Request: Add a regression test for a form that shows validation errors and submits asynchronously.
