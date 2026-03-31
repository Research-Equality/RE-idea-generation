# Skills Catalog

This directory contains the authoritative loadable skills for research idea generation and problem discovery in this repository.

## Skill Catalog

| Skill | Primary Role | Use When | Pairs Well With |
|------|---------------|----------|-----------------|
| `brainstorming-research-ideas` | Structured ideation and ranking | You need a repeatable session format to generate, filter, and refine candidate directions | `creative-thinking-for-research` |
| `creative-thinking-for-research` | Novelty generation and cognitive reframing | You are stuck in local-optimum thinking or need distant analogies, reformulations, and constraint shifts | `brainstorming-research-ideas` |
| `idea-generation` | Candidate proposal generation and scoring | You already have a topic, paper context, or codebase context and want concrete proposal candidates with explicit scoring | `novelty-assessment`, `brainstorming-research-ideas` |
| `template-grounded-ideation` | Code-constrained gap finding and proposal generation | You already have a runnable experiment template and want ideas grounded in editable seams, metrics, and baseline limitations | `idea-generation`, `scientific-critical-thinking` |
| `ideation` | Multi-agent concept exploration and session memory | You want a longer-form ideation process with explicit divergent/convergent roles, artifacts, and continuation support | `creative-thinking-for-research`, `brainstorming-research-ideas` |
| `ideation-memory-evolution` | Cross-cycle direction memory | You want to preserve promising, failed, and unresolved directions so later ideation starts from better judgment | `idea-generation`, `novelty-assessment` |
| `gap-driven-stage-reflection` | Evidence-driven plan revision | You have stage results and need disciplined next-step changes based on unmet signals, confounds, or suspicious outcomes | `template-grounded-ideation`, `scientific-critical-thinking` |
| `scientific-brainstorming` | Scientific thought-partner ideation | You want open-ended research brainstorming, cross-domain analogies, and gap-finding dialogue | `creative-thinking-for-research`, `brainstorming-research-ideas` |
| `hypothesis-generation` | Observation-to-hypothesis conversion | You already have observations or anomalies and need competing, testable explanations | `scientific-critical-thinking`, `novelty-assessment` |
| `scientific-critical-thinking` | Claim and evidence attack surface mapping | You want to find flaws, confounders, weak evidence, or hidden assumptions in a study or plan | `hypothesis-generation` |
| `novelty-assessment` | Novelty gate and overlap checking | You need to decide whether a direction is sufficiently different from existing literature before committing to it | `idea-generation` |

## Routing Guidance

- Default to `creative-thinking-for-research` when the bottleneck is novelty, reframing, or escaping incremental thinking
- Default to `brainstorming-research-ideas` when the bottleneck is prioritization, structure, or turning a rough theme into an actionable shortlist
- Default to `idea-generation` when the bottleneck is turning a topic or partial concept into scored candidate proposals
- Default to `template-grounded-ideation` when the bottleneck is understanding what an existing experiment scaffold is missing and turning those gaps into feasible new directions
- Default to `ideation` when the bottleneck is sustained exploration over time and you want explicit role separation plus reusable artifacts
- Default to `ideation-memory-evolution` when the bottleneck is retaining directional judgment across cycles rather than regenerating ideas from scratch
- Default to `gap-driven-stage-reflection` when the bottleneck is deciding what the evidence implies after a completed baseline or stage
- Default to `scientific-brainstorming` when the bottleneck is open-ended scientific ideation and research-gap surfacing
- Default to `hypothesis-generation` when the bottleneck is converting observations into falsifiable explanations
- Default to `scientific-critical-thinking` when the bottleneck is identifying flaws, biases, or weak links in current reasoning
- Default to `novelty-assessment` when the bottleneck is deciding whether a candidate is actually new enough
- Use both when the task spans both phases:
  1. Generate unconventional candidates with `creative-thinking-for-research`
  2. Filter and sharpen them with `brainstorming-research-ideas`
  3. Use `template-grounded-ideation` when there is already a runnable template or benchmark scaffold
  4. Convert finalists into concrete scored proposals with `idea-generation`
  5. Run a novelty gate with `novelty-assessment`
  6. Update `ideation-memory-evolution` so later cycles inherit what was learned
  7. Run `ideation` instead of or after steps 1-4 when you need a session-grade artifact set rather than a one-shot brainstorm

## Recommended Session Flow

1. Write down the topic, field, or unresolved tension you want to explore.
2. Use `creative-thinking-for-research` to produce several candidate directions from distinct frameworks.
3. Record all raw ideas in `outputs/<topic-slug>/idea_backlog.md`.
4. Use `brainstorming-research-ideas` to run diverge → converge → refine.
5. If a runnable template already exists, use `template-grounded-ideation` to map missing evaluation slices, assumptions, and intervention points.
6. Use `idea-generation` to rewrite the shortlist into concrete proposal candidates with explicit scoring.
7. Run `novelty-assessment` or `skills/idea-generation/scripts/novelty_check.py` on the top candidates.
8. Save the ranked shortlist to `outputs/<topic-slug>/direction_shortlist.md`.
9. Update `memory/ideation-memory.md` with `ideation-memory-evolution` after key decisions or failed validation.
10. If a baseline or stage completes, use `gap-driven-stage-reflection` to decide the next diagnostic move.
11. If the work needs more structured dialogue and history, run `ideation` and store the full session under `ideations/`.
12. If you have empirical anomalies, switch to `hypothesis-generation`; if you need to break weak reasoning, switch to `scientific-critical-thinking`.

## Shared Artifacts

- `outputs/<topic-slug>/idea_backlog.md`: raw ideas, partial thoughts, odd but potentially useful leads
- `outputs/<topic-slug>/problem_map.md`: pain points, tensions, contradictions, stakeholder concerns
- `outputs/<topic-slug>/research_log.md`: dated session log, pivots, dead ends, and follow-up questions
- `outputs/<topic-slug>/template_gap_map.md`: assumptions, untested seams, suspicious metrics, and failure slices in the current scaffold
- `outputs/<topic-slug>/direction_shortlist.md`: final ranked candidates with rationale and next steps
- `outputs/<topic-slug>/novelty_report.json`: structured novelty-check output and nearest-paper evidence
- `outputs/<topic-slug>/stage_reflection.json`: JSON plan updates after a completed baseline or stage
- `memory/ideation-memory.md`: cross-cycle memory of promising, failed, and unresolved directions
- `ideations/ideation-<slug>-<timestamp>/session/`: multi-agent ideation artifacts, briefs, summaries, and continuation lineage

## Scope Boundary

This repository is intentionally narrow. Skills for literature search, corpus analysis, experiments, implementation, or paper writing should live in neighboring repositories rather than here.
