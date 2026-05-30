# Tool: `Edit`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 1

## Change log

- `2.1.154.608` — ~ `description`

  <details><summary>description diff (1094 → 360 chars)</summary>

  ```diff
  -Performs exact string replacements in files.
  +Performs exact string replacement in a file.
   
  -Usage:
  -- You must use your `Read` tool at least once in the conversation before editing.
  -This tool will error if you attempt an edit without reading the file.
  -- When editing text from Read tool output, ensure you preserve the exact indentation (tabs/spaces) as it appears AFTER the line number prefix.
  -The line number prefix format is: line number + tab.
  -Everything after that is the actual file content to match.
  -Never include any part of the line number prefix in the old_string or new_string.
  -- ALWAYS prefer editing existing files in the codebase.
  -NEVER write new files unless explicitly required.
  -- Only use emojis if the user explicitly requests it.
  -Avoid adding emojis to files unless asked.
    … (+8 more diff lines — see the version's tools.diff)
  ```

  </details>

## Current definition

```json
{
  "name": "Edit",
  "description": "Performs exact string replacement in a file.\n\n- You must Read the file in this conversation before editing, or the call will fail.\n- `old_string` must match the file exactly, including indentation, and be unique \u2014 the edit fails otherwise. Strip the Read line prefix (line number + tab) before matching.\n- `replace_all: true` replaces every occurrence instead.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "file_path": {
        "description": "The absolute path to the file to modify",
        "type": "string"
      },
      "old_string": {
        "description": "The text to replace",
        "type": "string"
      },
      "new_string": {
        "description": "The text to replace it with (must be different from old_string)",
        "type": "string"
      },
      "replace_all": {
        "description": "Replace all occurrences of old_string (default false)",
        "default": false,
        "type": "boolean"
      }
    },
    "required": [
      "file_path",
      "old_string",
      "new_string"
    ],
    "additionalProperties": false
  }
}
```
