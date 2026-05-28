# Tool: `ScheduleWakeup`

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

- Currently present: yes
- Definition changes: 1

## Change log

- `2.1.141.e27` — ~ `description`

## Current definition

```json
{
  "name": "ScheduleWakeup",
  "description": "Schedule when to resume work in /loop dynamic mode \u2014 the user invoked /loop without an interval, asking you to self-pace iterations of a specific task.\n\nDo NOT schedule a short-interval wakeup to poll for background work you started \u2014 when harness-tracked work finishes, you are re-invoked automatically, so polling is wasted. Instead schedule a long fallback (1200s+) so the loop survives if the work hangs or never notifies. The exception is external work the harness cannot track (a CI run, a deploy, a remote queue) \u2014 there, pick a delay matched to how fast that state actually changes.\n\nPass the same /loop prompt back via `prompt` each turn so the next firing repeats the task. For an autonomous /loop (no user prompt), pass the literal sentinel `<<autonomous-loop-dynamic>>` as `prompt` instead \u2014 the runtime resolves it back to the autonomous-loop instructions at fire time. (There is a similar `<<autonomous-loop>>` sentinel for CronCreate-based autonomous loops; do not confuse the two \u2014 ScheduleWakeup always uses the `-dynamic` variant.) Omit the call to end the loop.\n\n## Picking delaySeconds\n\nThe Anthropic prompt cache has a 5-minute TTL. Sleeping past 300 seconds means the next wake-up reads your full conversation context uncached \u2014 slower and more expensive. So the natural breakpoints:\n\n- **Under 5 minutes (60s\u2013270s)**: cache stays warm. Right for actively polling external state the harness can't notify you about \u2014 a CI run, a deploy, a remote queue.\n- **5 minutes to 1 hour (300s\u20133600s)**: pay the cache miss. Right when there's no point checking sooner \u2014 waiting on something that takes minutes to change, genuinely idle, or as the long fallback heartbeat when something else is the primary wake signal.\n\n**Don't pick 300s.** It's the worst-of-both: you pay the cache miss without amortizing it. If you're tempted to \"wait 5 minutes,\" either drop to 270s (stay in cache) or commit to 1200s+ (one cache miss buys a much longer wait). Don't think in round-number minutes \u2014 think in cache windows.\n\nFor idle ticks with no specific signal to watch, default to **1200s\u20131800s** (20\u201330 min). The loop checks back, you don't burn cache 12\u00d7 per hour for nothing, and the user can always interrupt if they need you sooner.\n\nThink about what you're actually waiting for, not just \"how long should I sleep.\" If you're polling a CI run that takes ~8 minutes, sleeping 60s burns the cache 8 times before it finishes \u2014 sleep ~270s twice instead.\n\nThe runtime clamps to [60, 3600], so you don't need to clamp yourself.\n\n## The reason field\n\nOne short sentence on what you chose and why. Goes to telemetry and is shown back to the user. \"watching CI run\" beats \"waiting.\" The user reads this to understand what you're doing without having to predict your cadence in advance \u2014 make it specific.\n",
  "input_schema": {
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "type": "object",
    "properties": {
      "delaySeconds": {
        "description": "Seconds from now to wake up. Clamped to [60, 3600] by the runtime.",
        "type": "number"
      },
      "reason": {
        "description": "One short sentence explaining the chosen delay. Goes to telemetry and is shown to the user. Be specific.",
        "type": "string"
      },
      "prompt": {
        "description": "The /loop input to fire on wake-up. Pass the same /loop input verbatim each turn so the next firing re-enters the skill and continues the loop. For autonomous /loop (no user prompt), pass the literal sentinel `<<autonomous-loop-dynamic>>` instead (the dynamic-pacing variant, not the CronCreate-mode `<<autonomous-loop>>`).",
        "type": "string"
      }
    },
    "required": [
      "delaySeconds",
      "reason",
      "prompt"
    ],
    "additionalProperties": false
  }
}
```
