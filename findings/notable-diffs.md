# Notable diffs

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

Flagged notable if `prompt_delta_chars` ≥ 300, or any wire tool, static-binary tool, or embedded system-reminder was added/removed/changed. Most recent first. Full per-diff content lives under `findings/diffs/<from>__to__<to>/` (always present, regardless of how this file lists it).

## `2.1.153.9bb` → `2.1.154.608`

- **Default model**: `claude-opus-4-7` → `claude-opus-4-8`
- **Prompt delta**: -20746 chars (instructions block)
- **Output config (effort)**: `{'effort': 'xhigh'}` → `{'effort': 'high'}`
- **Cache breakpoints**: `['system[1]', 'system[2]', 'messages[0][2]']` → `['system[1]', 'system[2]', 'messages[0][1]']`
- **API betas**: added `mid-conversation-system-2026-04-07`
- **Tools added**: `Workflow`
- **Tools with changed definition**: `Agent` (description), `AskUserQuestion` (description), `Bash` (description), `Edit` (description), `Glob` (description), `Grep` (description), `Read` (description), `WebFetch` (description), `WebSearch` (description), `Write` (description)
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 removed (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.153.9bb__to__2.1.154.608/tools.diff) · [all artifacts](diffs/2.1.153.9bb__to__2.1.154.608/)

## `2.1.141.e27` → `2.1.142.1aa`

- **Prompt delta**: +1 chars (instructions block)
- **Tools added**: `TaskCreate`, `TaskGet`, `TaskList`, `TaskUpdate`
- **Tools removed**: `TodoWrite`
- **Tools with changed definition**: `Bash` (description)
- **Binary tools added**: `SendUserFile`
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.141.e27__to__2.1.142.1aa/tools.diff) · [all artifacts](diffs/2.1.141.e27__to__2.1.142.1aa/)

## `2.1.139.b1c` → `2.1.141.e27`

- **Prompt delta**: +4 chars (instructions block)
- **Tools with changed definition**: `Grep` (input_schema), `ScheduleWakeup` (description)
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.139.b1c__to__2.1.141.e27/tools.diff) · [all artifacts](diffs/2.1.139.b1c__to__2.1.141.e27/)

## `2.1.138.1a3` → `2.1.139.b1c`

- **Prompt delta**: +404 chars (instructions block)
- **Tools with changed definition**: `Agent` (description)
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.138.1a3__to__2.1.139.b1c/tools.diff) · [all artifacts](diffs/2.1.138.1a3__to__2.1.139.b1c/)

## `2.1.129.49a` → `2.1.138.1a3`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `Bash` (input_schema), `EnterWorktree` (description)
- **Binary tools with changed definition**: `AskUserQuestion` (see `tools-from-binary.matrix`)
- **System reminders (binary)**: 1 removed, 1 modified (see `system-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.129.49a__to__2.1.138.1a3/tools.diff) · [all artifacts](diffs/2.1.129.49a__to__2.1.138.1a3/)

## `2.1.128.9fd` → `2.1.129.49a`

- **Default model**: `claude-sonnet-4-6` → `claude-opus-4-7`
- **Prompt delta**: +14 chars (instructions block)
- **Output config (effort)**: `{'effort': 'high'}` → `{'effort': 'xhigh'}`
- **Max tokens**: `32000` → `64000`
- **API betas**: added `context-1m-2025-08-07`
- **Tools with changed definition**: `Bash` (description), `EnterPlanMode` (description)
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.128.9fd__to__2.1.129.49a/tools.diff) · [all artifacts](diffs/2.1.128.9fd__to__2.1.129.49a/)

## `2.1.116.f49` → `2.1.128.9fd`

- **Prompt delta**: +20 chars (instructions block)
- **Tools with changed definition**: `Agent` (description), `Read` (description)
- **Binary tools added**: `ShareOnboardingGuide`
- **Binary tools removed**: `Config`
- **Binary tools with changed definition**: `RemoteTrigger` (see `tools-from-binary.matrix`)
- **System reminders (binary)**: 1 removed, 2 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.116.f49__to__2.1.128.9fd/tools.diff) · [all artifacts](diffs/2.1.116.f49__to__2.1.128.9fd/)

## `2.1.111.b2b` → `2.1.116.f49`

- **Prompt delta**: -132 chars (instructions block)
- **Tools with changed definition**: `Bash` (description)
- **System reminders (binary)**: 2 added, 1 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.111.b2b__to__2.1.116.f49/tools.diff) · [all artifacts](diffs/2.1.111.b2b__to__2.1.116.f49/)

## `2.1.110.610` → `2.1.111.b2b`

- **Prompt delta**: -449 chars (instructions block)
- **Output config (effort)**: `absent` → `{'effort': 'high'}`
- **Tools with changed definition**: `Agent` (description), `Skill` (description, input_schema)
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.110.610__to__2.1.111.b2b/tools.diff) · [all artifacts](diffs/2.1.110.610__to__2.1.111.b2b/)

## `2.1.152.8a5` → `2.1.153.9bb`

- **Prompt delta**: -146 chars (instructions block)
- **Tools with changed definition**: `AskUserQuestion` (description)
- **System reminders (binary)**: 2 modified (see `system-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.152.8a5__to__2.1.153.9bb/tools.diff) · [all artifacts](diffs/2.1.152.8a5__to__2.1.153.9bb/)

## `2.1.150.474` → `2.1.152.8a5`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `AskUserQuestion` (description)
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.150.474__to__2.1.152.8a5/tools.diff) · [all artifacts](diffs/2.1.150.474__to__2.1.152.8a5/)

## `2.1.142.1aa` → `2.1.150.474`

- **Prompt delta**: +0 chars (instructions block)
- **Binary tools added**: `Workflow`
- **Binary tools with changed definition**: `Monitor` (see `tools-from-binary.matrix`)
- **System reminders (binary)**: 2 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Diff artifacts](diffs/2.1.142.1aa__to__2.1.150.474/)

