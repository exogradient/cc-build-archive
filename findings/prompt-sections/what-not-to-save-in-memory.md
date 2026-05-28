# Section: What NOT to save in memory

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Heading level: h2
- Currently present: yes
- Content changes: 0

## Change log

_Present since `2.1.110.610` or earlier; no changes observed in the archive window._

## Current content

```
- Code patterns, conventions, architecture, file paths, or project structure — these can be derived by reading the current project state.
- Git history, recent changes, or who-changed-what — `git log` / `git blame` are authoritative.
- Debugging solutions or fix recipes — the fix is in the code; the commit message has the context.
- Anything already documented in CLAUDE.md files.
- Ephemeral task details: in-progress work, temporary state, current conversation context.

These exclusions apply even when the user explicitly asks you to save. If they ask you to save a PR list or activity summary, ask what was *surprising* or *non-obvious* about it — that is the part worth keeping.
```
