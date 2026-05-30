# Tool: `Grep`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
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

## Current definition

```json
{
  "name": "Grep",
  "description": "Content search built on ripgrep. Prefer this over `grep`/`rg` via Bash \u2014 results integrate with the permission UI and file links.\n\n- Full regex syntax (e.g. \"log.*Error\", \"function\\s+\\w+\"). Ripgrep, not grep \u2014 escape literal braces (`interface\\{\\}`).\n- Filter with `glob` (e.g. \"**/*.tsx\") or `type` (e.g. \"js\", \"py\", \"rust\").\n- `output_mode`: \"content\" (matching lines), \"files_with_matches\" (paths only, default), or \"count\".\n- `multiline: true` for patterns that span lines.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "pattern": {
        "description": "The regular expression pattern to search for in file contents",
        "type": "string"
      },
      "path": {
        "description": "File or directory to search in (rg PATH). Defaults to current working directory.",
        "type": "string"
      },
      "glob": {
        "description": "Glob pattern to filter files (e.g. \"*.js\", \"*.{ts,tsx}\") - maps to rg --glob",
        "type": "string"
      },
      "output_mode": {
        "description": "Output mode: \"content\" shows matching lines (supports -A/-B/-C context, -n line numbers, head_limit), \"files_with_matches\" shows file paths (supports head_limit), \"count\" shows match counts (supports head_limit). Defaults to \"files_with_matches\".",
        "type": "string",
        "enum": [
          "content",
          "files_with_matches",
          "count"
        ]
      },
      "-B": {
        "description": "Number of lines to show before each match (rg -B). Requires output_mode: \"content\", ignored otherwise.",
        "type": "number"
      },
      "-A": {
        "description": "Number of lines to show after each match (rg -A). Requires output_mode: \"content\", ignored otherwise.",
        "type": "number"
      },
      "-C": {
        "description": "Alias for context.",
        "type": "number"
      },
      "context": {
        "description": "Number of lines to show before and after each match (rg -C). Requires output_mode: \"content\", ignored otherwise.",
        "type": "number"
      },
      "-n": {
        "description": "Show line numbers in output (rg -n). Requires output_mode: \"content\", ignored otherwise. Defaults to true.",
        "type": "boolean"
      },
      "-i": {
        "description": "Case insensitive search (rg -i)",
        "type": "boolean"
      },
      "-o": {
        "description": "Print only the matched (non-empty) parts of each matching line, one match per output line (rg -o / --only-matching). Requires output_mode: \"content\", ignored otherwise. Defaults to false.",
        "type": "boolean"
      },
      "type": {
        "description": "File type to search (rg --type). Common types: js, py, rust, go, java, etc. More efficient than include for standard file types.",
        "type": "string"
      },
      "head_limit": {
        "description": "Limit output to first N lines/entries, equivalent to \"| head -N\". Works across all output modes: content (limits output lines), files_with_matches (limits file paths), count (limits count entries). Defaults to 250 when unspecified. Pass 0 for unlimited (use sparingly \u2014 large result sets waste context).",
        "type": "number"
      },
      "offset": {
        "description": "Skip first N lines/entries before applying head_limit, equivalent to \"| tail -n +N | head -N\". Works across all output modes. Defaults to 0.",
        "type": "number"
      },
      "multiline": {
        "description": "Enable multiline mode where . matches newlines and patterns can span lines (rg -U --multiline-dotall). Default: false.",
        "type": "boolean"
      }
    },
    "required": [
      "pattern"
    ],
    "additionalProperties": false
  }
}
```
