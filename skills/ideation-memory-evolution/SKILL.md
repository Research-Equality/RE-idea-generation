---
name: ideation-memory-evolution
description: Maintains persistent memory of promising, failed, and ambiguous research directions across ideation and validation cycles. Use when updating what to pursue, avoid, or revisit after idea ranking, failed validation, or a major pivot.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Research Ideation, Persistent Memory, Direction Selection, Problem Discovery]
dependencies: []
---

# Ideation Memory Evolution

Turn one-off brainstorming into cumulative research taste.

This skill keeps a durable record of which directions look promising, which ones failed, and why. It is most useful after you have already generated or tested ideas and need to make the next cycle smarter instead of starting from scratch.

## Use When

- A shortlist or tournament has produced candidate directions
- A proposed direction failed validation and you want to preserve the failure mode
- You are revisiting a topic and need to remember what looked good, weak, or unresolved

## Inputs

- One or more of:
  - `outputs/<topic-slug>/direction_shortlist.md`
  - `outputs/<topic-slug>/problem_map.md`
  - `outputs/<topic-slug>/research_log.md`
  - `outputs/<topic-slug>/novelty_report.json`
  - stage logs, reviewer notes, or failure summaries
- Existing memory file if present:
  - `memory/ideation-memory.md`

## References

- Memory schema: `references/ideation-memory-schema.md`
- Starter template: `templates/ideation-memory.md`

## Workflow

### Step 1: Choose the Update Mode

Use one of these update modes:

- `IDE`: after idea ranking or direction selection, record promising directions and why they matter
- `IVE`: after failed validation, classify why a direction should be avoided, delayed, or reframed

This skill intentionally does not manage implementation tactics or experiment strategy memory. It only tracks direction-level learning.

### Step 2: Extract Decision-Relevant Signals

For each candidate direction, capture only the signals that change future choices:

- target problem or gap
- proposed mechanism or angle
- novelty risk
- feasibility risk
- strongest supporting evidence
- strongest disqualifying evidence

Discard decorative summaries. Keep only what will affect whether the direction should be revisited.

### Step 3: Update Memory

Maintain four sections in `memory/ideation-memory.md`:

1. Promising directions
2. Failed or deprioritized directions
3. Open questions worth revisiting
4. Decision heuristics learned from this cycle

Each entry should explain not just what happened, but why it should influence future ideation.

### Step 4: Classify Failures Precisely

When a direction fails, avoid vague labels like "didn't work." Classify the failure:

- not novel enough
- infeasible within current resources
- weak empirical signal
- confounded evaluation
- problem framing was wrong
- implementation burden too high for likely payoff
- interesting but needs a different template, dataset, or benchmark

### Step 5: Feed Forward

At the start of the next ideation cycle, read `memory/ideation-memory.md` first.

Use it to:

- avoid dead-end families
- reuse promising mechanisms in better-framed problems
- identify missing comparisons or hidden assumptions
- bias the next shortlist toward directions with better evidence quality

## Output

Primary artifact:

- `memory/ideation-memory.md`

Optional companion artifacts:

- `outputs/<topic-slug>/failure_review.md`
- `outputs/<topic-slug>/pivot_candidates.md`

## Rules

- Record explanations, not just verdicts
- Preserve ambiguous directions when the evidence is incomplete
- Separate "bad idea" from "bad current instantiation"
- Prefer short, high-signal entries over narrative logs
- Update the memory after major ideation decisions or failed validation, not after every tiny observation

## Related Skills

- In this repository: [brainstorming-research-ideas](../brainstorming-research-ideas/), [idea-generation](../idea-generation/), [novelty-assessment](../novelty-assessment/)
- Use this skill after those workflows to retain directional learning across cycles
