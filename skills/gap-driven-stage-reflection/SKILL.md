---
name: gap-driven-stage-reflection
description: Reflects on baseline or stage results to identify unmet success signals, suspicious outcomes, and next-stage changes. Use when results have landed and you need evidence-driven problem discovery instead of blindly continuing the plan.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Problem Discovery, Evidence-Driven Iteration, Experiment Reflection, Research Planning]
dependencies: []
---

# Gap-Driven Stage Reflection

Use completed stage results to discover what the current plan is missing.

This skill is for checkpoints after a meaningful baseline, ablation, new dataset, or new training recipe. It converts outputs into concrete plan updates instead of letting iteration drift.

## Use When

- A baseline has finished and you now have a real reference point
- Two iterations in a row failed to improve the primary metric
- Results are suspicious, unstable, or hard to interpret
- A new recipe, model, or dataset may have introduced confounds

## Inputs

- Stage name or index
- Stage intent
- Commands run and key parameters
- Metrics versus baseline
- Artifact paths for logs, plots, tables, or checkpoints
- Which success signals were met or missed

## References

- Reflection schema: `references/plan-update-schema.md`
- Starter JSON: `templates/plan-update.json`

## Workflow

### Step 1: Audit the Evidence

Before proposing any next step, check:

- what changed relative to baseline
- whether only one major variable changed
- whether the primary metric moved in a meaningful way
- whether variance, instability, or missing controls weaken the conclusion

### Step 2: Identify the Real Problem

Do not jump directly from "metric did not improve" to "try another method."

First classify the issue:

- unmet success signal
- suspicious or mismatched metric
- confounded change
- missing baseline or ablation
- data quality issue
- infrastructure or runtime bottleneck
- evidence still too weak to decide

### Step 3: Propose Plan Updates

Produce a compact JSON update with this schema:

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

Empty arrays are valid. If no changes are justified, return empty arrays rather than inventing work.

### Step 4: Prefer Gap-Closing Changes

The best updates usually do one of these:

- add a missing control or baseline
- isolate a confounded variable
- narrow the question to a falsifiable sub-problem
- add one analysis that explains suspicious behavior
- stop a weak direction and open a more justified next stage

### Step 5: Revise the Plan

Use the JSON result to update:

- `outputs/<topic-slug>/research_log.md`
- `outputs/<topic-slug>/direction_shortlist.md`
- `outputs/<topic-slug>/stage_reflection.json`

If the stage revealed a deeper dead end, also update `memory/ideation-memory.md`.

## Rules

- Evidence first, novelty second
- Do not propose a new stage if the current evidence cannot justify it
- Prefer minimal, diagnostic next steps over broad restarts
- Treat suspicious results as a problem to explain, not as a win to report
- Keep changes traceable to specific unmet signals or observed anomalies

## Related Skills

- In this repository: [template-grounded-ideation](../template-grounded-ideation/), [scientific-critical-thinking](../scientific-critical-thinking/), [ideation-memory-evolution](../ideation-memory-evolution/)
- Use this skill after experiments or structured ideation when new evidence changes the direction
