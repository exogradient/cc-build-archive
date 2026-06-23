# Tool: `AskUserQuestion`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: **no** (removed)
- Definition changes: 3

## Change log

- `2.1.152.8a5` — ~ `description`

  <details><summary>description diff (1074 → 960 chars)</summary>

  ```diff
   
  -Plan mode note: In plan mode, use this tool to clarify requirements or choose between approaches BEFORE finalizing your plan.
  -Do NOT use this tool to ask "Is my plan ready?" or "Should I proceed?" - use ExitPlanMode for plan approval.
  -IMPORTANT: Do not reference "the plan" in your questions (e.g., "Do you have feedback about the plan?", "Does the plan look good?") because the user cannot see the plan in the UI until you call ExitPlanMode.
  -If you need plan approval, use ExitPlanMode instead.
  +Plan mode note: To switch into plan mode, use EnterPlanMode (not this tool).
  +Once in plan mode, use this tool to clarify requirements or choose between approaches BEFORE finalizing your plan.
  +Do NOT use this tool to ask "Is my plan ready?", "Should I proceed?", or otherwise reference "the plan" in questions — the user cannot see the plan until you call ExitPlanMode for approval.
   
  ```

  </details>
- `2.1.153.9bb` — ~ `description`

  <details><summary>description diff (960 → 1649 chars)</summary>

  ```diff
   
  +Preview feature:
  +Use the optional `preview` field on options when presenting concrete artifacts that users need to visually compare:
  +- ASCII mockups of UI layouts or components
  +- Code snippets showing different implementations
  +- Diagram variations
  +- Configuration examples
  +
  +Preview content is rendered as markdown in a monospace box.
  +Multi-line text with newlines is supported.
  +When any option has a preview, the UI switches to a side-by-side layout with a vertical option list on the left and preview on the right.
  +Do not use previews for simple preference questions where labels and descriptions suffice.
  +Note: previews are only supported for single-select questions (not multiSelect).
  +
  ```

  </details>
- `2.1.154.608` — ~ `description`

  <details><summary>description diff (1649 → 1786 chars)</summary>

  ```diff
  -Use this tool when you need to ask the user questions during execution.
  -This allows you to:
  -1.
  -Gather user preferences or requirements
  -2.
  -Clarify ambiguous instructions
  -3.
  -Get decisions on implementation choices as you work
  -4.
  -Offer choices to the user about what direction to take.
  +Use this tool only when you are blocked on a decision that is genuinely the user's to make: one you cannot resolve from the request, the code, or sensible defaults.
   
   Do NOT use this tool to ask "Is my plan ready?", "Should I proceed?", or otherwise reference "the plan" in questions — the user cannot see the plan until you call ExitPlanMode for approval.
  +
    … (+3 more diff lines — see the version's tools.diff)
  ```

  </details>
- `2.1.187.cfe` — removed.
