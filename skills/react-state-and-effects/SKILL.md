---
name: react-state-and-effects
description: >
  Use when writing or fixing React state, Effects, custom Hooks or context: an
  Effect that runs twice or loops, data that goes stale, state that resets or
  will not update, list items that mix up, or deciding where state should live.
  Governs state placement, Effects, keys and Hook structure. Do not use for
  HTTP client design (react-api-integration), speed work (react-performance),
  styling or accessibility (react-interface-quality) or test code (react-testing).
---

# React State and Effects

Fix the cause in how data flows, not the symptom. Most Effect bugs come from using an Effect for something that is not synchronising with the outside world. Follow the project's existing state tools; do not introduce a new one without a request.

## Hard rules

- Keep rendering pure: no mutation of props, state or outside values, and no side effects in the render body.
- Update state without mutating it: build a new array or object, and use the updater form (`setCount(c => c + 1)`) when the next value depends on the previous one.
- Use stable ids from the data as list keys. Use the index only for a static list that is never reordered, filtered or inserted into, and say why. Changing a component's `key` resets its state on purpose.
- Use an Effect only to synchronise with something outside React: a subscription, timer, browser API, non-React widget or network. Do not use one to derive values from props or state (compute during render) or to respond to a user action (use the event handler).
- List every reactive value an Effect reads in its dependency array and keep `react-hooks/exhaustive-deps` on. Fix a loop by restructuring, not by deleting dependencies or silencing the rule.
- Return a cleanup from every Effect that starts a timer, listener, subscription or request. React Strict Mode runs setup and cleanup twice in development to expose missing cleanup; treat that as a diagnostic, not a bug to switch off.
- Give each Effect one job. Split unrelated logic into separate Effects or a custom Hook.
- Call Hooks only at the top level of a component or custom Hook, never in loops, conditions or nested functions. Name custom Hooks `useSomething`. Each call to a Hook gets its own state; Hooks share logic, not state.
- Do not make a function component an error boundary; it cannot be one. Use a class with `getDerivedStateFromError`, or the project's boundary library. Suspense does not catch errors.
- Act only on what the user asked. Before answering or changing anything, open the relevant files and check what is already done; report only what you checked, never guess, and do not redo finished work. Reason: guesses and repeated work waste the user's credit.

## Gate

| Situation | Action |
|---|---|
| The state is used by one component | Keep it local; do not lift or globalise it |
| Two siblings need the same state | Lift it to the nearest common parent |
| Many distant components read a rarely changing value | Use context, with a stable value |
| State is cached server data | Hand off to [react-api-integration](../react-api-integration/SKILL.md) |
| Existing HOCs, render props or `cloneElement` work | Leave them unless asked; prefer Hooks, `children` and context in new code |

## Steps

1. **Inspect** the component, the state's owner, the Effect and its dependencies, the React version, and whether Strict Mode and the Hooks lint rules are on.
2. **Decide** where each piece of state lives and whether it is state at all. Remove state that can be computed from other state.
3. **Change** the smallest part. For context, memoise the provided value or split state from dispatch so unrelated consumers do not re-render.
4. **Verify** with the lint rules, a Strict Mode run, a remount or unmount check for cleanup, and the existing tests. Report what was not run.

## Agent dispatch

Use the `react-guardian-workflow` profile's route-and-implement mode for a change, or its debug mode for a reported defect. If the profile is unavailable, follow the steps directly.

## References

- [Synchronizing with Effects](https://react.dev/learn/synchronizing-with-effects)
- [You Might Not Need an Effect](https://react.dev/learn/you-might-not-need-an-effect)
- [Rules of Hooks](https://react.dev/reference/rules/rules-of-hooks)
- [Rendering lists and keys](https://react.dev/learn/rendering-lists)
- [Scaling up with reducer and context](https://react.dev/learn/scaling-up-with-reducer-and-context)
- [Component (error boundaries)](https://react.dev/reference/react/Component)

## Next

- [react-performance](../react-performance/SKILL.md)
- [react-testing](../react-testing/SKILL.md)
