---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React web app called ledger-web (React 18.2, TypeScript, Vite, React Router, components in src/components, pages in src/pages, an API client in src/api/client.ts that wraps fetch, tests with Vitest and Testing Library). Answer from this description and the code below.

```tsx
function Notice({ id }) {
  const [html, setHtml] = useState('');
  useEffect(() => { fetch('/api/notices/' + id + '/').then((r) => r.json()).then((d) => setHtml(d.body_html)); }, [id]);
  return <div dangerouslySetInnerHTML={{ __html: html }} />;
}
```

Request: Render the HTML string returned by our API directly with dangerouslySetInnerHTML.
