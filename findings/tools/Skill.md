# Tool: `Skill`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 1

## Change log

- `2.1.111.b2b` — ~ `description`; ~ `input_schema.properties.skill.description`

  <details><summary>description diff (1272 → 1315 chars)</summary>

  ```diff
   
  -When users reference a "slash command" or "/<something>" (e.g., "/commit", "/review-pr"), they are referring to a skill.
  +When users reference a "slash command" or "/<something>", they are referring to a skill.
   Use this tool to invoke it.
   How to invoke:
  -- Use this tool with the skill name and optional arguments
  -- Examples:
  -  - `skill: "pdf"` - invoke the pdf skill
  -  - `skill: "commit", args: "-m 'Fix bug'"` - invoke with arguments
  -  - `skill: "review-pr", args: "123"` - invoke with arguments
  -  - `skill: "ms-office-suite:pdf"` - invoke using fully qualified name
  +- Set `skill` to the exact name of an available skill (no leading slash).
  +For plugin-namespaced skills use the fully qualified `plugin:skill` form.
  +- Set `args` to pass optional arguments.
    … (+5 more diff lines — see the version's tools.diff)
  ```

  </details>

## Current definition

```json
{
  "name": "Skill",
  "description": "Execute a skill within the main conversation\n\nWhen users ask you to perform tasks, check if any of the available skills match. Skills provide specialized capabilities and domain knowledge.\n\nWhen users reference a \"slash command\" or \"/<something>\", they are referring to a skill. Use this tool to invoke it.\n\nHow to invoke:\n- Set `skill` to the exact name of an available skill (no leading slash). For plugin-namespaced skills use the fully qualified `plugin:skill` form.\n- Set `args` to pass optional arguments.\n\nImportant:\n- Available skills are listed in system-reminder messages in the conversation\n- Only invoke a skill that appears in that list, or one the user explicitly typed as `/<name>` in their message. Never guess or invent a skill name from training data; otherwise do not call this tool\n- When a skill matches the user's request, this is a BLOCKING REQUIREMENT: invoke the relevant Skill tool BEFORE generating any other response about the task\n- NEVER mention a skill without actually calling this tool\n- Do not invoke a skill that is already running\n- Do not use this tool for built-in CLI commands (like /help, /clear, etc.)\n- If you see a <command-name> tag in the current conversation turn, the skill has ALREADY been loaded - follow the instructions directly instead of calling this tool again\n",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "skill": {
        "description": "The name of a skill from the available-skills list. Do not guess names.",
        "type": "string"
      },
      "args": {
        "description": "Optional arguments for the skill",
        "type": "string"
      }
    },
    "required": [
      "skill"
    ],
    "additionalProperties": false
  }
}
```
