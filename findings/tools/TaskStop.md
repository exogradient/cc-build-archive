# Tool: `TaskStop`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 0

## Change log

_Present since `2.1.110.610` or earlier; no changes observed in the archive window._

## Current definition

```json
{
  "name": "TaskStop",
  "description": "\n- Stops a running background task by its ID\n- Takes a task_id parameter identifying the task to stop\n- Returns a success or failure status\n- Use this tool when you need to terminate a long-running task\n",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "task_id": {
        "description": "The ID of the background task to stop",
        "type": "string"
      },
      "shell_id": {
        "description": "Deprecated: use task_id instead",
        "type": "string"
      }
    },
    "additionalProperties": false
  }
}
```
