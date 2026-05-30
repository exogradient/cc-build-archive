# Tool: `CronDelete`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes

## Change log

_Present since `2.1.110.610` or earlier; no changes observed in the archive window._

## Current definition

```json
{
  "name": "CronDelete",
  "description": "Cancel a cron job previously scheduled with CronCreate. Removes it from .claude/scheduled_tasks.json (durable jobs) or the in-memory session store (session-only jobs).",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "id": {
        "description": "Job ID returned by CronCreate.",
        "type": "string"
      }
    },
    "required": [
      "id"
    ],
    "additionalProperties": false
  }
}
```
