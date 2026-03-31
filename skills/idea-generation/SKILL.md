---
name: idea-generation
description: Generates scored research proposals from either a topic-first prompt or a runnable experiment template, with iterative refinement and script-assisted novelty checks. Use when candidate directions need to become concrete, testable proposals.
version: 2.0.0
author: Research-Equality
license: MIT
tags: [Research Ideation, Idea Ranking, Template-Based Ideation, Novelty Assessment, Problem Discovery]
dependencies: []
---

# Idea Generation

Turn rough directions into concrete, testable proposals.

This skill now has two modes:

- `topic-first`: start from a topic, paper context, or partial concept
- `template-grounded`: start from a runnable scaffold such as `prompt.json` + `experiment.py` + `seed_ideas.json`

## Inputs

### Topic-First Mode

- A research area, task description, paper context, or existing concept
- Optional constraints such as venue, budget, dataset limits, or timeline

### Template-Grounded Mode

- Required template context:
  - `prompt.json`
  - `experiment.py`
  - `seed_ideas.json`
- Strongly recommended context:
  - baseline outputs such as `run_0/`, `final_info.json`, plots, logs, or reviewer notes
  - hard constraints such as budget, wall-clock limits, dataset restrictions, or forbidden dependencies

## Do Not Use When

- You need open-ended novelty frameworks before you even have candidate directions; use `creative-thinking-for-research` or `scientific-brainstorming`
- You only need a harsher novelty gate on an already-written proposal; use `novelty-assessment`
- You need post-evidence plan revision or long-term memory consolidation rather than proposal generation

## Scripts

### Novelty check against Semantic Scholar

```bash
python skills/idea-generation/scripts/novelty_check.py \
  --idea "Adaptive attention head pruning via gradient-guided importance" \
  --max-rounds 5 \
  --output outputs/adaptive-attention/novelty_report.json
```

Performs iterative literature search to assess whether an idea is likely to be novel.

## References

- Ideation prompts (generation, reflection, novelty): `references/ideation-prompts.md`
- Template pack structure: `references/template-pack.md`
- Starter files for template-grounded mode:
  - `templates/prompt.json`
  - `templates/seed_ideas.json`

## Workflow

### Step 1: Choose the Mode

Use `topic-first` when the input is mainly conceptual.

Use `template-grounded` when a runnable scaffold already exists and the main job is to find feasible gaps, intervention points, and next experiments inside that scaffold.

### Step 2: Generate 3-5 Candidate Proposals

For every candidate, produce:

- `Name`
- `Title`
- `Experiment`
- `Interestingness`
- `Feasibility`
- `Novelty`

#### Topic-First Path

- Translate the topic or partial concept into several candidate proposals
- Use the ideation prompt templates from `references/ideation-prompts.md`
- Prefer proposals that are simple, elegant, and testable

#### Template-Grounded Path

- Read the template pack before generating ideas
- Surface a `template_gap_map.md` of hidden assumptions, missing baselines, narrow evaluation slices, underused code seams, or suspicious failure modes
- Generate only ideas that fit the code, data, and resource constraints already present

### Step 3: Iterative Refinement

For each promising idea:

1. Critique significance, novelty, feasibility, and clarity
2. In template-grounded mode, also check whether the idea is too close to a seed or archived attempt
3. Simplify overly ambitious plans
4. Stop when the idea has converged

### Step 4: Novelty Gate

For each finalist:

1. Run `skills/idea-generation/scripts/novelty_check.py` or manually search Semantic Scholar / arXiv / OpenAlex
2. Review the nearest papers and overlap risk
3. Decide whether the direction is actually distinct enough to justify continuation

### Step 5: Rank and Select

- Score each idea on three dimensions: Interestingness, Feasibility, Novelty
- Be cautious and realistic on ratings
- Select the top idea(s) for development

## Output Format

```json
{
  "Name": "adaptive_attention_pruning",
  "Title": "Adaptive Attention Head Pruning via Gradient-Guided Importance Scoring",
  "Experiment": "Detailed implementation plan...",
  "Interestingness": 8,
  "Feasibility": 7,
  "Novelty": 9,
  "novel": true,
  "most_similar_papers": ["paper1", "paper2"]
}
```

Additional artifact for template-grounded mode:

- `outputs/<topic-slug>/template_gap_map.md`

## Rules

- Ideas must be feasible with available resources
- Do not overfit ideas to a specific dataset or model; aim for wider significance
- In template-grounded mode, stay inside the scaffold unless the task explicitly allows redesign
- Prefer intervention points already exposed by the code, metrics, or baseline outputs
- Reject ideas that are merely parameter fiddling unless they reveal a broader mechanism or failure regime
- Always check novelty before committing to an idea

## Related Skills

- In this repository: [brainstorming-research-ideas](../brainstorming-research-ideas/), [creative-thinking-for-research](../creative-thinking-for-research/), [scientific-critical-thinking](../scientific-critical-thinking/), [novelty-assessment](../novelty-assessment/)
