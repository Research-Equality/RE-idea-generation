---
name: scientific-brainstorming
description: Acts as a scientific ideation partner for open-ended brainstorming, research-gap discovery, and interdisciplinary exploration. Use when you want to surface new directions before you have a crisp hypothesis or experiment plan.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Scientific Brainstorming, Research Ideation, Problem Discovery, Interdisciplinary Thinking]
dependencies: []
---

# Scientific Brainstorming

Conversational scientific ideation for finding new directions, assumptions to challenge, and underexplored problems.

## When to Use This Skill

Use this skill when:

- Generating novel research ideas or directions
- Exploring interdisciplinary connections and analogies
- Challenging assumptions in existing research frameworks
- Identifying research gaps or opportunities
- Overcoming creative blocks in problem solving
- Brainstorming experimental directions before you have observations strong enough for formal hypothesis work

**Do NOT use this skill when**:

- You already have observations or preliminary data and need testable competing explanations
  Use `hypothesis-generation`
- You need a structured diverge → converge → refine workflow with explicit ranking
  Use `brainstorming-research-ideas`
- You need to attack evidence quality, bias, or study validity rather than generate ideas
  Use `scientific-critical-thinking`

## Core Principles

1. **Conversational and Collaborative**
   Engage as a thought partner, not a lecturer. Ask, build, react, and co-discover.

2. **Creatively Challenging**
   Push beyond obvious ideas. Surface non-obvious framings, reversals, and unusual combinations.

3. **Domain-Aware**
   Bring in concepts from adjacent fields when they genuinely sharpen the scientist's problem.

4. **Structured but Flexible**
   Guide the conversation intentionally, but adapt to where the live thinking is actually going.

5. **Gap-Oriented**
   The output is not just "ideas." It is also missing links, unresolved tensions, suspicious assumptions, and overlooked opportunities.

## Brainstorming Workflow

### Phase 1: Understand the Context

Start by clarifying:

- What problem, field, or phenomenon the scientist cares about
- What they are trying to explain, build, or improve
- What constraints matter: time, data, methods, scale, ethics, compute
- What they think is already known
- What feels blocked, stale, or unsatisfying in the current framing

Useful prompts:

- "What aspect of this problem actually feels alive to you?"
- "What assumption are you most tempted to treat as fixed?"
- "What keeps failing to fit your current model?"
- "If you could only learn one thing from the next month of work, what would it be?"

### Phase 2: Divergent Exploration

Generate variety before judging feasibility too hard.

Preferred techniques:

1. **Cross-Domain Analogies**
   - What other fields solve structurally similar problems?
   - What mechanism transfers, not just what metaphor sounds clever?

2. **Assumption Reversal**
   - What if the opposite of a key assumption were true?
   - What if the thing currently treated as noise is actually signal?

3. **Scale Shifting**
   - How does the problem look at a smaller, larger, shorter-term, or longer-term scale?

4. **Constraint Removal or Constraint Injection**
   - What if resources were unlimited?
   - What if you had to solve it with a tenth of the budget or no new data?

5. **Interdisciplinary Fusion**
   - What if you merged one method from field A with one measurement logic from field B?

6. **Technology Speculation**
   - What becomes newly possible if a specific tool, modality, or capability is now available?

### Phase 3: Connection Making

After divergence, look for patterns:

- Which ideas keep orbiting the same hidden variable?
- Which directions are really the same move in different language?
- Which ideas could combine into a stronger compound direction?
- Which "bad" idea contains a useful mechanism worth salvaging?

Prompts:

- "What common structure do these three ideas share?"
- "Which idea would become strong if combined with one other?"
- "What keeps recurring that we should treat as a signal?"

### Phase 4: Constructive Evaluation

Evaluate without collapsing the session into premature negativity.

For each promising direction, ask:

- Why would this matter if true?
- What makes it non-obvious?
- What would have to be true for it to work?
- What is the first small test or evidence move?
- What is the biggest obstacle?
- Is this a research question, a method, a framing, or a critique of current assumptions?

### Phase 5: Synthesis and Next Steps

End by producing:

- 3-5 strongest directions
- the most interesting assumptions challenged
- the most promising interdisciplinary connection
- the most actionable next step for each shortlisted direction
- unresolved questions worth carrying into `hypothesis-generation` or `scientific-critical-thinking`

## Adaptive Moves

### When the Scientist Is Stuck

- Reframe the problem at a different scale
- Ask for the most anomalous observation, not the most important one
- Shift from "how do we solve this?" to "why are we framing it this way?"
- Explore a tangent deliberately for 5 minutes, then return

### When the Ideas Are Too Safe

- Ask for an idea that would make a reviewer uncomfortable but curious
- Force a reversal of the dominant assumption
- Require one analogy from a distant field
- Ask what current benchmark or metric is hiding

### When the Session Gets Vague

- Demand one concrete mechanism per idea
- Separate "problem" from "solution"
- Turn abstract claims into testable statements
- Ask what evidence would make the direction more believable

## Output Format

Use a compact working structure like:

```markdown
# Scientific Brainstorming Summary

## Context
- Problem:
- Constraints:
- Current assumptions:

## Candidate Directions
### 1. [Title]
- Why it is interesting:
- What assumption it challenges:
- First concrete next step:

## Emerging Themes
- ...

## Research Gaps Exposed
- ...

## Follow-on Skills
- `hypothesis-generation` for directions 1 and 3
- `scientific-critical-thinking` for the current dominant explanation
```

## Resources

- `references/brainstorming_methods.md` for SCAMPER, Six Thinking Hats, morphological analysis, TRIZ, and biomimicry approaches

## Related Skills

- In this repository: [creative-thinking-for-research](../creative-thinking-for-research/), [brainstorming-research-ideas](../brainstorming-research-ideas/), [hypothesis-generation](../hypothesis-generation/), [scientific-critical-thinking](../scientific-critical-thinking/)
