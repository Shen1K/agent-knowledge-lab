# 项目架构与 package 职责

这个项目的经验来自 GitHub Issue 分诊 v0.1 和 v0.2：知识不是一次性写出的 SOP，而是从数据、信息、案例、claim、决策点、playbook、eval 和反馈中逐步长出来的。

因此 `agent-knowledge-lab` 的目录不是普通文档分类，而是一条知识生产流水线。

```text
raw data / sources
  -> source notes
  -> case cards
  -> knowledge claims
  -> decision points
  -> playbooks
  -> evals
  -> execution reports
  -> change proposals
  -> updated knowledge
```

## 最终作用

项目最终要成为一套可被人类、Codex、Claude Code 和未来知识 Agent 共同使用的知识系统。

它的作用不是保存资料，而是把资料转化为可执行判断：

```text
数据提供事实
信息暴露模式
知识定义判断路径
playbook 组织行动
eval 验证结果
反馈推动知识更新
```

## Package 职责

### `knowledge/`

项目的核心知识工作区，也是未来持久知识的默认形态。

职责：

- 保存可被人类阅读、可被 Agent 检索的知识对象。
- 使用 YAML frontmatter 保存机器可读字段。
- 使用 `[[wiki links]]` 保存 Obsidian 友好的关系。
- 承载从原始材料到可执行知识的完整链路。

子目录职责：

- `00-index/`：知识入口、专题页、地图和开放问题。人类和 Agent 都应该从这里找方向。
- `01-raw/`：原始来源笔记和证据指针。它不负责解释，只负责保留来源、观察和限制。
- `02-cases/`：案例卡。把一次真实活动或公开实践重建成可讨论的 episode。
- `03-claims/`：知识主张。最小可用、可证伪、可评估的知识单元。
- `04-decision-points/`：决策点。把 claim 转化为执行时要回答的问题。
- `05-rules/`：规则。组合多个 claim，形成更操作化的判断规则。
- `06-playbooks/`：任务级流程。把决策点、规则和 claim 串成 Agent 可以执行的步骤。
- `07-evals/`：评估规则和评估报告。说明如何判断知识或输出是否有效。
- `08-changes/`：变更提案和变更日志。让知识迭代可追踪。

最终产物：

- 可浏览的知识图谱
- 可引用的知识 ID
- 可执行的 playbook
- 可评估的 claim
- 可审计的变更历史

### `skill/`

知识生成方法本身。

职责：

- 告诉 Agent 如何把原始材料转化为知识。
- 提供创建 source notes、case card、claim、decision point、playbook、eval 和 change proposal 的模板。
- 约束 AI 输出默认是 `hypothesis`，不能无证据升级为事实。

最终作用：

- 让 Codex、Claude Code 或其他 Agent 能用同一套方法生成知识。
- 让知识生成过程可重复，而不是依赖一次性的 prompt 灵感。

### `schemas/`

机器校验层。

职责：

- 定义知识对象的最低结构。
- 为未来 validator、indexer、graph service 或 API 做准备。
- 防止知识对象缺少关键字段，如 `id`、`type`、`status`、`evidence`、`relations`。

最终作用：

- 让 Markdown-first 的项目未来能迁移到数据库、图谱或服务。
- 让 Agent 在写文件后可以自动检查结构质量。

### `examples/`

教学样例，不是 live knowledge。

职责：

- 给新读者展示一组最小完整样例。
- 帮助 Agent 理解模板如何填写。
- 与 `knowledge/` 中的真实知识区分开，避免 example ID 与真实 ID 混淆。

最终作用：

- 降低上手门槛。
- 作为 Codex / Claude Code 学习项目格式的参考材料。

### `docs/`

项目方法论、执行记录和设计反思。

职责：

- 解释为什么这样设计。
- 记录每次 reference use case 的执行过程、假设变化和反馈。
- 保存迁移路径、自我审核和工具使用指南。

最终作用：

- 让人类理解项目背后的思考。
- 让 Agent 在继续迭代时知道历史上下文，而不是重复试错。

### `notes/`

讨论中产生的灵感和未结构化想法。

职责：

- 暂存还没进入正式知识系统的思考。
- 记录项目演进中的开放观点。

最终作用：

- 作为未来 source notes、claims 或 docs 的候选材料。
- 避免想法丢失，同时不污染正式知识区。

### `.obsidian/`

Obsidian 展示配置。

职责：

- 启用基本插件，如 graph 和 canvas。
- 让知识目录可以作为 vault 浏览。

最终作用：

- 支持人类以图谱、backlinks 和 canvas 方式理解知识关系。

## Codex / Claude Code 使用方式

### 进入项目后先读什么

Agent 应按这个顺序读取上下文：

1. `README.md`
2. `AGENTS.md` 或 `CLAUDE.md`
3. `docs/project-architecture.md`
4. `skill/SKILL.md`
5. `knowledge/00-index/home.md`
6. 当前任务相关专题页，例如 `knowledge/00-index/github-issue-triage.md`

### 生成知识时写到哪里

默认规则：

- 长期知识写入 Obsidian `knowledge base` vault。
- 如果任务明确要求更新项目模板、schema 或说明，再写入当前 repo。
- 原始来源先写 `01-raw/`。
- 真实案例写 `02-cases/`。
- 可证伪结论写 `03-claims/`。
- 执行逻辑写 `04-decision-points/` 和 `06-playbooks/`。
- 评估方式或评估结果写 `07-evals/`。
- 对已有知识的修改建议写 `08-changes/`。
- 执行过程写 `docs/executions/`。

### 执行一轮知识迭代

推荐流程：

```text
1. 明确任务目标和完成条件
2. 收集来源和真实样本
3. 写 source notes
4. 为关键样本写 case cards
5. 比较样本，提炼 claim
6. 把 claim 变成 decision point
7. 把 decision point 组织成 playbook
8. 写 eval 或 eval report
9. 更新专题页和 knowledge map
10. 记录 change proposal 或 execution report
```

### Agent 应避免什么

- 不要把总结直接当成知识。
- 不要在没有证据时把 `hypothesis` 升级为 `validated`。
- 不要只写 playbook，不写 claim 和 eval。
- 不要只写人类说明，不提供 Agent 可解析的 frontmatter。
- 不要直接覆盖已验证知识，应该先写 change proposal。
- 不要把项目级知识误当成通用知识。

## 从 GitHub Issue 分诊得到的架构调整

两轮 GitHub Issue 分诊说明：

- `01-raw` 必须记录来源强度，否则公开指南和真实 issue 会被打平。
- `02-cases` 必须保留每个真实样本，否则 claim 失去可追溯证据。
- `03-claims` 是知识最小单元，不应该直接跳到 SOP。
- `04-decision-points` 是 Agent 真正执行判断的地方。
- `06-playbooks` 应该组织行动顺序，而不是替代判断。
- `07-evals` 必须记录“如何知道知识有效”，否则无法迭代。
- `08-changes` 是知识系统自我修正的入口。

这让项目目的变得更清楚：

```text
agent-knowledge-lab 不是知识仓库。
它是把真实数据转化为可执行、可评估、可迭代知识的工作系统。
```
