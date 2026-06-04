# Tool: `Grep`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: **no** (removed)
- Definition changes: 2

## Change log

- `2.1.141.e27` — + `input_schema.properties.-o`; + `input_schema.properties.-o.description`; + `input_schema.properties.-o.type`
- `2.1.154.608` — ~ `description`

  <details><summary>description diff (866 → 477 chars)</summary>

  ```diff
  -A powerful search tool built on ripgrep
  +Content search built on ripgrep.
  +Prefer this over `grep`/`rg` via Bash — results integrate with the permission UI and file links.
   
  -  Usage:
  -  - ALWAYS use Grep for search tasks.
  -NEVER invoke `grep` or `rg` as a Bash command.
  -The Grep tool has been optimized for correct permissions and access.
  -  - Supports full regex syntax (e.g., "log.*Error", "function\s+\w+")
  -  - Filter files with glob parameter (e.g., "*.js", "**/*.tsx") or type parameter (e.g., "js", "py", "rust")
  -  - Output modes: "content" shows matching lines, "files_with_matches" shows only file paths (default), "count" shows match counts
  -  - Use Agent tool for open-ended searches requiring multiple rounds
  -  - Pattern syntax: Uses ripgrep (not grep) - literal braces need escaping (use `interface\{\}` to find `interface{}` in Go code)
  -  - Multiline matching: By default patterns match within single lines only.
    … (+10 more diff lines — see the version's tools.diff)
  ```

  </details>
- `2.1.163.7c7` — removed.
