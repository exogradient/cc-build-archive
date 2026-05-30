# Tool: `Write`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 1

## Change log

- `2.1.154.608` — ~ `description`

  <details><summary>description diff (618 → 240 chars)</summary>

  ```diff
  -Writes a file to the local filesystem.
  +Writes a file to the local filesystem, overwriting if one exists.
   
  -Usage:
  -- This tool will overwrite the existing file if there is one at the provided path.
  -- If this is an existing file, you MUST use the Read tool first to read the file's contents.
  -This tool will fail if you did not read the file first.
  -- Prefer the Edit tool for modifying existing files — it only sends the diff.
  -Only use this tool to create new files or for complete rewrites.
  -- NEVER create documentation files (*.md) or README files unless explicitly requested by the User.
  -- Only use emojis if the user explicitly requests it.
  -Avoid writing emojis to files unless asked.
  +When to use: creating a new file, or fully replacing one you've already Read.
  +Overwriting an existing file you haven't Read will fail.
    … (+1 more diff lines — see the version's tools.diff)
  ```

  </details>

## Current definition

```json
{
  "name": "Write",
  "description": "Writes a file to the local filesystem, overwriting if one exists.\n\nWhen to use: creating a new file, or fully replacing one you've already Read. Overwriting an existing file you haven't Read will fail. For partial changes, use Edit instead.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "file_path": {
        "description": "The absolute path to the file to write (must be absolute, not relative)",
        "type": "string"
      },
      "content": {
        "description": "The content to write to the file",
        "type": "string"
      }
    },
    "required": [
      "file_path",
      "content"
    ],
    "additionalProperties": false
  }
}
```
