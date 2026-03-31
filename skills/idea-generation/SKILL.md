---
name: idea-generation
description: Generates research ideas with iterative refinement and script-assisted novelty checks. Use when translating a topic, codebase context, or partial concept into scored candidate research directions.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Research Ideation, Idea Ranking, Novelty Assessment, Problem Discovery]
dependencies: []
---

# Idea Generation

Generate and refine novel research ideas with literature-backed novelty assessment.

## Input

- A research area, task description, or existing codebase context
- Optional constraints such as venue, budget, dataset limits, or timeline

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

## Workflow

### Step 1: Generate Ideas
Given a research area and optional code or paper context:
1. Generate 3-5 diverse research ideas
2. For each idea, provide: Name, Title, Experiment plan, and ratings
3. Use the ideation prompt templates from `references/ideation-prompts.md`

### Step 2: Iterative Refinement (up to 5 rounds per idea)
For each idea:
1. Critically evaluate quality, novelty, and feasibility
2. Refine the idea while preserving its core spirit
3. Stop when converged ("I am done") or max rounds reached

### Step 3: Novelty Assessment
For each promising idea:
1. Run `skills/idea-generation/scripts/novelty_check.py` or manually search Semantic Scholar / arXiv
2. Use the novelty checking prompts from `references/ideation-prompts.md`
3. Multi-round search: generate queries, review results, decide
4. Binary decision: Novel / Not Novel with justification

### Step 4: Rank and Select
- Score each idea on three dimensions (1-10): Interestingness, Feasibility, Novelty
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

## Rules

- Ideas must be feasible with available resources
- Do not overfit ideas to a specific dataset or model; aim for wider significance
- Be a harsh critic for novelty and look for conference-level contribution
- Each idea should stem from a simple, elegant question or hypothesis
- Always check novelty before committing to an idea

## Related Skills

- In this repository: [brainstorming-research-ideas](../brainstorming-research-ideas/), [creative-thinking-for-research](../creative-thinking-for-research/), [novelty-assessment](../novelty-assessment/)
- Companion repositories: literature-search, literature-review, research-planning
