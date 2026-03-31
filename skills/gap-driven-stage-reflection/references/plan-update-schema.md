# Plan Update Schema

This schema is for reflection after a completed stage, not for initial ideation.

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

## Field Guidance

- `completed`: stages or checks that are now done
- `unmet_success_signals`: explicit signals that failed
- `skill_suggestions`: optional follow-up skills to load next
- `stage_modifications`: edits to existing stages
- `new_stages`: only genuinely new work justified by the evidence
- `todo_updates`: concise actionable checklist updates

## Reflection Triggers

Run this reflection when:

- a baseline is complete
- a new dataset/model/recipe was introduced
- two iterations failed in a row
- results are unstable or suspicious
- a new artifact reveals a hidden failure mode

## Good Modifications

- "Split the stage into baseline reproduction and method delta to remove confounding."
- "Add slice-level evaluation because aggregate accuracy hides the failure regime."
- "Drop this branch and add a simpler control because the current change is uninterpretable."

## Bad Modifications

- "Try more hyperparameters."
- "Run more experiments."
- "Improve the model."

Those are too vague to support disciplined iteration.
