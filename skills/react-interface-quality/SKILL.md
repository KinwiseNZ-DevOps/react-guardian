---
name: react-interface-quality
description: >
  Improves React DOM component structure, responsive behaviour, accessibility,
  and design-system consistency. Use for browser UI reviews and changes. Do not
  use for React Native screens, API client contracts, or backend integration.
---

# React Interface Quality

Retain the product's visual identity and user flows. Prefer composable components and clear data flow, but keep existing patterns when a rewrite has no demonstrated benefit.

## Hard rules

- Do not invent brand colours, typography, spacing scales, or fixed breakpoints. Reuse project tokens and verify overflow at the affected sizes.
- Use native semantic elements and labels first. Add ARIA only when native semantics do not express the interaction.
- Keep components and Hooks pure during render. Do not mutate props, state, or other non-local values; run side effects in event handlers or Effects.
- Keep controls keyboard-operable, with visible focus and understandable names. Ensure async feedback and validation errors are perceivable.
- Avoid rendering the same information in different structures solely by device size when responsive CSS can preserve semantics.
- Do not add loading, error, or empty states mechanically when the component has no asynchronous or variable data.

## Gate

| Situation | Action |
|---|---|
| The UI already meets the requested behaviour and has no evidenced defect | Leave it unchanged |
| The user describes a usability, accessibility, or layout issue | Reproduce it at the affected viewport and interaction |
| A broad redesign is implied but not specified | Clarify the intended outcome before replacing established patterns |

## Steps

1. **Inspect** nearby components, styles, tokens, breakpoints, routing, and accessibility patterns.
2. **Reproduce** the issue at relevant screen sizes and input modes. Check loading, empty, error, and success states where relevant.
3. **Change** the smallest set of components. Keep rendering focused, move reusable behaviour into hooks or utilities where it improves clarity, and avoid premature memoisation.
4. **Verify** keyboard use, visible focus, semantic structure, responsive layout, and the project's existing UI checks.

## Agent dispatch

Use the `react-guardian-workflow` profile's route-and-implement mode for an interface change, or its plan-only mode when the approach needs agreeing first. If the profile is unavailable, follow the steps directly.

## References

- [React API reference and Rules of React](https://react.dev/reference/react)

## Next

- [react-testing](../react-testing/SKILL.md)
