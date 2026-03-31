# Plan Update Schema

Use this schema when `direction-evolution` runs in `stage-reflection` mode.

## Required JSON Shape

```json
{
  "completed": ["..."],
  "unmet_success_signals": ["..."],
  "skill_suggestions": ["..."],
  "stage_modifications": [
    {"stage": "Stage name or index", "change": "What to adjust and why"}
  ],
  "new_stages": [
    {
      "title": "...",
      "goal": "...",
      "success_signals": ["..."],
      "what_to_run": ["..."],
      "expected_artifacts": ["..."]
    }
  ],
  "todo_updates": ["..."]
}
```

## Good Modifications

- add a missing control or baseline
- isolate a confounded variable
- narrow the question to a falsifiable sub-problem
- add one analysis that explains suspicious behavior
- stop a weak direction and open a more justified next stage
