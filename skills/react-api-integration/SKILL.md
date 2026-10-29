---
name: react-api-integration
description: >
  Use when a React app calls an HTTP API: fetching data, sign-in and token
  handling, error and loading states, retries, or a request that keeps failing.
  Designs or changes React clients that talk to HTTP APIs, including request
  boundaries, authentication handling, errors and async UI states. Do not use
  for building server endpoints, general component styling (react-interface-
  quality) or tests (react-testing).
---

# React API Integration

Keep transport and response handling consistent with the application's existing client. Preserve the server contract and show users clear, safe feedback without exposing implementation details. For React Native, check the app's platform and credential storage conventions as well as its network client.

## Hard rules

- Never ship private credentials in client application code or browser-delivered configuration.
- Do not retry non-idempotent mutations automatically unless the API supports an idempotency mechanism and the user-visible behaviour is clear.
- Do not trust HTML or other active content returned by a server. Render text safely and use an established sanitisation boundary when rich HTML is required.
- Avoid logging tokens, personal data, full request bodies, or server internals.
- Act only on what the user asked. Before answering or changing anything, open the relevant files and check what is already done; report only what you checked, never guess, and do not redo finished work. Reason: guesses and repeated work waste the user's credit.

## Gate

| Situation | Action |
|---|---|
| The request does not involve remote data | Route to the owning UI or state skill |
| An API call is duplicated or handles failures inconsistently | Inspect the current client and consolidate only the affected boundary |
| The server contract is unknown | Inspect API schemas or ask for the missing contract before guessing |

## Steps

1. **Inspect** the existing HTTP client, auth and CSRF handling, environment configuration, types, cache/state layer, and server contract.
2. **Define** request and response types at the boundary where the project supports them. Normalize errors once and distinguish validation, authentication, network, and server failures.
3. **Implement** cancellation or stale-response handling where component lifetime or changing inputs make it necessary. Use bounded retries only for safe, retryable operations.
4. **Verify** success and failure states, auth expiry, duplicate submission behaviour, and that secrets or sensitive response data are not logged or exposed.

## Agent dispatch

Use the `react-guardian-workflow` profile's route-and-implement mode for an integration change, or its plan-only mode when the approach needs agreeing first. If the profile is unavailable, follow the steps directly.

## Next

- [react-interface-quality](../react-interface-quality/SKILL.md)
- [react-testing](../react-testing/SKILL.md)
