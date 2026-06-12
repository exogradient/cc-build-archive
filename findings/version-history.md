# Claude Code build history

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

One row per captured `cc_version=X.Y.Z.BBB` build observed via npm registry watch,
newest last. Same `X.Y.Z` with a different `.BBB` is a silent republish
(see [methodology](../README.md)). Columns are absolute snapshots for orientation;
for what *changed* between two builds see `notable-diffs.md` and the per-entity
history under `tools/` and `prompt-sections/`.

Surface columns (env / flags / telem / models / settings) are counts extracted
from the binary by `extract-binary-surface.py`; `—` means the capture predates
that extractor.

| cc_version | npm | model | effort | BUILD_TIME (UTC) | GIT_SHA | tools | prompt B | env | flags | telem | models | settings |
|---|---|---|---|---|---|--:|--:|--:|--:|--:|--:|--:|
| `2.1.110.610` | 2.1.110 | claude-sonnet-4-6 | — | 2026-04-15T19:37:30Z | `—` | 23 | 26712 | — | — | — | — | — |
| `2.1.111.b2b` | 2.1.111 | claude-sonnet-4-6 | high | 2026-04-16T14:24:43Z | `—` | 23 | 26263 | — | — | — | — | — |
| `2.1.116.f49` | 2.1.116 | claude-sonnet-4-6 | high | 2026-04-20T13:57:26Z | `9e176d07` | 23 | 26131 | — | — | — | — | — |
| `2.1.128.9fd` | 2.1.128 | claude-sonnet-4-6 | high | 2026-05-04T17:32:00Z | `d6caed18` | 23 | 26151 | — | — | — | — | — |
| `2.1.129.49a` | 2.1.129 | claude-opus-4-7 | xhigh | 2026-05-05T01:33:14Z | `978d0e32` | 23 | 26165 | — | — | — | — | — |
| `2.1.138.1a3` | 2.1.138 | claude-opus-4-7 | xhigh | 2026-05-09T04:04:51Z | `d6d49465` | 23 | 26165 | — | — | — | — | — |
| `2.1.139.b1c` | 2.1.139 | claude-opus-4-7 | xhigh | 2026-05-11T17:03:24Z | `208bf4b4` | 23 | 26569 | — | — | — | — | — |
| `2.1.141.e27` | 2.1.141 | claude-opus-4-7 | xhigh | 2026-05-13T21:26:59Z | `4f4623dd` | 23 | 26573 | — | — | — | — | — |
| `2.1.142.1aa` | 2.1.142 | claude-opus-4-7 | xhigh | 2026-05-14T16:37:49Z | `880324aa` | 26 | 26574 | — | — | — | — | — |
| `2.1.150.474` | 2.1.150 | claude-opus-4-7 | xhigh | 2026-05-23T01:22:49Z | `28d4819e` | 26 | 26562 | — | — | — | — | — |
| `2.1.152.8a5` | 2.1.152 | claude-opus-4-7 | xhigh | 2026-05-26T19:23:17Z | `228d8c60` | 26 | 26581 | — | — | — | — | — |
| `2.1.153.9bb` | 2.1.153 | claude-opus-4-7 | xhigh | 2026-05-27T20:03:21Z | `6cfd2117` | 26 | 26327 | 388 | 47 | 1237 | 105 | 48 |
| `2.1.154.608` | 2.1.154 | claude-opus-4-8 | high | 2026-05-28T12:27:24Z | `b84d2da9` | 27 | 5581 | 392 | 47 | 1242 | 107 | 48 |
| `2.1.156.588` | 2.1.156 | claude-opus-4-8 | high | 2026-05-28T18:30:33Z | `de3d672b` | 27 | 5581 | 392 | 47 | 1243 | 107 | 48 |
| `2.1.157.152` | 2.1.157 | claude-opus-4-8 | high | 2026-05-29T16:21:19Z | `11776d26` | 27 | 5581 | 397 | 47 | 1262 | 107 | 48 |
| `2.1.158.5e6` | 2.1.158 | claude-opus-4-8 | high | 2026-05-29T23:26:17Z | `96d5f493` | 27 | 5581 | 398 | 47 | 1262 | 107 | 48 |
| `2.1.159.28e` | 2.1.159 | claude-opus-4-8 | high | 2026-05-31T16:22:50Z | `dd8c11fc` | 27 | 5581 | 399 | 47 | 1263 | 107 | 48 |
| `2.1.160.bca` | 2.1.160 | claude-opus-4-8 | high | 2026-06-01T15:37:30Z | `de93a1b1` | 27 | 5581 | 449 | 54 | 1275 | 108 | 48 |
| `2.1.161.b76` | 2.1.161 | claude-opus-4-8 | high | 2026-06-02T01:45:55Z | `6a550aea` | 27 | 5581 | 453 | 54 | 1280 | 108 | 48 |
| `2.1.163.7c7` | 2.1.163 | claude-opus-4-8 | high | 2026-06-04T05:48:05Z | `9f38ff86` | 25 | 5581 | 459 | 54 | 1303 | 108 | 48 |
| `2.1.165.ecd` | 2.1.165 | claude-opus-4-8 | high | 2026-06-05T04:32:54Z | `7864e199` | 25 | 5581 | 459 | 54 | 1303 | 107 | 48 |
| `2.1.166.4b6` | 2.1.166 | claude-opus-4-8 | high | 2026-06-05T16:25:43Z | `9bb70ca5` | 25 | 5581 | 464 | 54 | 1313 | 108 | 48 |
| `2.1.168.91f` | 2.1.168 | claude-opus-4-8 | high | 2026-06-06T22:44:08Z | `166c23ad` | 25 | 5581 | 464 | 54 | 1313 | 107 | 48 |
| `2.1.169.ab7` | 2.1.169 | claude-opus-4-8 | high | 2026-06-08T03:22:12Z | `eb44edf1` | 25 | 5860 | 474 | 54 | 1361 | 110 | 48 |
| `2.1.170.6bc` | 2.1.170 | claude-opus-4-8 | high | 2026-06-09T15:09:09Z | `1cda84de` | 25 | 5905 | 477 | 56 | 1366 | 112 | 48 |
| `2.1.172.326` | 2.1.172 | claude-opus-4-8 | high | 2026-06-10T16:30:37Z | `1b719ca2` | 25 | 5905 | 484 | 56 | 1381 | 114 | 46 |
| `2.1.173.53a` | 2.1.173 | claude-opus-4-8 | high | 2026-06-11T01:23:13Z | `70451452` | 25 | 5905 | 484 | 56 | 1381 | 114 | 46 |
| `2.1.174.d48` | 2.1.174 | claude-opus-4-8 | high | 2026-06-11T17:15:35Z | `0ba24f00` | 25 | 5905 | 487 | 56 | 1387 | 113 | 46 |
| `2.1.175.ea6` | 2.1.175 | claude-opus-4-8 | high | 2026-06-12T01:26:01Z | `0b916301` | 25 | 5905 | 487 | 56 | 1387 | 113 | 46 |
