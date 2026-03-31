# Skills Catalog

This directory contains the authoritative loadable skills for research idea generation and problem discovery in this repository.

## Skill Catalog

| Skill | Primary Role | Use When | Pairs Well With |
|------|---------------|----------|-----------------|
| `brainstorming-research-ideas` | Structured ideation and ranking | You need a repeatable session format to generate, filter, and refine candidate directions | `creative-thinking-for-research` |
| `creative-thinking-for-research` | Novelty generation and cognitive reframing | You are stuck in local-optimum thinking or need distant analogies, reformulations, and constraint shifts | `brainstorming-research-ideas` |
| `idea-generation` | Candidate proposal generation and scoring | You already have a topic, paper context, or runnable template and want concrete proposal candidates with explicit scoring | `novelty-assessment`, `brainstorming-research-ideas` |
| `ideation` | Multi-agent concept exploration and session memory | You want a longer-form ideation process with explicit divergent/convergent roles, artifacts, and continuation support | `creative-thinking-for-research`, `brainstorming-research-ideas` |
| `direction-evolution` | Cross-cycle memory and post-stage revision | You want to preserve directional judgment and convert new evidence into the next justified step | `idea-generation`, `scientific-critical-thinking` |
| `scientific-brainstorming` | Scientific thought-partner ideation | You want open-ended research brainstorming, cross-domain analogies, and gap-finding dialogue | `creative-thinking-for-research`, `brainstorming-research-ideas` |
| `hypothesis-generation` | Observation-to-hypothesis conversion | You already have observations or anomalies and need competing, testable explanations | `scientific-critical-thinking`, `novelty-assessment` |
| `scientific-critical-thinking` | Claim and evidence attack surface mapping | You want to find flaws, confounders, weak evidence, or hidden assumptions in a study or plan | `hypothesis-generation` |
| `novelty-assessment` | Novelty gate and overlap checking | You need to decide whether a direction is sufficiently different from existing literature before committing to it | `idea-generation` |

## Routing Guidance

### Minimal Default Path

1. Choose one opener:
   `creative-thinking-for-research` for framework-driven novelty, or `scientific-brainstorming` for conversational scientific exploration.
2. Use `brainstorming-research-ideas` to structure and rank candidates.
3. Use `idea-generation`:
   topic-first mode for conceptual inputs, or template-grounded mode when a runnable template already exists.
4. Run `novelty-assessment`.
5. Update `direction-evolution`.

### Optional Branches

- Use `ideation` when you need a longer, role-separated session with reusable artifacts.
- Use `scientific-critical-thinking` when the bottleneck is weak reasoning, confounding, or invalid inference rather than idea quantity.
- Use `hypothesis-generation` when the starting point is an anomaly or observation rather than a vague topic.
- Use `direction-evolution` after ranking, failed validation, or a completed stage. It is the post-cycle operating layer.

### Non-Overlap Rules

- Do not use both `creative-thinking-for-research` and `scientific-brainstorming` by default.
- Use `idea-generation` in one of its two modes rather than splitting proposal generation across multiple skills.
- Treat `ideation` as an orchestration layer, not as an extra scoring step after the default path.
- Treat `direction-evolution` as post-cycle consolidation, not as initial ideation.

## Recommended Session Flow

1. Write down the topic, field, anomaly, or unresolved tension you want to explore.
2. Open the space with one skill: `creative-thinking-for-research` or `scientific-brainstorming`.
3. Record raw ideas in `outputs/<topic-slug>/idea_backlog.md`.
4. Use `brainstorming-research-ideas` to run diverge → converge → refine.
5. Concretize with `idea-generation`, choosing topic-first or template-grounded mode.
6. Run `novelty-assessment` or `skills/idea-generation/scripts/novelty_check.py` on the top candidates.
7. Save the shortlist to `outputs/<topic-slug>/direction_shortlist.md`.
8. Update `memory/ideation-memory.md` and `outputs/<topic-slug>/stage_reflection.json` with `direction-evolution` as needed.
9. If the work needs a managed long-form session, run `ideation`.
10. If you have empirical anomalies, switch to `hypothesis-generation`; if you need critique, switch to `scientific-critical-thinking`.
11. If a baseline or stage completes later, use `direction-evolution` in stage-reflection mode to decide the next diagnostic move.

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
