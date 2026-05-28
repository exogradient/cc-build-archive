# Section: Using your tools

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Heading level: h1
- Currently present: yes
- Content changes: 2

## Change log

- `2.1.111.b2b` — content changed (1602 → 742 chars, -860).
- `2.1.142.1aa` — content changed (742 → 743 chars, +1).

## Current content

```
 - Prefer dedicated tools over Bash when one fits (Read, Edit, Write, Glob, Grep) — reserve Bash for shell-only operations.
 - Use TaskCreate to plan and track work. Mark each task completed as soon as it's done; don't batch.
 - You can call multiple tools in a single response. If you intend to call multiple tools and there are no dependencies between them, make all independent tool calls in parallel. Maximize use of parallel tool calls where possible to increase efficiency. However, if some tool calls depend on previous calls to inform dependent values, do NOT call these tools in parallel and instead call them sequentially. For instance, if one operation must complete before another starts, run these operations sequentially instead.
```
