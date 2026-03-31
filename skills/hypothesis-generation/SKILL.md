---
name: hypothesis-generation
description: Converts observations, preliminary data, or unexplained phenomena into competing, testable hypotheses with distinguishing predictions and experiment ideas. Use when open-ended ideation should become falsifiable scientific reasoning.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Hypothesis Generation, Scientific Method, Problem Discovery, Experimental Design]
dependencies: []
---

# Hypothesis Generation

Turn observations and anomalies into competing scientific hypotheses that can actually be tested.

## When to Use This Skill

Use this skill when:

- You have experimental observations or preliminary data that need explanation
- You want to develop competing mechanistic hypotheses
- You need specific predictions that distinguish between explanations
- You want experiments or studies that could falsify the leading hypotheses
- You need to move from open-ended idea generation to scientific reasoning

**Do NOT use this skill when**:

- You are still exploring broad research directions without concrete observations
  Use `scientific-brainstorming`
- You mainly need to critique a study or claim for flaws
  Use `scientific-critical-thinking`
- You mainly need novelty ranking rather than explanation building
  Use `novelty-assessment`

## Core Workflow

### 1. Clarify the Phenomenon

State the phenomenon precisely:

- What was observed?
- Under what conditions?
- What is stable vs. noisy?
- What is surprising relative to expectation?
- What are the boundaries of the claim?

Separate:

- raw observation
- interpretation
- speculation

### 2. Ground in Existing Evidence

Before proposing explanations, establish what is already known.

Search for:

- recent reviews
- mechanistic work
- analogous systems
- contradictory findings
- prior failed explanations

Use `references/literature_search_strategies.md`.

### 3. Synthesize the Evidence Base

Summarize:

- current best-supported mechanisms
- unresolved contradictions
- assumptions in the current literature
- what remains unexplained by dominant accounts

This becomes the constraint set for hypothesis generation.

### 4. Generate 3-5 Competing Hypotheses

Each hypothesis should:

- explain the observation mechanistically, not just rename it
- be distinguishable from the others
- connect to existing evidence where possible
- make predictions the others do not

Good hypothesis families often differ by:

- causal variable
- scale of explanation
- timing
- hidden moderator
- measurement artifact vs. genuine mechanism

### 5. Evaluate Hypothesis Quality

Assess each hypothesis against:

- testability
- falsifiability
- parsimony
- explanatory power
- scope
- consistency with established knowledge
- novelty or insight

Use `references/hypothesis_quality_criteria.md`.

### 6. Design Distinguishing Tests

For each viable hypothesis:

- what should be measured?
- what comparison or control is needed?
- what pattern would support it?
- what pattern would weaken or falsify it?
- what is the cheapest informative next experiment?

Use `references/experimental_design_patterns.md`.

### 7. Formulate Explicit Predictions

Predictions should be concrete enough that a result could change your mind.

Include:

- expected direction of effect
- timing if relevant
- context or conditions
- contrasting predictions across hypotheses

## Output Structure

Prefer a compact markdown report:

```markdown
# Hypothesis Report

## Phenomenon
- ...

## Evidence Base
- ...

## Competing Hypotheses
### H1. [Title]
- Mechanism:
- Why it fits:
- Weak points:

## Distinguishing Predictions
- If H1 is true, ...
- If H2 is true, ...

## Best Next Tests
- ...

## Current Ranking
- Most plausible now:
- Most informative falsification test:
```

## Quality Rules

- Avoid hypotheses that are just descriptions with new nouns
- Require at least one falsifying condition per serious hypothesis
- Prefer multiple competing explanations over a single favorite story
- Distinguish exploratory hypotheses from already well-supported mechanisms
- Preserve uncertainty honestly instead of forcing premature convergence

## Typical Failure Modes

- Hypotheses too vague to test
- Escape clauses that prevent falsification
- Overly complex stories with many speculative steps
- Confusing correlation with mechanism
- Repackaging literature consensus as if it were a new hypothesis

## Resources

- `references/hypothesis_quality_criteria.md`
- `references/literature_search_strategies.md`
- `references/experimental_design_patterns.md`

## Related Skills

- In this repository: [scientific-brainstorming](../scientific-brainstorming/), [scientific-critical-thinking](../scientific-critical-thinking/), [novelty-assessment](../novelty-assessment/)
