# RE-idea-generation

[English](README.md) | [简体中文](README.zh.md)

An authoritative skills repository for research idea generation, problem discovery, and direction exploration.

This repository focuses on the front end of the research workflow: finding worthwhile problems, reframing vague interests into researchable questions, and generating defensible directions before execution begins. It is not a general end-to-end research toolkit. It is a curated home for skills directly related to ideation, open-question discovery, and early-stage direction selection.

## Positioning

- Keep only skills directly related to idea generation, problem discovery, and direction exploration
- Normalize upstream skill snapshots into a portable repository layout
- Serve as the authoritative home for future ideation-related skills in Research-Equality

## Included Skills

The skill collection lives under [skills/](skills/).

### Primary Flow Skills

- `creative-thinking-for-research`: use when the bottleneck is novelty generation, reframing, or escaping local-optimum thinking
- `scientific-brainstorming`: use when you want an open-ended, domain-aware thought partner before you have a crisp hypothesis
- `brainstorming-research-ideas`: use when you need diverge → converge → refine with explicit filtering and ranking
- `idea-generation`: use when you have a topic, partial concept, or runnable scaffold and need scored candidate proposals
- `novelty-assessment`: use as the last ideation gate before committing to a direction

### Branch Skills

- `hypothesis-generation`: turn observations, anomalies, or preliminary data into competing testable hypotheses with predictions and experiment ideas
- `scientific-critical-thinking`: interrogate claims, methods, evidence quality, and confounders to expose flaws, hidden assumptions, and genuine open problems

### Operating Skills

- `ideation`: run a structured multi-agent ideation session around a concept seed when one-shot workflows are not enough
- `direction-evolution`: preserve cross-cycle direction memory and evidence-driven next-step updates after shortlisting, failed validation, or completed stages

See [skills/README.md](skills/README.md) for the skill catalog and routing guidance.

## Canonical Flow

To keep overlap low, use this as the default path:

1. Open the space with exactly one starter:
   `creative-thinking-for-research` for novelty frameworks, or `scientific-brainstorming` for conversational scientific exploration.
2. Structure and shortlist with `brainstorming-research-ideas`.
3. Concretize with `idea-generation`:
   use `topic-first` mode for conceptual inputs, or `template-grounded` mode when a runnable scaffold already exists.
4. Run `novelty-assessment`.
5. Preserve what was learned with `direction-evolution`.

## Routing Rules

- Do not use both `creative-thinking-for-research` and `scientific-brainstorming` by default. Pick one opener based on whether you need cognitive frameworks or a live scientific thought partner.
- Use `idea-generation` in one of its two modes rather than splitting proposal generation across multiple skills.
- Use `ideation` as an orchestration wrapper when a longer, role-separated session is needed. It is not part of the minimal default path.
- Use `scientific-critical-thinking` as a critique branch before or after proposal generation when the bottleneck is weak reasoning rather than idea quantity.
- Use `hypothesis-generation` when you start from anomalies, observations, or preliminary results rather than from open-ended ideation.
- Use `direction-evolution` after ranking, failed validation, or completed stages. It is the post-cycle operating layer, not an initial ideation skill.

Recommended shared artifacts:

- `outputs/<topic-slug>/idea_backlog.md` for raw candidate ideas
- `outputs/<topic-slug>/problem_map.md` for tensions, gaps, and stakeholder pain points
- `outputs/<topic-slug>/research_log.md` for session notes and pivots
- `outputs/<topic-slug>/template_gap_map.md` for template assumptions, untested seams, and missing evaluation slices
- `outputs/<topic-slug>/direction_shortlist.md` for ranked final candidates
- `outputs/<topic-slug>/novelty_report.json` for script-assisted novelty checks and similar-paper logs
- `outputs/<topic-slug>/stage_reflection.json` for evidence-driven plan updates after a completed stage
- `memory/ideation-memory.md` for cross-cycle records of promising, failed, and unresolved directions
- `ideations/ideation-<slug>-<timestamp>/session/` for multi-agent ideation sessions, briefs, graphs, and continuation lineage

## Repository Layout

```text
skills/
  README.md
  brainstorming-research-ideas/
    SKILL.md
  creative-thinking-for-research/
    SKILL.md
  idea-generation/
    SKILL.md
    references/
    scripts/
    templates/
  ideation/
    SKILL.md
    templates/
  direction-evolution/
    SKILL.md
    references/
    templates/
  scientific-brainstorming/
    SKILL.md
    references/
  hypothesis-generation/
    SKILL.md
    references/
  scientific-critical-thinking/
    SKILL.md
    references/
  novelty-assessment/
    SKILL.md
    references/
README.md
README.zh.md
LICENSE
```

## Usage

Prompt examples assume you load or reference the skill directly from this repository:

```text
Read skills/creative-thinking-for-research/SKILL.md and use 2-3 frameworks to generate five novel research directions for long-context software engineering agents.
```

```text
Read skills/brainstorming-research-ideas/SKILL.md and run the diverge-converge-refine workflow for evaluation gaps in trustworthy code generation.
```

```text
Read skills/idea-generation/SKILL.md and generate 5 feasible ideas for repository-level problem discovery in trustworthy coding agents, then save a novelty report for the top 2.
```

```text
Read skills/idea-generation/SKILL.md in template-grounded mode and use the current experiment template to find three under-tested failure modes plus two feasible new research directions grounded in the existing code.
```

```text
Read skills/direction-evolution/SKILL.md in memory-update mode and update memory/ideation-memory.md from this shortlist, novelty report, and failed validation notes so the next ideation cycle avoids dead ends.
```

```text
Read skills/direction-evolution/SKILL.md in stage-reflection mode and convert the latest baseline results into a JSON plan update that identifies unmet success signals and the next diagnostic stage.
```

```text
Read skills/ideation/SKILL.md and run a standard-depth ideation session for "tools that help researchers surface evaluation blind spots", producing a vision doc, idea briefs, and an ideation graph.
```

```text
Read skills/hypothesis-generation/SKILL.md and turn these anomalous evaluation results into 3 competing, testable hypotheses with differentiating predictions.
```

## Curation Rules

- A skill must directly support idea generation, problem discovery, or research-direction evaluation
- Skills for literature collection, experiments, implementation, paper formatting, or presentation should live in other repositories
- Prefer reusable, portable skills with clear routing boundaries
- Avoid mirroring large upstream repositories wholesale when a focused curation is enough

## Provenance

The current skill set was curated from a local source snapshot:

- `AI-research-SKILLs/21-research-ideation/brainstorming-research-ideas`
- `AI-research-SKILLs/21-research-ideation/creative-thinking-for-research`
- `agent-research-skills/skills/idea-generation`
- `agent-research-skills/skills/novelty-assessment`
- `ideation_team_skill/SKILL.md`
- `claude-scientific-skills/scientific-skills/scientific-brainstorming`
- `claude-scientific-skills/scientific-skills/hypothesis-generation`
- `claude-scientific-skills/scientific-skills/scientific-critical-thinking`
- `ai-scientist/ai_scientist/generate_ideas.py`
- `ai-scientist/README.md` (template structure)
- `ai-scientist/templates/nanoGPT_lite/prompt.json`
- `ai-scientist/templates/nanoGPT_lite/seed_ideas.json`
- `EvoScientist/EvoScientist/prompts.py`
- `EvoScientist/EvoScientist/subagent.yaml`

Only ideation- and problem-discovery-related skills are retained here. The normalized authoritative versions are the ones under [skills/](skills/).

## About

Open-source skills for research idea generation, problem discovery, and direction exploration in Research-Equality.
