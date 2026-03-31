# Template Pack Reference

This reference defines the minimal package needed for code-constrained ideation.

## Required Files

- `experiment.py`: the executable core of the template
- `prompt.json`: the system framing and task description
- `seed_ideas.json`: starting ideas or precedent concepts

## Optional But Valuable

- `plot.py`: shows which metrics or visualizations already matter
- `run_0/` or baseline result folders: expose expected outputs and bottlenecks
- `ideas.json`: prior generated ideas, including rejected or weak ones
- logs, reviewer scores, or retrospective notes

## Minimal Directory Shape

```text
template-name/
  experiment.py
  prompt.json
  seed_ideas.json
  plot.py
  run_0/
  ideas.json
```

Only the first three are required for this skill. Everything else improves gap finding and prioritization.

## What To Read First

1. `prompt.json`
   Read the task description to understand the intended research question.
2. `experiment.py`
   Identify editable seams, available metrics, assumptions, and hard constraints.
3. `seed_ideas.json`
   Map which idea families are already covered so you avoid trivial duplicates.

## Gap-Finding Surfaces

When reading the template, inspect these surfaces:

- architecture or mechanism knobs
- objective, loss, or reward design
- data sampling and augmentation policy
- training schedule and optimization dynamics
- evaluation slices and missing baselines
- robustness, transfer, or out-of-distribution behavior
- compute, latency, or memory tradeoffs
- instrumentation gaps: what the current logs cannot explain

## Good Idea Shapes

The strongest ideas usually do one of these:

- expose a hidden failure regime the template currently misses
- add a targeted intervention on a concrete mechanism in the code
- turn an observed anomaly into a testable explanation
- widen the evaluation claim without exploding implementation cost
- replace a weak heuristic with a more interpretable mechanism

## Weak Idea Shapes

Avoid ideas that are mostly:

- random parameter tuning without a scientific question
- requests for entirely new infrastructure outside the template scope
- cosmetic metric additions with no change in decision quality
- near-duplicates of seed ideas with renamed terminology

## Suggested Working Files

- `outputs/<topic-slug>/template_gap_map.md`: missing tests, questionable assumptions, suspicious metrics
- `outputs/<topic-slug>/idea_backlog.md`: raw ideas tied to specific code seams
- `outputs/<topic-slug>/direction_shortlist.md`: ranked finalists with cost and novelty notes
- `outputs/<topic-slug>/top_idea.json`: one finalized idea using the standard schema

## Standard Idea Schema

```json
{
  "Name": "short_snake_case_name",
  "Title": "Readable title",
  "Experiment": "Implementation and evaluation plan grounded in the template.",
  "Interestingness": 1,
  "Feasibility": 1,
  "Novelty": 1
}
```
