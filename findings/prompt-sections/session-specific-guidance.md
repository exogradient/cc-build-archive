# Section: Session-specific guidance

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Heading level: h1
- Currently present: yes
- Content changes: 1

## Change log

- `2.1.111.b2b` — content changed (1258 → 740 chars, -518).

## Current content

```
 - Use the Agent tool with specialized agents when the task at hand matches the agent's description. Subagents are valuable for parallelizing independent queries or for protecting the main context window from excessive results, but they should not be used excessively when not needed. Importantly, avoid duplicating work that subagents are already doing - if you delegate research to a subagent, do not also perform the same searches yourself.
 - For broad codebase exploration or research that'll take more than 3 queries, spawn Agent with subagent_type=Explore. Otherwise use the Glob or Grep directly.
 - When the user types `/<skill-name>`, invoke it via Skill. Only use skills listed in the user-invocable skills section — don't guess.
```
