---
name: direction-evolution
description: Updates cross-cycle direction memory and evidence-driven next-step plans after shortlisting, failed validation, or completed stages. Use after ideation or new results to decide what to pursue, avoid, or revise next.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Research Ideation, Persistent Memory, Evidence-Driven Iteration, Direction Selection, Problem Discovery]
dependencies: []
---

# Direction Evolution

Use this skill after ideation or after new evidence lands.

It combines two adjacent operating tasks:

- `memory-update`: preserve what the project learned about promising, failed, or ambiguous directions
- `stage-reflection`: convert completed stage results into concrete next-step updates

This is a post-cycle skill. It does not generate fresh ideas from scratch.

## Use When

- A shortlist or tournament has produced candidate directions
- A proposed direction failed validation and you want to preserve the failure mode
- You are revisiting a topic and need to remember what looked good, weak, or unresolved
- A baseline, ablation, new dataset, or new recipe has finished and you need an evidence-driven next step
- Two iterations in a row failed to improve the primary metric
- Results are suspicious, unstable, or hard to interpret

## Do Not Use When

- You still need to generate or score the directions themselves; use `brainstorming-research-ideas` or `idea-generation`
- You need novelty checking rather than post-cycle consolidation; use `novelty-assessment`
- You are trying to explain an anomaly with competing mechanisms; use `hypothesis-generation`

## Inputs

Possible inputs include:

- `outputs/<topic-slug>/direction_shortlist.md`
- `outputs/<topic-slug>/problem_map.md`
- `outputs/<topic-slug>/research_log.md`
- `outputs/<topic-slug>/novelty_report.json`
- stage logs, reviewer notes, or failure summaries
- stage name or index
- commands run and key parameters
- metrics versus baseline
- artifact paths for logs, plots, tables, or checkpoints

Existing outputs if present:

- `memory/ideation-memory.md`
- `outputs/<topic-slug>/stage_reflection.json`

## References

- Memory schema: `references/ideation-memory-schema.md`
- Plan update schema: `references/plan-update-schema.md`
- Starter templates:
  - `templates/ideation-memory.md`
  - `templates/plan-update.json`

## Workflow

### Step 1: Choose the Mode

Use `memory-update` when the main job is to preserve directional judgment.

Use `stage-reflection` when the main job is to decide what the latest evidence implies for the next stage.

Use both when a completed stage both changes the plan and teaches a durable lesson worth preserving.

### Step 2: Memory Update

Update `memory/ideation-memory.md` with:

1. promising directions
2. failed or deprioritized directions
3. open questions worth revisiting
4. decision heuristics learned from the cycle

Capture only the signals that change future choices:

- target problem or gap
- proposed mechanism or angle
- novelty risk
- feasibility risk
- strongest supporting evidence
- strongest disqualifying evidence

### Step 3: Stage Reflection

When stage evidence exists, produce `outputs/<topic-slug>/stage_reflection.json` using the plan-update schema.

First classify the issue:

- unmet success signal
- suspicious or mismatched metric
- confounded change
- missing baseline or ablation
- data quality issue
- infrastructure or runtime bottleneck
- evidence still too weak to decide

Then propose only justified updates:

- completed work
- unmet success signals
- stage modifications
- new stages
- concise todo updates

### Step 4: Link the Two Outputs

If stage reflection reveals a deeper dead end or reusable lesson, also update `memory/ideation-memory.md`.

If memory review shows repeated failure patterns, use that to constrain future stage updates.

## Output Artifacts

- `memory/ideation-memory.md`
- `outputs/<topic-slug>/stage_reflection.json`
- optional:
  - `outputs/<topic-slug>/failure_review.md`
  - `outputs/<topic-slug>/pivot_candidates.md`

## Rules

- Record explanations, not just verdicts
- Preserve ambiguous directions when evidence is incomplete
- Separate "bad idea" from "bad current instantiation"
- Evidence first, novelty second
- Do not propose a new stage if the current evidence cannot justify it
- Prefer minimal, diagnostic next steps over broad restarts
- Treat this skill as post-cycle consolidation, not as initial ideation

## Related Skills

- In this repository: [idea-generation](../idea-generation/), [novelty-assessment](../novelty-assessment/), [scientific-critical-thinking](../scientific-critical-thinking/)
- Use this skill after ideation or after completed stages to keep direction selection cumulative rather than forgetful
