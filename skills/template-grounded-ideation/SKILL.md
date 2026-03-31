---
name: template-grounded-ideation
description: Generates research ideas and problem-discovery leads from an existing executable template or code scaffold. Use when you already have an experiment package and want feasible, novel directions grounded in the code, metrics, and resource limits you actually have.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Research Ideation, Problem Discovery, Code-Constrained Ideation, Template-Based Research]
dependencies: []
---

# Template-Grounded Ideation

Generate research ideas from a runnable template instead of from a blank topic prompt.

This skill is for situations where the search space is constrained by an existing `experiment.py`, benchmark setup, or evaluation scaffold. It turns those constraints into an advantage: ideas stay executable, measurable, and easier to prioritize.

## Use When

- You already have a template pack with code and baseline runs
- You want ideas that fit available datasets, compute, and editable code seams
- You want to discover missing questions, blind spots, or under-tested intervention points in an existing setup

## Inputs

- Required template context:
  - `prompt.json`
  - `experiment.py`
  - `seed_ideas.json`
- Strongly recommended context:
  - baseline outputs such as `run_0/`, `final_info.json`, plots, logs, or reviewer notes
  - hard constraints such as budget, wall-clock limits, dataset restrictions, or forbidden dependencies

## References

- Template pack structure: `references/template-pack.md`
- Starter files: `templates/prompt.json`, `templates/seed_ideas.json`
- Novelty script: `../idea-generation/scripts/novelty_check.py`

## Workflow

### Step 1: Read the Template Pack

Extract four things before generating any ideas:

1. What question the template currently studies
2. What parts of the code are realistically editable
3. What outputs or metrics already exist
4. What the template cannot currently test well

Treat `experiment.py` as the boundary of feasible intervention, not just as background reading.

### Step 2: Build an Idea Archive

Use `seed_ideas.json` as the initial archive. Add any prior accepted, rejected, or scored ideas if they exist.

For each archived idea, note:

- core mechanism
- target failure mode or hypothesis
- resource cost
- final outcome or reviewer score if available

The archive is there to prevent duplicates and to show which regions of idea space are already saturated.

### Step 3: Surface Gaps Before Proposing New Ideas

Look for problem-discovery signals in the template:

- hidden assumptions in the baseline
- missing ablations or controls
- narrow evaluation slices
- knobs that exist in code but are never stressed
- failure cases visible in logs or plots but not investigated
- places where the task description makes a broader claim than the template actually tests

Convert the strongest gaps into candidate questions before turning them into full ideas.

### Step 4: Generate Candidate Ideas

Produce 3-5 ideas grounded in the template. Each idea must:

- fit the available code and data constraints
- be meaningfully different from the archive
- specify what in `experiment.py` or the evaluation pipeline would change
- aim for broader significance than a one-off dataset trick

Use this JSON schema:

```json
{
  "Name": "short_snake_case_name",
  "Title": "Readable research title",
  "Experiment": "Concrete implementation and evaluation plan tied to the template.",
  "Interestingness": 1,
  "Feasibility": 1,
  "Novelty": 1
}
```

### Step 5: Reflection Loop

Refine each promising idea for up to 5 rounds:

1. Critique significance, novelty, feasibility, and clarity
2. Check whether the idea is too close to a seed or prior failed attempt
3. Simplify overly ambitious plans
4. Stop early once the idea has converged

If earlier ideas have reviewer `Score` values, prefer learning from that signal without collapsing onto the exact same family of ideas.

### Step 6: Novelty Gate

Run a literature check on finalists:

```bash
python skills/idea-generation/scripts/novelty_check.py \
  --idea-file outputs/<topic-slug>/top_idea.json \
  --max-rounds 5 \
  --output outputs/<topic-slug>/novelty_report.json
```

Use Semantic Scholar first. If needed, manually cross-check with OpenAlex or arXiv.

### Step 7: Select for Execution

Prioritize ideas that combine:

- a real gap in the current template
- low-to-medium implementation cost
- clear measurable outcomes
- plausible conference or workshop contribution

## Output Artifacts

- `outputs/<topic-slug>/template_gap_map.md`
- `outputs/<topic-slug>/idea_backlog.md`
- `outputs/<topic-slug>/direction_shortlist.md`
- `outputs/<topic-slug>/top_idea.json`
- `outputs/<topic-slug>/novelty_report.json`

## Rules

- Stay inside the resource and code constraints unless the task explicitly allows template redesign
- Do not propose ideas that require entirely new infrastructure when the current template cannot support them
- Use seed ideas as anchors for coverage, not as defaults to lightly mutate
- Prefer intervention points already exposed by the code, metrics, or baseline outputs
- Treat problem discovery as template diagnosis: find what the scaffold is assuming, omitting, or failing to explain
- Reject ideas that are merely parameter fiddling unless they reveal a broader mechanism or failure regime

## Related Skills

- In this repository: [idea-generation](../idea-generation/), [novelty-assessment](../novelty-assessment/), [scientific-critical-thinking](../scientific-critical-thinking/)
- Use `idea-generation` for topic-first ideation
- Use this skill when the template itself is the primary source of constraints and inspiration
