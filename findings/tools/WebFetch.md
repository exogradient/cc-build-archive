# Tool: `WebFetch`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 1

## Change log

- `2.1.154.608` — ~ `description`

  <details><summary>description diff (1479 → 374 chars)</summary>

  ```diff
  -IMPORTANT: WebFetch WILL FAIL for authenticated or private URLs.
  -Before using this tool, check if the URL points to an authenticated service (e.g.
  -Google Docs, Confluence, Jira, GitHub).
  -If so, look for a specialized MCP tool that provides authenticated access.
  +Fetches a URL, converts the page to markdown, and answers `prompt` against it using a small fast model.
   
  -- Fetches content from a specified URL and processes it using an AI model
  -- Takes a URL and a prompt as input
  -- Fetches the URL content, converts HTML to markdown
  -- Processes the content with the prompt using a small, fast model
  -- Returns the model's response about the content
  -- Use this tool when you need to retrieve and analyze web content
  -
  -Usage notes:
    … (+15 more diff lines — see the version's tools.diff)
  ```

  </details>

## Current definition

```json
{
  "name": "WebFetch",
  "description": "Fetches a URL, converts the page to markdown, and answers `prompt` against it using a small fast model.\n\n- Fails on authenticated/private URLs \u2014 use an authenticated MCP tool or `gh` for those instead.\n- HTTP is upgraded to HTTPS. Cross-host redirects are returned to you rather than followed; call again with the redirect URL.\n- Responses are cached for 15 minutes per URL.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "url": {
        "description": "The URL to fetch content from",
        "type": "string",
        "format": "uri"
      },
      "prompt": {
        "description": "The prompt to run on the fetched content",
        "type": "string"
      }
    },
    "required": [
      "url",
      "prompt"
    ],
    "additionalProperties": false
  }
}
```
