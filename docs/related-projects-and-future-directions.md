# 相邻项目参考与未来迭代方向

本文记录 GitHub 上与 `agent-knowledge-lab` 相邻的开源项目和方向。它不是竞品清单，而是后续分析项目定位、能力边界和迭代路线时的参考材料。

## 当前判断

GitHub 上已经有许多与 Agent 知识、记忆、Wiki、评估和 Obsidian 集成相关的项目，但暂时没有看到与 `agent-knowledge-lab` 完全同构的项目。

相邻项目大多在回答这些问题：

- Agent 如何把会话和项目上下文沉淀成 Wiki？
- Agent 如何存储和检索长期记忆？
- Agent 行为如何被 trace 和 eval？
- Obsidian 如何作为 Agent 可读写的知识界面？

`agent-knowledge-lab` 当前更关注另一个问题：

```text
如何把真实执行过程转化为可执行、可评估、可迭代的 Agent 工作知识？
```

它的差异点是把经验明确拆成：

```text
source notes
-> case cards
-> claims
-> decision points
-> playbooks
-> evals
-> change proposals
```

## 参考项目分类

### LLM Wiki / Obsidian Wiki

这一类项目最接近 `agent-knowledge-lab`，因为它们也强调把 LLM 或 coding agent 的上下文持续沉淀为互相链接的 Markdown 知识。

参考项目：

- [Pratiyush/llm-wiki](https://github.com/Pratiyush/llm-wiki)
- [Ar9av/obsidian-wiki](https://github.com/Ar9av/obsidian-wiki)
- [NiharShrotri/llm-wiki](https://github.com/NiharShrotri/llm-wiki)

相似点：

- 使用 Markdown 或 Obsidian 作为知识载体。
- 强调跨会话保存知识。
- 让知识变成可浏览、可链接、可持续更新的 Wiki。
- 适合为 coding agent 提供项目上下文。

差异点：

- LLM Wiki 类项目更偏“持续生成和维护知识库”。
- `agent-knowledge-lab` 更偏“从执行经验中抽取判断逻辑，并把判断逻辑连接到 eval 和变更机制”。
- LLM Wiki 主要解决知识沉淀；`agent-knowledge-lab` 还要求知识能指导行动、接受评估、被反馈修改。

可借鉴方向：

- 自动从 Codex、Claude Code、Cursor 等 session 中提取候选知识。
- 把项目上下文编译成适合 Agent 启动时读取的入口页。
- 改进 Obsidian graph、backlinks 和 topic index 的体验。

### Agent Memory / Knowledge Graph

这一类项目更偏底层基础设施，关注长期记忆、关系图谱、MCP server 和检索能力。

参考项目：

- [neo4j-labs/agent-memory](https://github.com/neo4j-labs/agent-memory)
- [agentralabs/agentic-memory](https://github.com/agentralabs/agentic-memory)
- [memory-graph/memory-graph](https://github.com/memory-graph/memory-graph)
- [MemPalace/mempalace](https://github.com/MemPalace/mempalace)
- [memvid/memvid](https://github.com/memvid/memvid)

相似点：

- 都试图解决 Agent 的长期上下文问题。
- 都重视知识或记忆之间的关系。
- 都可能通过 MCP 或 API 给 Agent 提供可调用能力。

差异点：

- Agent Memory 类项目更关注“如何存、如何查、如何关联”。
- `agent-knowledge-lab` 更关注“什么经验值得成为知识、知识如何表达成判断、如何知道这条知识有用”。
- Memory 系统可以作为未来后端，但不应该替代知识生产方法本身。

可借鉴方向：

- 为 `knowledge/` 建立索引器。
- 把 `relations` 转成图数据库或 graph API。
- 支持按任务目标召回相关 claim、decision point、playbook 和 eval。
- 支持 supersession、conflict、stale knowledge 等生命周期关系。

### Agent Eval / Trace

这一类项目专注于记录 Agent 执行过程，并对 Agent 行为进行自动化评估。

参考项目：

- [agentevals-dev/agentevals](https://github.com/agentevals-dev/agentevals)

相似点：

- 都承认 Agent 输出需要被评估，而不是只被保存。
- 都希望从真实执行结果中获得反馈信号。
- 都适合分析 Agent 是否按预期执行任务。

差异点：

- Eval / trace 项目更偏评估基础设施。
- `agent-knowledge-lab` 需要把评估结果回流到具体知识对象，例如 claim、decision point、playbook 或 change proposal。

可借鉴方向：

- 建立“知识前 / 知识后”的对照评估。
- 记录 Agent 实际使用了哪些知识 ID。
- 把失败样本回写为 case card 或 change proposal。
- 用 trace 评估 Agent 是否真的遵循 decision point，而不是只在最终答案中声称使用了知识。

### Obsidian MCP / Knowledge Tooling

这一类项目提供工具连接层，使 Agent 能读写 Obsidian vault 或 Markdown 知识库。

参考项目：

- [cyanheads/obsidian-mcp-server](https://github.com/cyanheads/obsidian-mcp-server)
- [letta-ai/letta-obsidian](https://github.com/letta-ai/letta-obsidian)

相似点：

- 都把 Obsidian 当作人类可用的知识界面。
- 都可以让 Agent 与 Markdown 知识库交互。

差异点：

- Obsidian MCP 类项目主要解决工具接入问题。
- `agent-knowledge-lab` 主要解决知识对象如何设计、如何评估、如何迭代的问题。

可借鉴方向：

- 后续可以接入 Obsidian MCP，让 Agent 直接查询 vault。
- 通过 MCP 提供 `find_claims`、`find_playbooks`、`propose_change` 等动作。
- 把 Obsidian 作为人类评审层，而不是只作为文件夹。

## 项目定位

更准确的定位不是“另一个 Agent memory 项目”，而是：

```text
Agent working knowledge lab
```

也可以描述为：

```text
把执行经验转化为可测试 Agent 工作知识的 Markdown-first 系统。
```

它位于几个方向之间：

```text
LLM Wiki          -> 负责持续沉淀项目知识
Agent Memory      -> 负责记忆存取和关系检索
Agent Eval        -> 负责行为评估和反馈采集
agent-knowledge-lab -> 负责把经验转化为 claim / decision / playbook / eval
```

## 未来迭代方向

### 1. 做硬评估

当前 GitHub Issue 分诊 v0.1 和 v0.2 已经证明方法可以跑通，但还需要更硬的对照评估。

建议方向：

- 准备固定 issue 样本集。
- 比较无知识、普通 prompt、使用 `agent-knowledge-lab` 知识三种条件。
- 评估 needs-info 误判率、actionability 判断质量、reply draft 可用性和维护者接受度。
- 记录 Agent 使用了哪些知识 ID。
- 把失败样本转成 case card 或 change proposal。

### 2. 建立最小工具链

Markdown-first 适合早期探索，但需要最小工具链让知识更稳定地被 Codex 和 Claude Code 使用。

建议方向：

- `validate`：检查 frontmatter、id、type、status、evidence 和 relations。
- `index`：生成 topic index 和 relation graph。
- `context`：根据任务构造 Agent prompt context。
- `trace`：记录一次执行引用了哪些知识。
- `eval`：对固定样本运行评估。
- `change`：从失败样本生成变更提案。

### 3. 扩展第二个 reference use case

GitHub Issue 分诊是好的起点，但需要第二个不同类型场景验证迁移性。

候选方向：

- GitHub PR review。
- CI failure diagnosis。
- bug report to reproduction。
- customer support triage。
- codebase onboarding。
- product feedback classification。

优先选择标准：

- 有足够真实样本。
- 有可观察反馈。
- Agent 当前容易犯重复错误。
- 人类专家存在稳定判断路径。
- 输出可以被明确评估。

### 4. 构造 Agent prompt context

项目最终要更好地服务 Codex 和 Claude Code，因此需要从知识库中生成任务级 prompt context。

建议方向：

- 从 topic page 找到相关 claim、decision point、playbook 和 eval。
- 按任务阶段组织 prompt，而不是简单拼接全文。
- 在 prompt 中保留知识 ID，便于追踪执行使用情况。
- 明确哪些知识是 domain-level，哪些是 project-level。
- 输出时要求 Agent 标注 `knowledge_used`。

### 5. 明确知识生命周期

为了避免知识库变成新的垃圾场，需要更明确的生命周期。

建议状态：

- `draft`
- `hypothesis`
- `reviewed`
- `validated`
- `superseded`
- `deprecated`

建议规则：

- AI 新生成知识默认是 `hypothesis`。
- 只有经过人工评审或评估证据支持，才能升级。
- 修改 validated knowledge 时先写 change proposal。
- 旧知识被替代时保留 supersession 关系。

## 后续分析问题

- `agent-knowledge-lab` 应该优先做 skill、CLI 工具，还是 MCP server？
- 知识对象最小 schema 应该固定到什么程度？
- 如何量化“知识提升了 Agent 执行质量”？
- 是否需要设计一个 `knowledge_used` trace 格式？
- Obsidian vault 和 repo 之间如何同步，才能同时服务人类浏览和 Agent 执行？
- 哪些能力应该保持 Markdown-first，哪些能力应该迁移到图数据库或服务？

## 暂定结论

`agent-knowledge-lab` 的差异化不在存储记忆，也不在生成 Wiki，而在于定义一条从执行经验到可测试工作知识的链路。

如果后续要继续推进，最重要的不是扩展更多文档，而是把以下三件事做实：

```text
知识对象 schema
Agent prompt context 构造
知识前后效果评估
```
