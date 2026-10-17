---
name: react-migration
description: >
  Plans and performs React for web version upgrades and legacy API migrations.
  Use when upgrading React or React DOM, moving to modern root APIs, or fixing
  migration warnings. Do not use for React Native runtime upgrades or unrelated
  feature work.
---

# React Migration

Keep observable behaviour stable while changing runtime and APIs. The target version, framework, renderer, libraries, and deployment setup determine the safe path; inspect them before editing.

## Gate

| Situation | Action |
|---|---|
| No upgrade or deprecated API issue is requested or evidenced | Do not start a migration |
| The user requests an upgrade or project warnings identify a blocker | Inventory and plan the smallest staged change |
| A dependency has unknown compatibility | Verify its maintained support before changing versions |

## Steps

1. **Inventory** `react`, `react-dom`, type packages, framework, lockfile, render entry points, deprecated API usage, and test/build scripts.
2. **Plan** compatible intermediate steps and risks. For React 19, consult the [official upgrade guide](https://react.dev/blog/2024/04/25/react-19-upgrade-guide); it recommends React 18.3 as a warning step for apps coming from earlier 18 releases.
3. **Migrate** root rendering and deprecated APIs in small changes. Prefer official codemods only after reviewing their scope and the diff. Do not assume every library or app uses the same renderer.
4. **Check behaviour** with existing tests, build, and targeted manual scenarios. Review warnings and fix only those caused by the migration.

## Hard rules

- Keep `react` and `react-dom` versions compatible and preserve the package manager's lockfile discipline.
- Do not remove `forwardRef`, class components, or `propTypes` indiscriminately. Confirm the exact API, component type, and target version first.
- Treat Strict Mode development behaviour as a diagnostic signal. Do not hide warnings by disabling it without identifying the underlying issue.
- Do not promise a zero-warning upgrade when third-party libraries or unrelated warnings remain; identify ownership and evidence.

## Agent dispatch

Use the `react-guardian-workflow` profile's plan-only mode for a migration plan, or its route-and-implement mode for an approved migration. If the profile is unavailable, work directly from the repository and official migration guide.

## References

- [React 18 upgrade guide](https://react.dev/blog/2022/03/08/react-18-upgrade-guide)
- [React 19 upgrade guide](https://react.dev/blog/2024/04/25/react-19-upgrade-guide)

## Next

- [react-testing](../react-testing/SKILL.md)
