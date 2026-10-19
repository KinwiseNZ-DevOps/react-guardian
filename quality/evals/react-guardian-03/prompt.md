---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React Native app called ledger-mobile built with Expo, TypeScript, React Navigation, screens in src/screens and shared components in src/components, targeting iOS and Android. Answer from this description and the code below.

The tab bar in src/navigation/index.tsx renders the Home, Activity and Settings screens. Pressing back on Settings sometimes exits the app instead of returning to Activity. React Navigation is at version 6.

Request: This is a React Native app. Fix its navigation.
