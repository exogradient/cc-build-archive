# Section: Before recommending from memory

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Heading level: h2
- Currently present: yes
- Content changes: 0

## Change log

_Present since `2.1.110.610` or earlier; no changes observed in the archive window._

## Current content

```
A memory that names a specific function, file, or flag is a claim that it existed *when the memory was written*. It may have been renamed, removed, or never merged. Before recommending it:

- If the memory names a file path: check the file exists.
- If the memory names a function or flag: grep for it.
- If the user is about to act on your recommendation (not just asking about history), verify first.

"The memory says X exists" is not the same as "X exists now."

A memory that summarizes repo state (activity logs, architecture snapshots) is frozen in time. If the user asks about *recent* or *current* state, prefer `git log` or reading the code over recalling the snapshot.
```
