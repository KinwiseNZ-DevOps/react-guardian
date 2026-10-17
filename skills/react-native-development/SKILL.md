---
name: react-native-development
description: >
  Builds and reviews React Native applications for mobile platforms using native
  components, platform-aware code, and React Native tooling. Use for Android or
  iOS React Native work. Do not use for browser DOM or React DOM tasks.
---

# React Native Development

Use React's shared component and Hook rules together with React Native's platform-specific APIs. Preserve the app's existing framework and environment choices; native apps do not share the browser DOM or web component model.

## Gate

| Situation | Action |
|---|---|
| The project is a React DOM web app | Use [react-interface-quality](../react-interface-quality/SKILL.md) for UI work |
| The task targets an Android or iOS React Native app | Inspect the installed runtime, framework, platform, and project conventions |
| The task depends on a native API or library not understood from project code | Check the official versioned docs and package compatibility before editing |

## Steps

1. **Inspect** the package manifest and lockfile, React Native version, framework, Metro configuration, scripts, and Android/iOS targets. Do not assume a bare workflow or Expo.
2. **Locate** the relevant core component, navigation, native module, or platform-specific implementation. Prefer existing project abstractions.
3. **Change** the smallest native implementation that meets the request. Use core native components and keep Android/iOS behaviour shared unless there is a verified platform difference.
4. **Verify** the affected platform builds and test on each platform whose behaviour changed. Report unavailable devices or native tooling as unverified.

## Hard rules

- Do not use browser-only DOM elements, `window` APIs, or CSS assumptions in native components.
- Do not add or replace the app framework, navigation stack, or native dependencies without a request and a compatibility reason.
- Use `Platform` or `.ios`/`.android` modules only when a real platform difference warrants them; keep shared logic shared.
- Check the documentation for the installed React Native version and relevant platform because APIs and support can vary.
- Keep React render and Hook logic pure. Side effects belong in event handlers or Effects, not in render.

## Agent dispatch

Use the `react-guardian-workflow` profile's route-and-implement mode for a React Native change, or its plan-only mode when the approach needs agreeing first. If the profile is unavailable, follow the steps directly.

## References

- [React Native getting started](https://reactnative.dev/docs/getting-started)
- [Core and native components](https://reactnative.dev/docs/intro-react-native-components)
- [Platform-specific code](https://reactnative.dev/docs/platform-specific-code)
- [React Native testing](https://reactnative.dev/docs/testing-overview)
- [React API reference](https://react.dev/reference/react)

## Next

- [react-migration](../react-migration/SKILL.md)
- [react-api-integration](../react-api-integration/SKILL.md)
- [react-testing](../react-testing/SKILL.md)
