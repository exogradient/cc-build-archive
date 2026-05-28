---
title: cc-build-archive
description: A historical, diffable record of the system prompt and tool definitions inside Anthropic's Claude Code, extracted from shipped builds to show how the agent's instructions and capabilities change across releases.
---

# cc-build-archive

Every AI coding agent runs on two things the model sees but users usually
don't: a **system prompt** (the standing instructions given on every turn) and
a **tool set** (what it's allowed to do — read files, run commands, search the
web). In Claude Code both ship right inside the published binary — not secret,
readable by anyone who extracts it. What doesn't exist anywhere is a
historical, side-by-side record of how they change release to release.

This archive recovers the system prompt and tool definitions from each Claude
Code release and diffs it against the last.

## Notable moments captured

- `2.1.111`→`2.1.116` (Apr 16→20) — a system-prompt line telling the model to be
  terse (*"Length limits: keep text between tool calls to ≤25 words…"*) appears
  then is removed, matching Anthropic's
  [post-mortem](https://www.anthropic.com/engineering/april-23-postmortem) on a
  stretch of degraded quality.
- `2.1.129` (May 5) — default model flips `Sonnet 4.6` → `Opus 4.7`, with a
  `1M-context` flag turning on in the same release.
- `2.1.142` (May 14) — the single `TodoWrite` tool is replaced by four `Task*`
  tools (`TaskCreate`/`TaskGet`/`TaskList`/`TaskUpdate`).
- `2.1.139` (May 11) — the sub-agent (`Agent`) tool's instructions grow ~400
  characters in one release.

## Beyond what a single request shows

A normal request only sends the tools it needs up front; the binary holds many
more **deferred tools** loaded on demand (background monitors, push
notifications, cron scheduling). The archive extracts the full tool list from
the executable, so the inventory reflects everything a release can do.

## Where to look

- **`findings/notable-diffs.md`** — highlight reel: releases where the prompt, a
  tool, the default model, or an API capability flag changed.
- **`findings/tools/<ToolName>.md`** · **`findings/prompt-sections/<section>.md`**
  — one file per tool / prompt section: current definition + full change history.
- **`findings/version-history.md`** — one row per release (model, tool count,
  prompt size, timestamps).
- **`captures/<version>/`** — raw evidence: the exact system prompt, wire tools,
  full tool list from the binary, the prompt structure (cache breakpoints +
  the skills/context reminders injected into the first user turn), and metadata.

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
