---
name: react-migration
description: >
  Use when upgrading React or React DOM, moving to modern root APIs, replacing
  legacy APIs, or fixing console warnings after a version upgrade. Plans and
  performs React for web version upgrades and legacy API migrations. Do not use
  for React Native runtime upgrades (react-native-development) or unrelated
  feature work.
---

# React Migration

Keep observable behaviour stable while changing runtime and APIs. The target version, framework, renderer, libraries, and deployment setup determine the safe path; inspect them before editing.

## Hard rules

- Keep `react` and `react-dom` versions compatible and preserve the package manager's lockfile discipline.
- Do not remove `forwardRef`, class components, or `propTypes` indiscriminately. Confirm the exact API, component type, and target version first.
- Treat Strict Mode development behaviour as a diagnostic signal. Do not hide warnings by disabling it without identifying the underlying issue.
- Do not promise a zero-warning upgrade when third-party libraries or unrelated warnings remain; identify ownership and evidence.
- Act only on what the user asked. Before answering or changing anything, open the relevant files and check what is already done; report only what you checked, never guess, and do not redo finished work. Reason: guesses and repeated work waste the user's credit.

## Gate

| Situation | Action |
|---|---|
| No upgrade or deprecated API issue is requested or evidenced | Do not start a migration |
| The user requests an upgrade or project warnings identify a blocker | Inventory and plan the smallest staged change |
| A dependency has unknown compatibility | Verify its maintained support before changing versions |

## Steps

1. **Inventory** `react`, `react-dom`, type packages, framework, lockfile, render entry points, deprecated API usage, and test/build scripts.
2. **Plan** compatible intermediate steps and risks. For React 19, consult the [official upgrade guide](https://react.dev/blog/2024/04/25/react-19-upgrade-guide) and follow its staged upgrade path rather than assuming a single jump between major versions.
3. **Migrate** root rendering and deprecated APIs in small changes. Prefer official codemods only after reviewing their scope and the diff. Do not assume every library or app uses the same renderer.
4. **Check behaviour** with existing tests, build, and targeted manual scenarios. Review warnings and fix only those caused by the migration.

## Agent dispatch

Use the `react-guardian-workflow` profile's plan-only mode for a migration plan, or its route-and-implement mode for an approved migration. If the profile is unavailable, work directly from the repository and official migration guide.

## References

- [React 18 upgrade guide](https://react.dev/blog/2022/03/08/react-18-upgrade-guide)
- [React 19 upgrade guide](https://react.dev/blog/2024/04/25/react-19-upgrade-guide)

## Next

- [react-testing](../react-testing/SKILL.md)
