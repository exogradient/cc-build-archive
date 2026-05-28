# Section: auto memory

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Heading level: h1
- Currently present: yes
- Content changes: 1

## Change log

- `2.1.153.9bb` — content changed (725 → 678 chars, -47).

## Current content

```
You have a persistent, file-based memory system at `/tmp/cc-home.<RANDOM>/.claude/projects/-tmp-cc-capture-<RANDOM>/memory/`. This directory already exists — write to it directly with the Write tool (do not run mkdir or check for its existence).

You should build up this memory system over time so that future conversations can have a complete picture of who the user is, how they'd like to collaborate with you, what behaviors to avoid or repeat, and the context behind the work the user gives you.

If the user explicitly asks you to remember something, save it immediately as whichever type fits best. If they ask you to forget something, find and remove the relevant entry.
```
