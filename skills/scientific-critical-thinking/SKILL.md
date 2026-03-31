---
name: scientific-critical-thinking
description: Evaluates scientific claims, experimental designs, evidence quality, and bias structure. Use when you want to expose weak assumptions, confounders, or invalid inference and turn critique into clearer research problems.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Scientific Critical Thinking, Evidence Quality, Bias Detection, Problem Discovery]
dependencies: []
---

# Scientific Critical Thinking

Interrogate claims, methods, and evidence so weak reasoning becomes visible and useful.

## When to Use This Skill

Use this skill when:

- Evaluating a paper, claim, or research plan for rigor
- Assessing whether a conclusion is stronger than the evidence behind it
- Identifying confounders, hidden assumptions, or weak causal logic
- Stress-testing proposed experiments before running them
- Turning critique into concrete open problems or stronger study designs

**Do NOT use this skill when**:

- You mainly need generative ideation
  Use `scientific-brainstorming`
- You already have observations and need competing explanations
  Use `hypothesis-generation`
- You need full peer-review prose instead of an internal critique workflow
  Use a dedicated review or writing skill in a neighboring repository

## Core Review Lenses

### 1. Claim-to-Evidence Matching

Ask:

- What exact claim is being made?
- What evidence actually supports it?
- Is the paper making a correlational, causal, predictive, or mechanistic claim?
- Has the conclusion outrun the design?

### 2. Study Design Validity

Inspect:

- whether the design matches the question
- appropriateness of controls
- temporal ordering
- construct validity of the measurements
- internal and external validity

Use `references/experimental_design.md`.

### 3. Bias and Confounding

Look for:

- selection bias
- measurement bias
- observer or performance bias
- reporting bias
- unmeasured confounding
- confirmation bias or HARKing

Use `references/common_biases.md`.

### 4. Statistical Validity

Check:

- sample size and power
- test appropriateness
- multiple-comparison control
- effect sizes and interval estimates
- missing-data handling
- overfitting or fragile subgroup claims

### 5. Evidence Quality

Evaluate:

- design hierarchy
- methodological quality within the design class
- consistency across studies
- directness and generalizability
- precision and publication bias

Use `references/evidence_hierarchy.md`.

## Critical Thinking Workflow

### Step 1: Restate the Claim Precisely

Rewrite the central claim in plain language.

Separate:

- what was measured
- what was inferred
- what was merely implied

### Step 2: Inspect the Design

Determine:

- what kind of study it is
- whether the design can support the level of inference being made
- what comparison or control is doing the real work
- what alternative explanations remain open

### Step 3: Audit Bias and Confounding

Ask:

- who or what is missing from the sample?
- what systematic distortion could produce the effect?
- what variable could explain both the predictor and the outcome?
- what was likely decided after the data were seen?

### Step 4: Inspect Measurement and Analysis

Ask:

- are the measures valid proxies for the construct?
- are the models or tests appropriate?
- are effect sizes meaningful, or just significant?
- how robust is the result to different analytic choices?

### Step 5: Grade Evidence Strength

Place the evidence on an appropriate hierarchy, then downgrade or upgrade based on:

- bias
- inconsistency
- indirectness
- imprecision
- publication bias
- large effect or convergent evidence

### Step 6: Convert Critique into Problem Discovery

Do not stop at "this is flawed."

Produce:

- the most damaging weakness
- the most plausible rival explanation
- the most informative missing experiment
- the hidden assumption worth testing directly
- the research gap exposed by the critique

## Output Format

```markdown
# Critical Thinking Report

## Claim
- ...

## What the Evidence Actually Shows
- ...

## Major Risks to Validity
- Design:
- Bias/confounding:
- Statistical:

## Strongest Alternative Explanation
- ...

## Evidence Grade
- Level:
- Why:

## Problem Discovery Output
- Missing experiment:
- Hidden assumption to test:
- Research gap exposed:
```

## Heuristics

- Strong rhetoric often masks weak identification
- A significant result is not the same as a meaningful result
- A mechanistic story without a discriminating test is still a story
- A higher-tier design can still be poor evidence if executed badly
- The best critique ends with a sharper next question, not just rejection

## Resources

- `references/common_biases.md`
- `references/evidence_hierarchy.md`
- `references/experimental_design.md`

## Related Skills

- In this repository: [hypothesis-generation](../hypothesis-generation/), [scientific-brainstorming](../scientific-brainstorming/), [novelty-assessment](../novelty-assessment/)
