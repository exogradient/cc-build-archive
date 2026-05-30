# Tool: `Glob`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 1

## Change log

- `2.1.154.608` — ~ `description`

  <details><summary>description diff (371 → 140 chars)</summary>

  ```diff
  -- Fast file pattern matching tool that works with any codebase size
  -- Supports glob patterns like "**/*.js" or "src/**/*.ts"
  -- Returns matching file paths sorted by modification time
  -- Use this tool when you need to find files by name patterns
  -- When you are doing an open ended search that may require multiple rounds of globbing and grepping, use the Agent tool instead
  +Fast file pattern matching.
  +Supports glob patterns like "**/*.js" or "src/**/*.ts".
  +Returns matching file paths sorted by modification time.
  ```

  </details>

## Current definition

```json
{
  "name": "Glob",
  "description": "Fast file pattern matching. Supports glob patterns like \"**/*.js\" or \"src/**/*.ts\". Returns matching file paths sorted by modification time.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "pattern": {
        "description": "The glob pattern to match files against",
        "type": "string"
      },
      "path": {
        "description": "The directory to search in. If not specified, the current working directory will be used. IMPORTANT: Omit this field to use the default directory. DO NOT enter \"undefined\" or \"null\" - simply omit it for the default behavior. Must be a valid directory path if provided.",
        "type": "string"
      }
    },
    "required": [
      "pattern"
    ],
    "additionalProperties": false
  }
}
```
