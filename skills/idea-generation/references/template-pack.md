# Template Pack Reference

Use this reference when `idea-generation` runs in `template-grounded` mode.

## Required Files

- `experiment.py`: executable core of the scaffold
- `prompt.json`: system framing and task description
- `seed_ideas.json`: precedent ideas or archive seeds

## Optional but Valuable

- `plot.py`
- `run_0/` or other baseline result folders
- `ideas.json`
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

Only the first three are required for `template-grounded` mode.

## What to Read First

1. `prompt.json`
2. `experiment.py`
3. `seed_ideas.json`

## Gap-Finding Surfaces

- architecture or mechanism knobs
- objective, loss, or reward design
- data sampling and augmentation policy
- training schedule and optimization dynamics
- evaluation slices and missing baselines
- robustness, transfer, or out-of-distribution behavior
- compute, latency, or memory tradeoffs
- instrumentation gaps

## Weak Idea Shapes

- random parameter tuning without a scientific question
- requests for entirely new infrastructure outside the scaffold scope
- cosmetic metric additions with no decision impact
- near-duplicates of seed ideas
