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

- `brainstorming-research-ideas`
  适合把一个模糊主题展开成多个候选方向，再通过 diverge → converge → refine 流程筛选并收敛
- `creative-thinking-for-research`
  适合在思路卡住、缺乏新颖性或需要跨领域迁移时，使用认知科学框架生成更有跳跃性的研究方向
- `idea-generation`
  适合在已经有研究主题、部分 proposal 或代码上下文时，批量生成候选 idea，并给出 Interestingness / Feasibility / Novelty 评分
- `template-grounded-ideation`
  适合在已经有 `prompt.json`、`experiment.py`、`seed_ideas.json` 这类实验模板时，从现有代码边界、指标和资源约束里直接找 gap、生成可执行的新方向
- `novelty-assessment`
  适合在正式投入实现前，对候选方向做更严格的 novelty gate，判断是否只是已有工作的轻微变体
- `ideation`
  适合把一个概念种子交给多角色 ideation 流程持续展开，生成可继续迭代的 briefs、vision 文档、会话图谱与 lineage
- `ideation-memory-evolution`
  适合在 shortlist、验证失败或方向 pivot 之后，把“什么值得继续、什么该避免、为什么”沉淀成跨轮次可复用的 ideation memory
- `gap-driven-stage-reflection`
  适合在 baseline 或某个阶段结果出来后，围绕 unmet signals、可疑结果和新暴露的问题重写下一步计划
- `scientific-brainstorming`
  适合以科学研究伙伴的方式做开放式 brainstorm，发现研究空白、可疑假设和跨学科连接
- `hypothesis-generation`
  适合从异常现象、初步结果或观察出发，产出可检验的竞争性假设、预测与实验思路
- `scientific-critical-thinking`
  适合系统攻击一个 claim、paper 或研究方案，暴露偏差、混杂、证据薄弱点和真正值得追的问题

更详细的目录与路由规则见 [skills/README.md](skills/README.md)。

## 技能路由

- 当你缺的是“新角度”或“新颖性”，先用 `creative-thinking-for-research`
- 当你缺的是“结构化筛选”和“把点子落成研究方向”，用 `brainstorming-research-ideas`
- 当你已经有主题或代码上下文，想直接产出几条可执行候选方向时，用 `idea-generation`
- 当你已经有可运行的实验模板，想围绕现有代码接口、评测切片和资源约束找问题、出方向时，用 `template-grounded-ideation`
- 当你需要在真正开题前做最后一道“是否真的新”的检查时，用 `novelty-assessment`
- 当你希望进行更长时间、角色分工明确的 ideation session，而不是单轮 brainstorm 时，用 `ideation`
- 当你希望后续几轮 ideation 不再重复踩坑，而是继承上轮的判断和失败经验时，用 `ideation-memory-evolution`
- 当实验阶段已经拿到结果，下一步应该由证据而不是直觉驱动时，用 `gap-driven-stage-reflection`
- 当你需要一个更像科研合作者的开放式 brainstorm 对话时，用 `scientific-brainstorming`
- 当你已经有观察结果、异常现象或初步数据，想把它们收敛成可检验假设时，用 `hypothesis-generation`
- 当你想通过批判性分析来发现问题、识别证据漏洞或拆掉糟糕方案时，用 `scientific-critical-thinking`
- 当任务既要发散又要收敛时，可以按 `creative-thinking-for-research` → `brainstorming-research-ideas` → `template-grounded-ideation` / `idea-generation` → `novelty-assessment` → `ideation-memory-evolution` 串起来

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
