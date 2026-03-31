# RE-idea-generation

[English](README.md) | [简体中文](README.zh.md)

一个聚焦于研究想法生成、问题发现与方向探索的权威技能仓库。

这个仓库只覆盖研究流程最前端的部分：识别值得做的问题、把模糊兴趣收敛成可研究的问题、在真正开始执行前形成可辩护的研究方向。它不是一个端到端研究工具箱，而是 Research-Equality 体系下专门承载 ideation 与 problem discovery 技能的精简仓库。

## 仓库定位

- 只保留和 idea generation、problem discovery、direction exploration 直接相关的 skills
- 将上游大仓库中的相关技能整理成更便携、可维护的结构
- 作为 Research-Equality 后续 ideation 类技能的权威落点

## 当前收录技能

技能目录位于 [skills/](skills/)。

### 主流程技能

- `creative-thinking-for-research`
  适合在卡思路、缺新颖性或需要认知框架来打开空间时使用
- `scientific-brainstorming`
  适合在还没有清晰假设前，用“科研合作者式”的开放对话来找方向
- `brainstorming-research-ideas`
  适合把模糊主题展开成候选方向，再通过 diverge → converge → refine 收敛
- `idea-generation`
  适合在已有主题、部分 concept 或 runnable scaffold 时，把方向写成带评分的候选 proposal
- `novelty-assessment`
  适合在正式投入前做最后一道 novelty gate

### 分支技能

- `hypothesis-generation`
  适合从异常现象、初步结果或观察出发，产出可检验的竞争性假设、预测与实验思路
- `scientific-critical-thinking`
  适合系统攻击一个 claim、paper 或研究方案，暴露偏差、混杂、证据薄弱点和真正值得追的问题

### 运行层技能

- `ideation`
  适合把一个概念种子交给多角色 ideation 流程持续展开，生成可继续迭代的 briefs、vision 文档、会话图谱与 lineage
- `direction-evolution`
  适合在 shortlist、验证失败、方向 pivot 或阶段结果出来后，同时维护 ideation memory 和 evidence-driven 的 next-step update

更详细的目录与路由规则见 [skills/README.md](skills/README.md)。

## 推荐主流程

为了尽量减少重叠，默认按这条线走：

1. 先选一个开场技能：
   `creative-thinking-for-research` 负责认知框架式发散，`scientific-brainstorming` 负责对话式科学探索。
2. 用 `brainstorming-research-ideas` 做结构化收敛和 shortlist。
3. 用 `idea-generation` 做 proposal 化：
   topic-first 场景走普通模式，已有 runnable scaffold 的场景走 template-grounded 模式。
4. 用 `novelty-assessment` 做最终 novelty gate。
5. 用 `direction-evolution` 把这一轮学到的判断和后续更新沉淀下来。

## 去冗余路由规则

- 默认不要同时用 `creative-thinking-for-research` 和 `scientific-brainstorming`。前者是框架型发散，后者是对话型发散，先选一个。
- `idea-generation` 已经包含 topic-first 和 template-grounded 两种模式，不再拆成两个 skill。
- `ideation` 是多角色长会话的 orchestration 层，不是默认主流程里的必经步骤。
- `scientific-critical-thinking` 是批判性分支，在“想法不够清楚”之外、当你主要缺的是 critique 时再用。
- `hypothesis-generation` 适合从异常现象或已有观察出发，不适合作为 blank-topic ideation 的默认入口。
- `direction-evolution` 只在 ranking、失败验证或阶段结果之后再用；它是 post-cycle 运行层，不是默认 ideation 入口。

建议把运行过程中的产物放到：

- `outputs/<topic-slug>/idea_backlog.md`
- `outputs/<topic-slug>/problem_map.md`
- `outputs/<topic-slug>/research_log.md`
- `outputs/<topic-slug>/template_gap_map.md`
- `outputs/<topic-slug>/direction_shortlist.md`
- `outputs/<topic-slug>/novelty_report.json`
- `outputs/<topic-slug>/stage_reflection.json`
- `memory/ideation-memory.md`
- `ideations/ideation-<slug>-<timestamp>/session/`

## 目录结构

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

## 使用方式

可以直接让代理读取对应技能文件，例如：

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

## 收录规则

- 技能必须直接服务于想法生成、问题发现或研究方向评估
- 文献检索、实验执行、工程实现、论文排版、演示汇报等能力不放在这个仓库
- 优先保留边界清晰、可复用、可迁移的技能
- 不复制整个上游大仓库，只保留当前主题真正需要的部分

## 来源说明

当前版本从本地上游快照中整理而来：

- `AI-research-SKILLs/21-research-ideation/brainstorming-research-ideas`
- `AI-research-SKILLs/21-research-ideation/creative-thinking-for-research`
- `agent-research-skills/skills/idea-generation`
- `agent-research-skills/skills/novelty-assessment`
- `ideation_team_skill/SKILL.md`
- `claude-scientific-skills/scientific-skills/scientific-brainstorming`
- `claude-scientific-skills/scientific-skills/hypothesis-generation`
- `claude-scientific-skills/scientific-skills/scientific-critical-thinking`
- `ai-scientist/ai_scientist/generate_ideas.py`
- `ai-scientist/README.md`（模板结构说明）
- `ai-scientist/templates/nanoGPT_lite/prompt.json`
- `ai-scientist/templates/nanoGPT_lite/seed_ideas.json`
- `EvoScientist/EvoScientist/prompts.py`
- `EvoScientist/EvoScientist/subagent.yaml`

仓库最终以 [skills/](skills/) 下的整理版本为准。

## 关于

Research-Equality 的开源研究想法生成与问题发现技能仓库。
