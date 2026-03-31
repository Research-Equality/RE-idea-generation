# Skills Catalog

This directory contains the authoritative loadable skills for research idea generation and problem discovery in this repository.

## Skill Catalog

| Skill | Primary Role | Use When | Pairs Well With |
|------|---------------|----------|-----------------|
| `brainstorming-research-ideas` | Structured ideation and ranking | You need a repeatable session format to generate, filter, and refine candidate directions | `creative-thinking-for-research` |
| `creative-thinking-for-research` | Novelty generation and cognitive reframing | You are stuck in local-optimum thinking or need distant analogies, reformulations, and constraint shifts | `brainstorming-research-ideas` |
| `idea-generation` | Candidate proposal generation and scoring | You already have a topic, paper context, or codebase context and want concrete proposal candidates with explicit scoring | `novelty-assessment`, `brainstorming-research-ideas` |
| `ideation` | Multi-agent concept exploration and session memory | You want a longer-form ideation process with explicit divergent/convergent roles, artifacts, and continuation support | `creative-thinking-for-research`, `brainstorming-research-ideas` |
| `scientific-brainstorming` | Scientific thought-partner ideation | You want open-ended research brainstorming, cross-domain analogies, and gap-finding dialogue | `creative-thinking-for-research`, `brainstorming-research-ideas` |
| `hypothesis-generation` | Observation-to-hypothesis conversion | You already have observations or anomalies and need competing, testable explanations | `scientific-critical-thinking`, `novelty-assessment` |
| `scientific-critical-thinking` | Claim and evidence attack surface mapping | You want to find flaws, confounders, weak evidence, or hidden assumptions in a study or plan | `hypothesis-generation` |
| `novelty-assessment` | Novelty gate and overlap checking | You need to decide whether a direction is sufficiently different from existing literature before committing to it | `idea-generation` |

## Routing Guidance

- Default to `creative-thinking-for-research` when the bottleneck is novelty, reframing, or escaping incremental thinking
- Default to `brainstorming-research-ideas` when the bottleneck is prioritization, structure, or turning a rough theme into an actionable shortlist
- Default to `idea-generation` when the bottleneck is turning a topic or partial concept into scored candidate proposals
- Default to `ideation` when the bottleneck is sustained exploration over time and you want explicit role separation plus reusable artifacts
- Default to `scientific-brainstorming` when the bottleneck is open-ended scientific ideation and research-gap surfacing
- Default to `hypothesis-generation` when the bottleneck is converting observations into falsifiable explanations
- Default to `scientific-critical-thinking` when the bottleneck is identifying flaws, biases, or weak links in current reasoning
- Default to `novelty-assessment` when the bottleneck is deciding whether a candidate is actually new enough
- Use both when the task spans both phases:
  1. Generate unconventional candidates with `creative-thinking-for-research`
  2. Filter and sharpen them with `brainstorming-research-ideas`
  3. Convert finalists into concrete scored proposals with `idea-generation`
  4. Run a novelty gate with `novelty-assessment`
  5. Run `ideation` instead of or after steps 1-3 when you need a session-grade artifact set rather than a one-shot brainstorm

## Recommended Session Flow

1. Write down the topic, field, or unresolved tension you want to explore.
2. Use `creative-thinking-for-research` to produce several candidate directions from distinct frameworks.
3. Record all raw ideas in `outputs/<topic-slug>/idea_backlog.md`.
4. Use `brainstorming-research-ideas` to run diverge → converge → refine.
5. Use `idea-generation` to rewrite the shortlist into concrete proposal candidates with explicit scoring.
6. Run `novelty-assessment` or `skills/idea-generation/scripts/novelty_check.py` on the top candidates.
7. Save the ranked shortlist to `outputs/<topic-slug>/direction_shortlist.md`.
8. If the work needs more structured dialogue and history, run `ideation` and store the full session under `ideations/`.
9. If you have empirical anomalies, switch to `hypothesis-generation`; if you need to break weak reasoning, switch to `scientific-critical-thinking`.

## Shared Artifacts

- `outputs/<topic-slug>/idea_backlog.md`: raw ideas, partial thoughts, odd but potentially useful leads
- `outputs/<topic-slug>/problem_map.md`: pain points, tensions, contradictions, stakeholder concerns
- `outputs/<topic-slug>/research_log.md`: dated session log, pivots, dead ends, and follow-up questions
- `outputs/<topic-slug>/direction_shortlist.md`: final ranked candidates with rationale and next steps
- `outputs/<topic-slug>/novelty_report.json`: structured novelty-check output and nearest-paper evidence
- `ideations/ideation-<slug>-<timestamp>/session/`: multi-agent ideation artifacts, briefs, summaries, and continuation lineage

## Scope Boundary

This repository is intentionally narrow. Skills for literature search, corpus analysis, experiments, implementation, or paper writing should live in neighboring repositories rather than here.
