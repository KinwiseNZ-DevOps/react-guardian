---
name: react-performance
description: >
  Use when a React web app feels slow: laggy typing or clicks, slow page or
  route loads, a large bundle, long lists, heavy images or too many requests.
  Finds the real cause with measurements and applies the smallest fix. Do not
  use for rebuilding state structure (react-state-and-effects), API client
  design (react-api-integration), React Native tuning (react-native-development)
  or a request to memoise everything.
---

# React Performance

Measure first, change one thing, measure again. A change that is not shown to help is a risk with no benefit. Keep behaviour, accessibility and the visual design unchanged.

## Hard rules

- Do not optimise without evidence: a profile, a metric, a user-visible symptom or a bundle report. Record the before and after numbers, or say that none were taken.
- Do not wrap everything in `React.memo`, `useMemo` or `useCallback`. Memoise only where a profile shows wasted re-renders and the props are stable. `useCallback` helps only when the function goes to a memoised child or is an Effect dependency.
- Check whether the project uses the React Compiler before adding manual memoisation. Do not add it where the compiler already handles it.
- Fix in this order: move state down to the component that uses it, pass changing parts as `children`, fix keys and Effect loops, then memoise.
- Do not put frequently changing values in one wide context; every consumer re-renders when it changes.
- Lazy-load routes and heavy, rarely used components with `React.lazy` inside a Suspense boundary, and give load failures an error boundary. Do not lazy-load content that is visible on first paint.
- Virtualise only lists long enough to cost real time. Check the installed virtualisation library's version before writing its props; pagination or filtering may be the better fix.
- Give images explicit width and height, load below-the-fold images lazily, offer responsive sizes, and never lazy-load the main above-the-fold image.
- Follow the installed version of the data-fetching library for caching and prefetching. Do not mix the old and new query APIs.
- Act only on what the user asked. Before answering or changing anything, open the relevant files and check what is already done; report only what you checked, never guess, and do not redo finished work. Reason: guesses and repeated work waste the user's credit.

## Gate

| Situation | Action |
|---|---|
| No symptom, metric or profile is given | Ask for the symptom or measure it before changing code |
| Slow typing or clicks | Profile renders; look at state placement and wide contexts first |
| Slow first load | Check bundle size, route splitting, images and request count |
| Long list is slow | Check keys, row cost and virtualisation or pagination |

## Steps

1. **Measure** with React DevTools Profiler, the browser Performance panel or the build's bundle report, on a production build for load questions.
2. **Locate** the specific component, request, asset or bundle chunk responsible.
3. **Change** the smallest part in the fix order above.
4. **Verify** by measuring the same scenario again, and run the existing tests and accessibility checks for the touched UI.

## Agent dispatch

Use the `react-guardian-workflow` profile's plan-only mode when the cause is unclear, or route-and-implement once the cause is measured. If the profile is unavailable, follow the steps directly.

## References

- [memo](https://react.dev/reference/react/memo)
- [React Compiler](https://react.dev/learn/react-compiler)
- [Rendering lists and keys](https://react.dev/learn/rendering-lists)

## Next

- [react-state-and-effects](../react-state-and-effects/SKILL.md)
- [react-testing](../react-testing/SKILL.md)
