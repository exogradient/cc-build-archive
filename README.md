---
title: cc-build-archive
description: A historical, diffable record of the system prompt and tool definitions inside Anthropic's Claude Code, extracted from shipped builds to show how the agent's instructions and capabilities change across releases.
---

# cc-build-archive

An AI coding agent is shaped by far more than its model weights. On every turn
it carries a **system prompt** (standing instructions), a **tool set** (what it
may actually do — read files, run commands, search the web), and a set of
**request-time levers** (which model, how much reasoning effort, which API
capability flags, how context is managed). In Claude Code all of this ships
inside the published binary — not secret, but not documented either: extractable
by anyone, recorded by no one. There is no public, side-by-side history of how
these change release to release.

This archive is that history. For every Claude Code release it extracts the wire
system prompt, the full tool definitions, and the request-config surface, then
diffs each release against the one before — so a change in how the agent is
instructed, what it can do, or how it's run becomes a concrete, dated diff.

## Relationship to the official CHANGELOG

Anthropic ships a
[CHANGELOG](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md):
curated, prose release notes stating each public `X.Y.Z`'s *intended* changes
(however they're drafted — Anthropic has said Claude authors much of Claude
Code itself). This archive is its complement — **machine-extracted ground
truth of what each shipped binary actually contains.** The contrast that
matters isn't who writes the notes; it's *summarized intent* vs *extracted
artifact*. Different questions, so this enriches rather than duplicates:

- **It shows what the notes omit.** The CHANGELOG describes user-facing changes;
  the archive surfaces the layers it never mentions — the exact wire system
  prompt, full tool schemas, the default model / effort / thinking / API-beta /
  cache levers, the telemetry-event surface, and env/settings keys.
- **It catches silent republishes the CHANGELOG can't.** Anthropic sometimes
  re-publishes the same `X.Y.Z` as a new build with no new CHANGELOG entry; the
  watcher detects those by tarball-integrity/ETag change and diffs them anyway.
- **It makes the notes verifiable.** Every prose claim can be checked against the
  shipped artifact, with the supporting diff attached.

## Notable moments captured

- `2.1.111`→`2.1.116` (Apr 16→20) — a system-prompt line telling the model to be
  terse (*"Length limits: keep text between tool calls to ≤25 words…"*) appears
  then is removed, lining up with Anthropic's
  [post-mortem](https://www.anthropic.com/engineering/april-23-postmortem) on a
  stretch of degraded quality.
- `2.1.128`→`2.1.129` (May 5) — default model flips `Sonnet 4.6` → `Opus 4.7`;
  the `context-1m` beta turns on, max output tokens double (32k → 64k), and
  reasoning effort steps up (`high` → `xhigh`) in the same release.
- `2.1.139` (May 11) — the sub-agent (`Agent`) tool's instructions grow ~400
  characters in one release.
- `2.1.141`→`2.1.142` (May 14) — the single `TodoWrite` tool is replaced by four
  `Task*` tools (`TaskCreate`/`TaskGet`/`TaskList`/`TaskUpdate`).
- `2.1.153`→`2.1.154` (May 28) — the **Opus 4.8** rollout: default model `Opus 4.7` →
  `Opus 4.8`, the new `Workflow` tool appears, the `mid-conversation-system`
  beta turns on, every core tool's description is rewritten, and the
  instructions block *shrinks ~20.7k characters* while effort is dialed back
  `xhigh` → `high` — a coordinated prompt-and-config retune, none of it obvious
  from a version bump.
- `2.1.156`→`2.1.157` (May 29) — plugin-sync and agent-loop machinery lands as a wave of
  new telemetry/env surface (`tengu_plugins_sync_*`, `tengu_loop_*`,
  `CLAUDE_CODE_SYNC_PLUGINS`, `CLAUDE_CODE_LOOP_KEEPALIVE`) with no prompt change
  — a feature visible only in the binary surface, not the wire request.

## Beyond what a single request shows

A normal request only sends the tools it needs up front; the binary holds many
more **deferred tools** loaded on demand (background monitors, push
notifications, cron scheduling). The archive extracts the full tool list from
the executable, so the inventory reflects everything a release can do.

## Where to look

- **`findings/notable-diffs.md`** — highlight reel: releases where the prompt, a
  tool, the default model, or an API capability flag changed.
- **`findings/system-prompt-history.md`** — the current system prompt, section by
  section, followed by one consolidated change log (with rendered word-level
  diffs of each wording change).
- **`findings/skills-history.md`** — the available-skills list (a `role: system`
  message in `messages[]`, distinct from the `system` field) rendered verbatim,
  plus a per-skill change log.
- **`findings/tools/<ToolName>.md`** — one file per tool: current definition +
  full change history, each definition change shown as a rendered diff.
- **`findings/version-history.md`** — one row per release (model, tool count,
  prompt size, binary-surface counts, timestamps).
- **`findings/cadence.png`** — weekly chart of Claude Code's npm publication
  cadence.
- **`captures/<version>/`** — raw evidence: the exact system prompt, wire tools,
  full tool list from the binary, the prompt structure (cache breakpoints +
  the skills/context reminders injected into the first user turn), the binary
  config surface (`binary-surface.json` — env vars, feature flags, telemetry
  events, model ids, API betas, first-party endpoints, settings keys), and
  metadata.
- **`findings/diffs/<from>__to__<to>/`** — per-transition diff artifacts. Each
  `summary.yaml` lists **only what changed** between two builds (unchanged
  levers are omitted, so the signal is what's left); alongside it,
  `binary-surface.diff`, `tools.diff`, and `system-reminders.matrix` carry the
  detailed deltas when those surfaces moved.

## Method & caveats

Each release is captured two ways: **on the wire** (run once with `-p "hi"` in a
sealed sandbox — telemetry off, API key stubbed, traffic routed to a local proxy
that records the request and returns a synthetic reply, so no real API calls are
made), and **from the binary** (its embedded JS is read directly for the full
tool list).

- **Versioning.** npm's public `X.Y.Z` isn't unique — Anthropic sometimes
  re-publishes the same number with a different build. Each release is identified
  by the build ID Anthropic embeds in the binary (`cc_version=X.Y.Z.BBB`) plus
  the tarball hash, alongside its `BUILD_TIME`, `GIT_SHA`, and binary sha256.
- **History blind spot.** Builds captured after the fact come from npm's
  *current* tarball, so a silently-overwritten version only preserves its latest
  contents; the live watch catches overwrites going forward.
- **Noise.** Random sandbox paths and the host shell are normalized out before
  diffing, so a diff reflects a real prompt change, not where it ran.

## License

[CC-BY 4.0](LICENSE) on data and findings — cite by URL. Independent research
archive, not affiliated with or endorsed by Anthropic.
