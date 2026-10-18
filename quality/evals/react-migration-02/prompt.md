---
max_turns: 10
allowed_tools: [Read, Glob, Grep, Skill]
---

Add flushSync to every async setState call because batching is broken.
