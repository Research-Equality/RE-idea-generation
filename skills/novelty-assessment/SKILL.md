---
name: novelty-assessment
description: Assesses research idea novelty through multi-round literature search and harsh-critic evaluation. Use before committing to a research direction or investing in implementation.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Novelty Assessment, Research Ideation, Literature Gaps, Problem Discovery]
dependencies: []
---

# Novelty Assessment

Rigorously assess whether a research idea is novel through systematic literature search.

## Input

- A research idea description, title, or structured proposal JSON

## Scripts

### Automated novelty check
```bash
python skills/idea-generation/scripts/novelty_check.py \
  --idea "Your research idea description" \
  --max-rounds 10 \
  --output outputs/my-topic/novelty_report.json
```

### Manual literature search

Search Semantic Scholar, arXiv, or OpenAlex directly. If you have a literature-focused repository available elsewhere, use it only as external support rather than as the main ideation skill.

## References

- Assessment prompts and criteria: `references/assessment-prompts.md`

## Workflow

### Step 1: Understand the Idea
- Identify the core contribution
- List the key technical components
- Determine the research area and subfield

### Step 2: Multi-Round Literature Search (up to 10 rounds)
For each round:
1. Generate a targeted search query
2. Search Semantic Scholar / arXiv / OpenAlex
3. Review top-10 results with abstracts
4. Assess overlap with the idea
5. Decide: need more searching, or ready to decide

### Step 3: Make Decision
- **Novel**: After sufficient searching, no paper significantly overlaps
- **Not Novel**: Found a paper that significantly overlaps

### Step 4: Position the Idea
If novel, identify:
- Most similar existing papers (for Related Work)
- How the idea differs from each
- The specific gap this idea fills

## Harsh Critic Persona

```text
Be a harsh critic for novelty. Ensure there is a sufficient contribution
for a new conference or workshop paper. A trivial extension of existing
work is NOT novel. The idea must offer a meaningfully different approach,
formulation, or insight.
```

## Output Format

```json
{
  "decision": "novel",
  "confidence": "high",
  "justification": "After searching X rounds...",
  "most_similar_papers": [
    {"title": "...", "year": 2024, "overlap": "..."}
  ],
  "differentiation": "Our idea differs because..."
}
```

## Rules

- Minimum 3 search rounds before declaring something novel
- Try to recall exact paper names for targeted queries
- A paper idea is not novel if it is only a trivial extension
- Consider both methodology novelty and application novelty
- Check for concurrent or recent arXiv submissions

## Related Skills

- In this repository: [idea-generation](../idea-generation/), [brainstorming-research-ideas](../brainstorming-research-ideas/), [creative-thinking-for-research](../creative-thinking-for-research/)
