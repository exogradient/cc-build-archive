# Tool: `SendMessage`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- First seen: `2.1.186.75e` (2026-06-22T18:04:10)
- Currently present: yes

## Change log

- `2.1.186.75e` — added.

## Current definition

```json
{
  "name": "SendMessage",
  "description": "# SendMessage\n\nSend a message to another agent.\n\n```json\n{\"to\": \"researcher\", \"summary\": \"assign task 1\", \"message\": \"start on task #1\"}\n```\n\n| `to` | |\n|---|---|\n| `\"researcher\"` | Teammate by name |\n| `\"main\"` | The main conversation (background subagents only) |\n\nYour plain text output is NOT visible to other agents \u2014 to communicate, you MUST call this tool. Messages from teammates are delivered automatically; you don't check an inbox. Refer to active teammates by name; to resume a completed background agent, use the `agentId` (format `a...-...`) from its spawn result. When relaying, don't quote the original \u2014 it's already rendered to the user.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "to": {
        "description": "Recipient: teammate name",
        "type": "string"
      },
      "summary": {
        "description": "A 5-10 word summary shown as a preview in the UI (required when message is a string)",
        "type": "string",
        "maxLength": 200
      },
      "message": {
        "description": "Plain text message content",
        "type": "string"
      }
    },
    "required": [
      "to",
      "message"
    ],
    "additionalProperties": false
  }
}
```
