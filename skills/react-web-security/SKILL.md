---
name: react-web-security
description: >
  Use when reviewing or changing the security of a React web app: untrusted
  HTML or URLs in the page, sign-in and token storage, protected routes and
  roles, secrets in client configuration, dependency audits, source maps or
  payment steps. Do not use for HTTP client design (react-api-integration),
  server code, React Native secure storage or general accessibility.
---

# React Web Security

The browser is untrusted. Anything shipped to it, and anything it sends back, can be read or changed by the user. Keep the existing sign-in and payment providers; change the smallest thing that closes a real gap.

## Hard rules

- Treat route guards and role checks in React as interface only. The server must authorise every request. Never describe a client check as access control.
- Render text through JSX, which escapes it. Use `dangerouslySetInnerHTML` only when rich HTML is required, and only with a vetted sanitiser such as DOMPurify configured for the allowed tags.
- Validate user-supplied URLs before using them in `href` or `src`, and reject `javascript:` schemes. Avoid `eval` and `new Function` on user data.
- Anything in a client environment variable is public. Variables with the `REACT_APP_`, `VITE_` or `NEXT_PUBLIC_` prefix end up in the browser bundle. Never put a private key, token or secret in one; call the service through your own server.
- Never hard-code credentials, example passwords or keys in components, tests or listings.
- Prefer session or token cookies that the server sets as HttpOnly, Secure and SameSite over tokens in `localStorage` or `sessionStorage`, and state the trade-off. Cookie sessions need CSRF protection; browser-readable tokens are exposed to any script that runs on the page.
- Passwords are hashed on the server with a slow, salted algorithm. They are not encrypted and never stored in the browser.
- For payments, the server decides the amount and confirms the result. A success message from the browser is not proof of payment. Never handle raw card numbers; use the provider's hosted fields.
- Do not run `npm audit fix --force` without reading the breaking changes it makes. Review new dependencies for ownership, maintenance and licence.
- Publish source maps only deliberately. The usual approach is to upload them to the error tracker and not serve them publicly.
- Check privacy before enabling session replay or analytics; do not capture typed personal data without masking and consent.
- Act only on what the user asked. Before answering or changing anything, open the relevant files and check what is already done; report only what you checked, never guess, and do not redo finished work. Reason: guesses and repeated work waste the user's credit.

## Gate

| Situation | Action |
|---|---|
| The request is about the HTTP client, retries or error states | Route to [react-api-integration](../react-api-integration/SKILL.md) |
| Server-side access control is missing | Report it as the real fix; do not hide it with a client check |
| A secret is already in the bundle or repository | Say it must be treated as leaked and rotated, then remove it |

## Steps

1. **Inspect** where untrusted data reaches the page, where tokens are stored, which environment variables reach the bundle, which routes are guarded, and how the build is deployed.
2. **Rank** findings by what an attacker could do, and separate confirmed issues from possible ones.
3. **Change** the smallest part, keeping the sign-in provider and user flows.
4. **Verify** with a harmless script payload in a rendered field, a search of the built bundle for key names, `npm audit` output, and the existing tests. Report what was not run.

## Agent dispatch

Use the `react-guardian-workflow` profile's plan-only mode for a review, or route-and-implement for an agreed fix. If the profile is unavailable, follow the steps directly.

## References

- [Common components, including dangerouslySetInnerHTML](https://react.dev/reference/react-dom/components/common)
- [React 19 upgrade guide, javascript: URL errors](https://react.dev/blog/2024/04/25/react-19-upgrade-guide)

## Next

- [react-api-integration](../react-api-integration/SKILL.md)
- [react-testing](../react-testing/SKILL.md)
