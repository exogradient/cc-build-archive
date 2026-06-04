# Tool: `Bash`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 6

## Change log

- `2.1.116.f49` — ~ `description`

  <details><summary>description diff (9993 → 10167 chars)</summary>

  ```diff
   You may use `cd` if the User explicitly requests it.
  +In particular, never prepend `cd <current-directory>` to a `git` command — `git` already operates on the current working tree, and the compound triggers a permission prompt.
    - You may specify an optional timeout in milliseconds (up to 600000ms / 10 minutes).
  ```

  </details>
- `2.1.129.49a` — ~ `description`

  <details><summary>description diff (10167 → 10189 chars)</summary>

  ```diff
      - Create the commit with a message ending with:
  -   Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
  +   Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
      - Run git status after the commit completes to verify success.
   
  -   Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
  +   Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
      EOF
  ```

  </details>
- `2.1.138.1a3` — ~ `input_schema.properties.run_in_background.description`
- `2.1.142.1aa` — ~ `description`

  <details><summary>description diff (10189 → 10191 chars)</summary>

  ```diff
   - NEVER run additional commands to read or explore code, besides git bash commands
  -- NEVER use the TodoWrite or Agent tools
  +- NEVER use the TaskCreate or Agent tools
   - DO NOT push to the remote repository unless the user explicitly asks you to do so
   Important:
  -- DO NOT use the TodoWrite or Agent tools
  +- DO NOT use the TaskCreate or Agent tools
   - Return the PR URL when you're done, so the user can see it
  ```

  </details>
- `2.1.154.608` — ~ `description`

  <details><summary>description diff (10191 → 1234 chars)</summary>

  ```diff
  -Executes a given bash command and returns its output.
  +Executes a bash command and returns its output.
   
  -The working directory persists between commands, but shell state does not.
  -The shell environment is initialized from the user's profile (bash or zsh).
  +- Working directory persists between calls, but prefer absolute paths — `cd` in a compound command can trigger a permission prompt.
  +Shell state (env vars, functions) does not persist; the shell is initialized from the user's profile.
  +- IMPORTANT: Avoid using this tool to run `find`, `grep`, `cat`, `head`, `tail`, `sed`, `awk`, or `echo` commands, unless explicitly instructed or after you have verified that a dedicated tool cannot accomplish your task.
  +Instead, use the appropriate dedicated tool as this will provide a much better experience for the user.
  +- `timeout` is in milliseconds: default 120000, max 600000.
  +- `run_in_background` runs the command detached: it keeps running across turns and re-invokes you when it exits.
  +No `&` needed.
   
  -IMPORTANT: Avoid using this tool to run `find`, `grep`, `cat`, `head`, `tail`, `sed`, `awk`, or `echo` commands, unless explicitly instructed or after you have verified that a dedicated tool cannot accomplish your task.
    … (+161 more diff lines — see the version's tools.diff)
  ```

  </details>
- `2.1.163.7c7` — ~ `description`

  <details><summary>description diff (1234 → 1218 chars)</summary>

  ```diff
   Shell state (env vars, functions) does not persist; the shell is initialized from the user's profile.
  -- IMPORTANT: Avoid using this tool to run `find`, `grep`, `cat`, `head`, `tail`, `sed`, `awk`, or `echo` commands, unless explicitly instructed or after you have verified that a dedicated tool cannot accomplish your task.
  +- IMPORTANT: Avoid using this tool to run `cat`, `head`, `tail`, `sed`, `awk`, or `echo` commands, unless explicitly instructed or after you have verified that a dedicated tool cannot accomplish your task.
   Instead, use the appropriate dedicated tool as this will provide a much better experience for the user.
  ```

  </details>

## Current definition

```json
{
  "name": "Bash",
  "description": "Executes a bash command and returns its output.\n\n- Working directory persists between calls, but prefer absolute paths \u2014 `cd` in a compound command can trigger a permission prompt. Shell state (env vars, functions) does not persist; the shell is initialized from the user's profile.\n- IMPORTANT: Avoid using this tool to run `cat`, `head`, `tail`, `sed`, `awk`, or `echo` commands, unless explicitly instructed or after you have verified that a dedicated tool cannot accomplish your task. Instead, use the appropriate dedicated tool as this will provide a much better experience for the user.\n- `timeout` is in milliseconds: default 120000, max 600000.\n- `run_in_background` runs the command detached: it keeps running across turns and re-invokes you when it exits. No `&` needed.\n\n# Git\n- Interactive flags (`-i`, e.g. `git rebase -i`, `git add -i`) are not supported in this environment.\n- Use the `gh` CLI for GitHub operations (PRs, issues, API).\n- Commit or push only when the user asks. If on the default branch, branch first.\n- End git commit messages with:\nCo-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>\n- End PR bodies with:\n\ud83e\udd16 Generated with [Claude Code](https://claude.com/claude-code)",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "command": {
        "description": "The command to execute",
        "type": "string"
      },
      "timeout": {
        "description": "Optional timeout in milliseconds (max 600000)",
        "type": "number"
      },
      "description": {
        "description": "Clear, concise description of what this command does in active voice. Never use words like \"complex\" or \"risk\" in the description - just describe what it does.\n\nFor simple commands (git, npm, standard CLI tools), keep it brief (5-10 words):\n- ls \u2192 \"List files in current directory\"\n- git status \u2192 \"Show working tree status\"\n- npm install \u2192 \"Install package dependencies\"\n\nFor commands that are harder to parse at a glance (piped commands, obscure flags, etc.), add enough context to clarify what it does:\n- find . -name \"*.tmp\" -exec rm {} \\; \u2192 \"Find and delete all .tmp files recursively\"\n- git reset --hard origin/main \u2192 \"Discard all local changes and match remote main\"\n- curl -s url | jq '.data[]' \u2192 \"Fetch JSON from URL and extract data array elements\"",
        "type": "string"
      },
      "run_in_background": {
        "description": "Set to true to run this command in the background.",
        "type": "boolean"
      },
      "dangerouslyDisableSandbox": {
        "description": "Set this to true to dangerously override sandbox mode and run commands without sandboxing.",
        "type": "boolean"
      }
    },
    "required": [
      "command"
    ],
    "additionalProperties": false
  }
}
```
