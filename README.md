# Agent Knowledge Lab

从原始材料到可使用的 Agent 知识。

Agent Knowledge Lab 是一个开放项目，用来设计一套人类和 AI Agent 都能使用的知识系统。它一开始是一个轻量 skill：一套可重复的方法，把文档、数据、图片、issue、聊天记录和执行轨迹转化为结构化知识。如果这套方法被证明有用，它可以继续发展成更重的知识 Agent，之后再演进成协作服务。

## 为什么做

大多数 Agent 项目会讨论模型、prompt、工具和记忆。但更难的问题是知识：Agent 如何学习人类真实做事的方式，这些知识如何被记录，又如何通过反馈持续改进。

这个项目有几个基本假设：

- 知识不是一堆文档。
- AI 生成的知识在被验证前都是假设。
- 有用的 Agent 知识必须能被人类理解。
- 知识应该保留证据、边界、状态、关系和变更历史。
- 第一版系统应该足够轻，方便编辑；同时也要有结构，方便以后迁移。

## 核心想法

进入一个新领域时，不要直接从原始材料跳到 SOP。先重建人类活动。

```text
原始材料
  -> 活动重建
  -> 案例卡
  -> 知识主张
  -> 决策点
  -> 规则和 playbook
  -> eval 与反馈
  -> 更新后的知识
```

最小单元是 **知识主张**：一个有范围、有证据、可使用、可证伪的主张，可以指导人类或 Agent 行动。

## 项目结构

```text
skill/        轻量 skill 和知识生成模板。
knowledge/    适合 Obsidian 使用的知识工作区。
examples/     示例，从 GitHub Issue 分诊开始。
schemas/      面向未来工具的机器可读 schema。
docs/         哲学、设计说明、迁移路径和自我审核。
notes/        持续讨论中形成的项目思考笔记。
```

更完整的 package 职责、知识生产链路和 Agent 使用方式见 [docs/project-architecture.md](docs/project-architecture.md)。

## 快速开始

1. 用 Obsidian、VS Code 或任意 Markdown 编辑器打开这个文件夹。
2. 阅读 [PRINCIPLES.md](PRINCIPLES.md)。
3. 阅读 [docs/project-architecture.md](docs/project-architecture.md)。
4. 阅读 [skill/SKILL.md](skill/SKILL.md)。
5. 从 [skill/templates](skill/templates) 复制模板到对应的 `knowledge/` 文件夹。
6. 试着阅读 [examples/github-issue-triage](examples/github-issue-triage) 中的示例。

## 给 Codex / Claude Code 使用

这个项目已经提供 Agent 入口说明：

- Codex 读取 [AGENTS.md](AGENTS.md)。
- Claude Code 读取 [CLAUDE.md](CLAUDE.md)。

Agent 进入项目后应该按这个顺序理解上下文：

```text
README.md
-> AGENTS.md / CLAUDE.md
-> docs/project-architecture.md
-> skill/SKILL.md
-> knowledge/00-index/home.md
-> 具体任务专题页
```

默认约定：

- 当前 repo 维护方法、模板、schema、示例和项目说明。
- 长期知识默认沉淀到 Obsidian `knowledge base` vault。
- AI 生成的新知识默认是 `hypothesis`。
- 变更已验证知识时，先写 change proposal。

## 知识类型

- **原始材料**：原始证据。尽量保持不改写。
- **案例卡**：对一次人类活动片段的重建。
- **知识主张**：最小的、可使用且可测试的知识单元。
- **决策点**：任务中需要判断的时刻。
- **规则**：由一个或多个知识主张组合出的指令。
- **Playbook**：任务级操作指南。
- **Eval 规则**：判断知识或输出是否有效的方法。
- **变更提案**：基于证据或反馈提出的知识更新建议。

## 关系模型

知识关系记录在两个地方：

- YAML frontmatter：方便 Agent 和工具解析。
- `[[wiki links]]`：方便人在 Obsidian 中浏览。

第一版刻意保持关系类型较少：

```text
depends_on
supports
conflicts_with
generalizes
specializes
derived_from
```

## 当前示例

第一个验证领域是 **GitHub Issue 分诊**。

这个领域有价值，因为它有廉价的持续输入、可见的人类行为，以及相对清晰的反馈信号：标签、维护者回复、issue 关闭、重复 issue 链接和用户补充信息。

这条线已经跑过两轮：

- v0.1：公开分诊实践 + 1 个真实 Next.js issue，验证 information sufficiency gate。
- v0.2：10 个真实 Next.js issue 小样本，提炼出项目级 claim，并更新 eval report。

## 参考项目

与 LLM Wiki、Agent Memory、Agent Eval 和 Obsidian MCP 等相邻项目的比较，见 [docs/related-projects-and-future-directions.md](docs/related-projects-and-future-directions.md)。

## 路线图

见 [ROADMAP.md](ROADMAP.md)。

简短版本：

1. **Skill**：轻量模板和方法。
2. **知识 Agent**：提出案例卡、知识主张、冲突和更新。
3. **服务**：协作 UI、评审流程、图谱、eval 看板和 Agent API。

## 贡献

这个项目为讨论和迭代而设计。见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## License

MIT. 见 [LICENSE](LICENSE)。
