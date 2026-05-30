# Tool: `WebSearch`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 1

## Change log

- `2.1.154.608` — ~ `description`

  <details><summary>description diff (1316 → 306 chars)</summary>

  ```diff
  +Search the web.
  +Returns result blocks with titles and URLs.
  +US-only.
   
  -- Allows Claude to search the web and use the results to inform responses
  -- Provides up-to-date information for current events and recent data
  -- Returns search result information formatted as search result blocks, including links as markdown hyperlinks
  -- Use this tool for accessing information beyond Claude's knowledge cutoff
  -- Searches are performed automatically within a single API call
  -
  -CRITICAL REQUIREMENT - You MUST follow this:
  -  - After answering the user's question, you MUST include a "Sources:" section at the end of your response
  -  - In the Sources section, list all relevant URLs from the search results as markdown hyperlinks: [Title](URL)
  -  - This is MANDATORY - never skip including sources in your response
    … (+20 more diff lines — see the version's tools.diff)
  ```

  </details>

## Current definition

```json
{
  "name": "WebSearch",
  "description": "Search the web. Returns result blocks with titles and URLs. US-only.\n\n- The current month is May 2026 \u2014 use this when searching for recent information.\n- `allowed_domains` / `blocked_domains` filter results.\n- After answering from results, end with a \"Sources:\" list of the URLs you used as markdown links.",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "query": {
        "description": "The search query to use",
        "type": "string",
        "minLength": 2
      },
      "allowed_domains": {
        "description": "Only include search results from these domains",
        "type": "array",
        "items": {
          "type": "string"
        }
      },
      "blocked_domains": {
        "description": "Never include search results from these domains",
        "type": "array",
        "items": {
          "type": "string"
        }
      }
    },
    "required": [
      "query"
    ],
    "additionalProperties": false
  }
}
```
