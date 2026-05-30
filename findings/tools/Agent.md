# Tool: `Agent`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 4

## Change log

- `2.1.111.b2b` — ~ `description`

  <details><summary>description diff (6839 → 6839 chars)</summary>

  ```diff
   Available agent types and the tools they have access to:
  -- general-purpose: General-purpose agent for researching complex questions, searching for code, and executing multi-step tasks.
  -When you are searching for a keyword or file and are not confident that you will find the right match in the first few tries use this agent to perform the search for you.
  -(Tools: *)
  -- statusline-setup: Use this agent to configure the user's Claude Code status line setting.
  -(Tools: Read, Edit)
   - Explore: Fast agent specialized for exploring codebases.
   (Tools: All tools except Agent, ExitPlanMode, Edit, Write, NotebookEdit)
  +- general-purpose: General-purpose agent for researching complex questions, searching for code, and executing multi-step tasks.
  +When you are searching for a keyword or file and are not confident that you will find the right match in the first few tries use this agent to perform the search for you.
  +(Tools: *)
   - Plan: Software architect agent for designing implementation plans.
   (Tools: All tools except Agent, ExitPlanMode, Edit, Write, NotebookEdit)
  +- statusline-setup: Use this agent to configure the user's Claude Code status line setting.
    … (+2 more diff lines — see the version's tools.diff)
  ```

  </details>
- `2.1.128.9fd` — ~ `description`

  <details><summary>description diff (6839 → 6960 chars)</summary>

  ```diff
   Available agent types and the tools they have access to:
  -- Explore: Fast agent specialized for exploring codebases.
  -Use this when you need to quickly find files by patterns (eg.
  -"src/components/**/*.tsx"), search code for keywords (eg.
  -"API endpoints"), or answer questions about the codebase (eg.
  -"how do API endpoints work?").
  -When calling this agent, specify the desired thoroughness level: "quick" for basic searches, "medium" for moderate exploration, or "very thorough" for comprehensive analysis across multiple locations and naming conventions.
  +- Explore: Fast read-only search agent for locating code.
  +Use it to find files by pattern (eg.
  +"src/components/**/*.tsx"), grep for symbols or keywords (eg.
  +"API endpoints"), or answer "where is X defined / which files reference Y." Do NOT use it for code review, design-doc auditing, cross-file consistency checks, or open-ended analysis — it reads excerpts rather than whole files and will miss content past its read window.
  +When calling, specify search breadth: "quick" for a single targeted lookup, "medium" for moderate exploration, or "very thorough" to search across multiple locations and naming conventions.
   (Tools: All tools except Agent, ExitPlanMode, Edit, Write, NotebookEdit)
  ```

  </details>
- `2.1.139.b1c` — ~ `description`

  <details><summary>description diff (6960 → 7093 chars)</summary>

  ```diff
   Available agent types and the tools they have access to:
  +- claude: Catch-all for any task that doesn't fit a more specific agent.
  +FleetView's default when no agent name is typed.
  +(Tools: *)
   - Explore: Fast read-only search agent for locating code.
  ```

  </details>
- `2.1.154.608` — ~ `description`

  <details><summary>description diff (7093 → 2681 chars)</summary>

  ```diff
   (Tools: *)
  -- Explore: Fast read-only search agent for locating code.
  -Use it to find files by pattern (eg.
  -"src/components/**/*.tsx"), grep for symbols or keywords (eg.
  -"API endpoints"), or answer "where is X defined / which files reference Y." Do NOT use it for code review, design-doc auditing, cross-file consistency checks, or open-ended analysis — it reads excerpts rather than whole files and will miss content past its read window.
  -When calling, specify search breadth: "quick" for a single targeted lookup, "medium" for moderate exploration, or "very thorough" to search across multiple locations and naming conventions.
  +- Explore: Read-only search agent for broad fan-out searches — when answering means sweeping many files, directories, or naming conventions and you only need the conclusion, not the file dumps.
  +It reads excerpts rather than whole files, so it locates code; it doesn't review or audit it.
  +Specify search breadth: "medium" for moderate exploration, "very thorough" for multiple locations and naming conventions.
   (Tools: All tools except Agent, ExitPlanMode, Edit, Write, NotebookEdit)
   
  -## When not to use
  +## When to use
   
    … (+84 more diff lines — see the version's tools.diff)
  ```

  </details>

## Current definition

```json
{
  "name": "Agent",
  "description": "Launch a new agent to handle complex, multi-step tasks. Each agent type has specific capabilities and tools available to it.\n\nAvailable agent types and the tools they have access to:\n- claude: Catch-all for any task that doesn't fit a more specific agent. FleetView's default when no agent name is typed. (Tools: *)\n- Explore: Read-only search agent for broad fan-out searches \u2014 when answering means sweeping many files, directories, or naming conventions and you only need the conclusion, not the file dumps. It reads excerpts rather than whole files, so it locates code; it doesn't review or audit it. Specify search breadth: \"medium\" for moderate exploration, \"very thorough\" for multiple locations and naming conventions. (Tools: All tools except Agent, ExitPlanMode, Edit, Write, NotebookEdit)\n- general-purpose: General-purpose agent for researching complex questions, searching for code, and executing multi-step tasks. When you are searching for a keyword or file and are not confident that you will find the right match in the first few tries use this agent to perform the search for you. (Tools: *)\n- Plan: Software architect agent for designing implementation plans. Use this when you need to plan the implementation strategy for a task. Returns step-by-step plans, identifies critical files, and considers architectural trade-offs. (Tools: All tools except Agent, ExitPlanMode, Edit, Write, NotebookEdit)\n- statusline-setup: Use this agent to configure the user's Claude Code status line setting. (Tools: Read, Edit)\n\nWhen using the Agent tool, specify a subagent_type parameter to select which agent type to use. If omitted, the general-purpose agent is used.\n\n## When to use\n\nReach for this when the task matches an available agent type, when you have independent work to run in parallel, or when answering would mean reading across several files \u2014 delegate it and you keep the conclusion, not the file dumps. For a single-fact lookup where you already know the file, symbol, or value, search directly. Once you've delegated a search, don't also run it yourself \u2014 wait for the result.\n\n- The agent's final message is returned to you as the tool result; it is not shown to the user \u2014 relay what matters.\n- Use SendMessage with the agent's ID or name to continue a previously spawned agent with its context intact; a new Agent call starts fresh.\n- `isolation: \"worktree\"` gives the agent its own git worktree (auto-cleaned if unchanged).\n- `run_in_background: true` runs the agent asynchronously; you'll be notified when it completes.\n- When you launch multiple agents for independent work, send them in a single message with multiple tool uses so they run concurrently",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "description": {
        "description": "A short (3-5 word) description of the task",
        "type": "string"
      },
      "prompt": {
        "description": "The task for the agent to perform",
        "type": "string"
      },
      "subagent_type": {
        "description": "The type of specialized agent to use for this task",
        "type": "string"
      },
      "model": {
        "description": "Optional model override for this agent. Takes precedence over the agent definition's model frontmatter. If omitted, uses the agent definition's model, or inherits from the parent.",
        "type": "string",
        "enum": [
          "sonnet",
          "opus",
          "haiku"
        ]
      },
      "run_in_background": {
        "description": "Set to true to run this agent in the background. You will be notified when it completes.",
        "type": "boolean"
      },
      "isolation": {
        "description": "Isolation mode. \"worktree\" creates a temporary git worktree so the agent works on an isolated copy of the repo.",
        "type": "string",
        "enum": [
          "worktree"
        ]
      }
    },
    "required": [
      "description",
      "prompt"
    ],
    "additionalProperties": false
  }
}
```
