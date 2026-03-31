---
name: ideation
description: Orchestrates multi-agent ideation and problem discovery around a concept seed. Use when you need a longer-form session with explicit divergent and convergent roles, reusable artifacts, and continuation support.
version: 1.0.0
author: Research-Equality
license: MIT
tags: [Research Ideation, Problem Discovery, Multi-Agent Collaboration, Session Design]
dependencies: []
---

# Ideation

Structured multi-agent concept exploration for idea generation and problem discovery.

This curated version keeps only the ideation-focused parts of the upstream skill:

- Plan a session from a concept seed
- Run a role-separated ideation dialogue
- Produce reusable ideation artifacts
- Continue a prior session with lineage

It intentionally excludes downstream production work such as presentations, HTML distribution pages, PDFs, and PRD generation. Those belong in neighboring repositories.

## When to Use This Skill

- A concept is still fuzzy and needs sustained exploration rather than a one-shot brainstorm
- You want explicit separation between divergent generation, convergent editing, synthesis, and optional research
- You need artifacts that preserve the session's logic: briefs, ideation graph, snapshots, and a vision document
- You want to continue or branch from prior ideation sessions instead of restarting from scratch

**Do NOT use this skill when**:

- You only need a quick solo brainstorm; use `brainstorming-research-ideas`
- You need cognitive novelty frameworks rather than a managed session; use `creative-thinking-for-research`
- You already have candidate ideas and just need scoring or novelty checks; use `idea-generation` or `novelty-assessment`
- You are doing implementation planning, experiments, or paper writing

## Core Roles

| Role | Function |
|------|----------|
| **Arbiter** | Team lead. Configures the session, evaluates idea reports, and decides when the session has converged. |
| **Free Thinker** | Divergent generation. Pushes outward, proposes surprising directions, and resists premature filtering. |
| **Grounder** | Convergent editing. Keeps the dialogue connected to the brief, spots dead ends, and selects which directions deserve more oxygen. |
| **Writer** | Synthesis and memory. Maintains the ideation graph, snapshots, briefs, session summary, and final vision document. |
| **Explorer** | Optional factual research support. Investigates background, prior art, adjacent domains, or open questions requested by the team. |

## Execution Model

This skill works best in environments that support persistent multi-agent sessions with peer messaging.

- If your environment supports teams, messages, and task assignment: run it as a real multi-agent workflow.
- If your environment does not: emulate the roles in round-robin order while preserving the same artifacts and evaluation rules.

The important part is **role separation**, not a specific tool API.

## Session Layout

Each ideation run creates a timestamped directory:

```text
ideations/ideation-<slug>-<YYYYMMDD-HHMMSS>/
  session/
    session-config.yaml
    VISION_<slug>.md
    SESSION_SUMMARY.md
    ideation-graph.md
    LINEAGE.md
    sources/
    research/
    briefs/
    idea-reports/
    snapshots/
```

Use the current working directory unless the project already has an established output location.

## Templates

This skill depends on the templates in `templates/`:

- `templates/session-config.yaml`
- `templates/idea-report.md`
- `templates/idea-brief.md`
- `templates/ideation-graph.md`
- `templates/lineage.md`
- `templates/session-summary.md`
- `templates/vision-document.md`

## Action Detection

Support these entry patterns:

```text
ideation <concept>
ideation
ideation continue <path-or-keyword>
```

Interpret them as:

- `ideation <concept>`: start a new session and run the Plan action
- `ideation`: ask for the concept, then run the Plan action
- `ideation continue <ref>`: resume or branch from a previous session

## Action 1: Plan

The Plan action is a solo operation. Do not start the ideation team until the session is configured.

### P1. Analyze the Concept Seed

Read the seed material first. It can be:

- Inline text
- A local file
- A folder of prior sources
- A short concept note or issue description

Assess:

- Domain complexity
- Ambiguity
- Scope breadth
- Whether factual research is needed before or during ideation

### P2. Capture Sources

Create a self-contained session package under `session/sources/`.

Always capture:

- The user's request as `session/sources/request.md`
- Any provided concept file or files
- A `session/sources/manifest.md` inventory

If URLs or external references were explicitly provided, save fetched or summarized copies into `session/sources/` instead of keeping only links.

### P3. Create the Session Directory

Create the timestamped `ideations/ideation-<slug>-<timestamp>/session/` structure before the interview finishes so the output location is stable for the rest of the run.

### P4. Interview the User

Ask only what is needed to configure the session.

Always collect:

1. **Concept** if one was not provided
2. **Depth**
3. **Research mode**

Recommended depth options:

| Level | Intent | Typical Range |
|-------|--------|---------------|
| `quick` | Fast scan of the space | 2-3 directions |
| `standard` | Balanced exploration | 3-5 directions |
| `deep` | Stronger development and revisiting | 5-8 directions |
| `exhaustive` | Broadest mapping and repeated refinement | 8+ directions |

Research modes:

- `none`: no dedicated researcher
- `on-demand`: spawn or emulate the Explorer only when the team requests facts
- `parallel`: run Explorer alongside ideation
- `pre-session`: Explorer researches first, then thinkers begin

### P5. Build `session-config.yaml`

Use `templates/session-config.yaml` and fill:

- `concept_seed`
- `concept_slug`
- lineage fields
- `depth.level`
- optional overrides for report thresholds
- `research.mode`
- `research.topics`

### P6. Confirm and Transition

Summarize:

- Concept
- Depth
- Research mode
- Output directory

Then transition to Action 2.

## Action 2: Ideate

The Ideate action runs the session itself.

### I1. Create the Team

Create or emulate the following participants:

- Arbiter
- Free Thinker
- Grounder
- Writer
- Explorer if research mode is not `none`

### I2. Inject Depth Directives

Depth is not advisory. It changes behavior.

| Depth | Begin Convergence Check After | Force Convergence Check After | Interesting Threshold | Snapshot Frequency |
|-------|-------------------------------|-------------------------------|----------------------|-------------------|
| `quick` | 1 report | 3 reports | 1 of 4 criteria | 1-2 |
| `standard` | 3 reports | 6 reports | 2 of 4 criteria | 3-5 |
| `deep` | 5 reports | 12 reports | 3 of 4 criteria | 5-8 |
| `exhaustive` | 8 reports | no fixed cap | 4 of 4 criteria | 8+ |

The four "interesting" criteria are:

- Compelling
- Somewhat new
- A different take
- Substantive

### I3. Start the Dialogue

The opening sequence should be:

1. Free Thinker reads the seed and proposes initial directions
2. Grounder responds, keeps the session on brief, and selects which directions deserve development
3. Writer initializes `session/ideation-graph.md`
4. Explorer begins research if the mode requires it

### I4. Initial Task Set

Only initialize a minimal task set:

1. Read the seed and begin dialogue
2. Initialize the ideation graph
3. Produce the first idea report after meaningful exploration
4. Run the first research task if Explorer is active

Do not overplan. New tasks should emerge from the session.

### I5. Dialogue Rhythm

The Free Thinker and Grounder should alternate naturally:

- Free Thinker proposes, reframes, combines, and inverts
- Grounder picks, trims, redirects, and pushes for relevance
- Writer observes instead of participating
- Arbiter does not generate ideas directly

### I6. Idea Reports

When a direction becomes coherent enough to evaluate, write an idea report to:

```text
session/idea-reports/IDEA_<short-slug>.md
```

Use `templates/idea-report.md`.

Each report should explain:

- the idea
- the key insight
- how the team got there
- the Grounder's take
- the Free Thinker's vision
- open threads
- a recommendation to the Arbiter

### I7. Arbiter Evaluation Loop

Each time an idea report arrives, the Arbiter classifies it as:

- `interesting`
- `needs more conversation`
- `not interesting`

Use these rules:

- `interesting`: clears the current depth threshold and deserves preservation
- `needs more conversation`: has real promise but is underdeveloped, too muddy, or missing tension
- `not interesting`: too obvious, too weakly connected, or no longer worth more session time

The Arbiter should never solve the idea. The Arbiter only routes and evaluates.

### I8. Research Requests

If the team needs facts mid-session:

1. Route a question to the Explorer
2. Save the result under `session/research/`
3. Broadcast the findings back into the ideation dialogue

Use research to sharpen, not to derail. The Explorer should answer specific questions, not turn the session into a literature review.

### I9. Convergence

Convergence is reached when:

1. The depth-specific minimum report threshold has been met
2. The interesting list has enough range
3. Reports have been challenged and refined enough for the chosen depth
4. Additional dialogue yields diminishing returns

At the forced check threshold, the Arbiter must evaluate whether the session should close even if dialogue still feels productive.

### I10. Writer Finalization

When convergence is signaled, the Writer produces:

- a final snapshot
- an idea brief for each interesting item using `templates/idea-brief.md`
- `session/SESSION_SUMMARY.md` using `templates/session-summary.md`
- `session/VISION_<slug>.md` using `templates/vision-document.md`

The Writer is also responsible for keeping `session/ideation-graph.md` current throughout the session.

## Action 3: Continue

Continuation creates a **new versioned directory**. Never modify the parent session.

### C1. Resolve the Parent Session

Allow:

- direct paths
- keyword search against `ideations/ideation-*`

If multiple matches exist, show summaries and ask the user which session to continue.

### C2. Read Parent Context

Read:

- `session/session-config.yaml`
- `session/VISION_<slug>.md`
- `session/briefs/*.md`
- `session/ideation-graph.md`
- `session/SESSION_SUMMARY.md`

### C3. Mini-Interview

Collect:

1. What to deepen or revisit
2. Desired depth for the continuation
3. Whether to branch from a specific thread if applicable

### C4. Create Versioned Output

Use versioned naming:

```text
ideation-voice-memos-20260219-143052/
ideation-voice-memos-v2-20260221-091500/
ideation-voice-memos-v2a-20260222-150000/
```

Populate `session/LINEAGE.md` from `templates/lineage.md`.

### C5. Carry Forward the Right Materials

Copy:

- `session/sources/`
- a modified `session-config.yaml`

Reference in prompts:

- prior vision document
- prior briefs
- prior ideation graph
- specific focus for this continuation

The continuation should extend the previous work, not restart it.

## Role Prompt Capsules

Use these as compact spawn instructions or emulation rules.

### Free Thinker

- Be divergent and generative
- Do not self-censor too early
- Prefer unexpected connections, inversions, reframings, and "what if" moves
- Collaborate on idea reports once a direction has enough shape
- Ask for research when facts matter

### Grounder

- Keep the session tied to the brief
- Select what deserves more depth and kill what does not
- Notice ruts, repetition, and audience irrelevance
- Be direct, but do not collapse the session into negativity
- Push the Free Thinker toward the strongest emerging direction

### Writer

- Observe, document, and synthesize
- Do not participate in ideation
- Keep the ideation graph current in real time
- Produce snapshots, briefs, session summary, and vision document
- Preserve meaningful language from the dialogue when it carries intent

### Explorer

- Answer specific factual questions only
- Save research notes under `session/research/RESEARCH_<topic>.md`
- Report findings in a way that the ideation team can immediately use
- Do not turn the session into a broad survey

## Output Checklist

By the end of a successful session, the repository should contain:

- `session/session-config.yaml`
- `session/sources/request.md`
- `session/sources/manifest.md`
- `session/ideation-graph.md`
- `session/snapshots/SNAPSHOT_*.md`
- `session/idea-reports/IDEA_*.md`
- `session/briefs/BRIEF_*.md`
- `session/SESSION_SUMMARY.md`
- `session/VISION_<slug>.md`
- `session/LINEAGE.md` for continuations

## Related Skills

- In this repository: [creative-thinking-for-research](../creative-thinking-for-research/), [brainstorming-research-ideas](../brainstorming-research-ideas/), [idea-generation](../idea-generation/), [novelty-assessment](../novelty-assessment/)
- Companion repositories: literature-search, implementation-planning, paper-writing
