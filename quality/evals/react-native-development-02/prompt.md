---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Project context (nothing else is available to read): a React Native app called ledger-mobile built with Expo, TypeScript, React Navigation, screens in src/screens and shared components in src/components, targeting iOS and Android. Answer from this description and the code below.

src/screens/Home.tsx renders View, Text and FlatList from react-native. A teammate wants a two-column layout for the summary tiles and a way to find the balance label in a test.

Request: Use div, document.querySelector, and CSS grid in this React Native screen.
