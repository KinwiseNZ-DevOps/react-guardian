---
name: react-testing
description: >
  Use when adding test coverage for React components, hooks or user workflows,
  diagnosing flaky UI tests, or choosing test boundaries. Writes or reviews
  tests for React components, hooks and user workflows. Do not use for
  production changes that do not involve test work.
---

# React Testing

Test outcomes a user or caller can observe. Keep tests aligned with the repository's test runner and component boundaries instead of importing a preferred stack without need.

## Hard rules

- Do not assert private implementation details when rendered behaviour or public contracts can be tested.
- Do not mock the unit under test or its local state transitions. Mock external boundaries only when the real boundary is not suitable for this test.
- Do not make time-sensitive or network-dependent tests flaky. Control the clock or isolate external services using project conventions.
- Do not suppress React warnings broadly; identify and fix the source or explain why an isolated warning is expected.
- For React Native tests, follow the installed project's setup. JavaScript component tests do not validate the underlying platform code, so verify platform-dependent behaviour on a device or simulator.
- Act only on what the user asked. Before answering or changing anything, open the relevant files and check what is already done; report only what you checked, never guess, and do not redo finished work. Reason: guesses and repeated work waste the user's credit.

## Gate

| Situation | Action |
|---|---|
| No test change or test diagnosis is requested | Do not expand test scope |
| Behaviour changed or a defect needs regression coverage | Add a focused test at the owning boundary |
| A test depends on internal implementation details | Prefer an observable interaction or output |

## Steps

1. **Inspect** test scripts, existing libraries, setup, fixtures, and nearby tests.
2. **Choose** the narrowest boundary that proves the behaviour: pure logic, hook/component interaction, or end-to-end workflow.
3. **Exercise** realistic user input, async completion, and meaningful failure states. Keep fixtures minimal and deterministic.
4. **Run** the focused test, then relevant broader checks if available. Report failures separately from pre-existing failures.

## Agent dispatch

Use the `react-guardian-workflow` profile's test-review mode when available. Review its suggestions against nearby tests and this skill. If unavailable, follow the steps directly.

## References

- [React API reference and Rules of React](https://react.dev/reference/react)
- [React Native testing guidance](https://reactnative.dev/docs/testing-overview)

## Next

- [react-migration](../react-migration/SKILL.md)
- [react-api-integration](../react-api-integration/SKILL.md)
