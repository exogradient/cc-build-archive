# Tool: `Read`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 2

## Change log

- `2.1.128.9fd` — ~ `description`

  <details><summary>description diff (1680 → 1830 chars)</summary>

  ```diff
   - This tool can only read files, not directories.
  -To read a directory, use an ls command via the Bash tool.
  +To list files in a directory, use the registered shell tool.
   - You will regularly be asked to read screenshots.
   - If you read a file that exists but has empty contents you will receive a system reminder warning in place of file contents.
  +- Do NOT re-read a file you just edited to verify — Edit/Write would have errored if the change failed, and the harness tracks file state for you.
  ```

  </details>
- `2.1.154.608` — ~ `description`

  <details><summary>description diff (1830 → 838 chars)</summary>

  ```diff
   Reads a file from the local filesystem.
  -You can access any file directly by using this tool.
  -Assume this tool is able to read all files on the machine.
  -If the User provides a path to a file assume that path is valid.
  -It is okay to read a file that does not exist; an error will be returned.
   
  -Usage:
  -- The file_path parameter must be an absolute path, not a relative path
  -- By default, it reads up to 2000 lines starting from the beginning of the file
  +- `file_path` must be an absolute path.
  +- Reads up to 2000 lines by default.
   - You can optionally specify a line offset and limit (especially handy for long files), but it's recommended to read the whole file by not providing these parameters
   - Results are returned using cat -n format, with line numbers starting at 1
  -- This tool allows Claude Code to read images (eg PNG, JPG, etc).
    … (+18 more diff lines — see the version's tools.diff)
  ```

  </details>

## Current definition

```json
{
  "name": "Read",
  "description": "Reads a file from the local filesystem.\n\n- `file_path` must be an absolute path.\n- Reads up to 2000 lines by default.\n- You can optionally specify a line offset and limit (especially handy for long files), but it's recommended to read the whole file by not providing these parameters\n- Results are returned using cat -n format, with line numbers starting at 1\n- Reads images (PNG, JPG, \u2026) and presents them visually. Reads PDFs via the `pages` parameter (e.g. \"1-5\", max 20 pages/request; required for PDFs over 10 pages). Reads Jupyter notebooks (.ipynb) as cells with outputs.\n- Reading a directory, a missing file, or an empty file returns an error or system reminder rather than content.\n- Do NOT re-read a file you just edited to verify \u2014 Edit/Write would have errored if the change failed, and the harness tracks file state for you.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "file_path": {
        "description": "The absolute path to the file to read",
        "type": "string"
      },
      "offset": {
        "description": "The line number to start reading from. Only provide if the file is too large to read at once",
        "type": "integer",
        "minimum": 0,
        "maximum": 9007199254740991
      },
      "limit": {
        "description": "The number of lines to read. Only provide if the file is too large to read at once.",
        "type": "integer",
        "exclusiveMinimum": 0,
        "maximum": 9007199254740991
      },
      "pages": {
        "description": "Page range for PDF files (e.g., \"1-5\", \"3\", \"10-20\"). Only applicable to PDF files. Maximum 20 pages per request.",
        "type": "string"
      }
    },
    "required": [
      "file_path"
    ],
    "additionalProperties": false
  }
}
```
