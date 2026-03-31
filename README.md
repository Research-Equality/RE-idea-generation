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

### Core Ideation Skills

- `brainstorming-research-ideas`: structured diverge → converge → refine workflows for turning vague topics into ranked research candidates
- `creative-thinking-for-research`: cognitive-science-inspired frameworks for novelty generation, analogy transfer, reformulation, and constraint breaking
- `idea-generation`: generate candidate ideas from a topic, codebase, or existing concept, then score them on interestingness, feasibility, and novelty
- `template-grounded-ideation`: generate ideas from an executable template package (`prompt.json` + `experiment.py` + `seed_ideas.json`), surfacing feasible gaps, intervention points, and next experiments grounded in existing code
- `novelty-assessment`: run a harsher novelty gate before committing to a direction, with multi-round literature search and differentiation checks
- `ideation`: run a structured multi-agent ideation session around a concept seed, with role separation, session memory, and reusable artifacts for continued problem discovery
- `ideation-memory-evolution`: preserve promising directions, failed directions, and reusable decision heuristics across ideation and validation cycles
- `gap-driven-stage-reflection`: turn completed stage results into concrete plan updates, unmet-signal diagnoses, and next-stage proposals
- `scientific-brainstorming`: use a conversational, domain-aware scientific brainstorming partner to surface research gaps, assumptions, and interdisciplinary angles
- `hypothesis-generation`: turn observations, anomalies, or preliminary data into competing testable hypotheses with predictions and experiment ideas
- `scientific-critical-thinking`: interrogate claims, methods, evidence quality, and confounders to expose flaws, hidden assumptions, and genuine open problems

See [skills/README.md](skills/README.md) for the skill catalog and routing guidance.

## Skill Routing

To keep overlap low, the repository uses a layered ideation workflow:

- Start with `creative-thinking-for-research` when the problem is creative blockage, local-optimum thinking, or a need for genuinely novel angles
- Use `brainstorming-research-ideas` when the goal is to structure a session, generate multiple candidates, rank them, and sharpen one into a concrete direction
- Use `idea-generation` when you already have a topic, partial proposal, or code context and want concrete candidate ideas plus explicit scoring
- Use `template-grounded-ideation` when you already have a runnable experiment scaffold or benchmark template and want ideas constrained by real code seams, metrics, and resource limits
- Use `novelty-assessment` as the final novelty gate before committing to implementation or project planning
- Use `ideation` when a single prompt is not enough and you want a longer-form session with explicit divergent/convergent roles, session lineage, and reusable artifacts
- Use `ideation-memory-evolution` after shortlisting, failed validation, or pivots when you want future ideation to retain directional judgment instead of restarting cold
- Use `gap-driven-stage-reflection` when a baseline or experiment stage has completed and the next problem to solve should be derived from evidence, not intuition
- Use `scientific-brainstorming` when you want a scientific thought partner for open-ended ideation before you have a crisp hypothesis
- Use `hypothesis-generation` when you already have observations or a phenomenon and need testable, competing explanations
- Use `scientific-critical-thinking` when the best next move is to attack a claim, paper, or draft plan to find weak assumptions and underexplored gaps
- Use the full chain for deeper work: generate raw ideas with `creative-thinking-for-research`, structure them with `brainstorming-research-ideas`, use `template-grounded-ideation` when code constraints dominate, turn finalists into scored proposals with `idea-generation`, stress-test them with `novelty-assessment`, and retain learning with `ideation-memory-evolution`

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
  template-grounded-ideation/
    SKILL.md
    references/
    templates/
  ideation/
    SKILL.md
    templates/
  ideation-memory-evolution/
    SKILL.md
    references/
    templates/
  gap-driven-stage-reflection/
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
Read skills/template-grounded-ideation/SKILL.md and use the current experiment template to find three under-tested failure modes plus two feasible new research directions grounded in the existing code.
```

```text
Read skills/ideation-memory-evolution/SKILL.md and update memory/ideation-memory.md from this shortlist, novelty report, and failed validation notes so the next ideation cycle avoids dead ends.
```

```text
Read skills/gap-driven-stage-reflection/SKILL.md and convert the latest baseline results into a JSON plan update that identifies unmet success signals and the next diagnostic stage.
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
