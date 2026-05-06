# 路线图

## 阶段 1：轻量 Skill

目标：让知识生成方法显性化、可使用、易编辑。

交付物：

- 把原始材料转化为知识的 skill 指令。
- 案例、知识主张、决策点、playbook、eval 和变更提案的 Markdown 模板。
- Obsidian 兼容的文件夹结构和链接。
- GitHub Issue 分诊示例。
- 面向未来验证器的基础 JSON schema。

成功标准：

- 人类能在 10 分钟内读懂项目和方法。
- 模型能按照 skill 创建案例卡和知识主张。
- 每个生成的知识主张都有范围、证据、边界、状态、使用方式和评估方法。

## 阶段 2：知识 Agent

目标：在保留人类评审权的前提下，自动化重复的知识工作。

潜在能力：

- 从文件、GitHub、网站或聊天导出中摄入原始材料。
- 从原始证据生成案例卡。
- 提出知识主张和决策点。
- 检测冲突、重复、证据缺失和过期知识。
- 生成变更提案，而不是直接重写已验证知识。
- 跟踪 Agent 使用了哪些知识，以及结果表现如何。

护栏：

- AI 生成的知识默认 `status: hypothesis`。
- 已验证知识需要人类批准，或有清晰的评估证据。
- 每次更新都必须保留来源和变更历史。

## 阶段 3：知识服务

目标：把系统变成协作基础设施。

潜在能力：

- 用于浏览、评审和编辑知识的 Web UI。
- 知识图谱和关系浏览器。
- Eval 看板。
- 评审流程和权限。
- 多领域、多 Agent 的知识空间。
- 供 Agent 检索、引用和提交知识更新提案的 API。

## 开放问题

- 知识主张的最小 schema 应该是什么？
- 如何把反馈归因到具体知识单元？
- 如何处理通用、领域、项目和工具层知识之间的冲突？
- 什么时候可以把一个假设升级为已验证知识？
- 哪些内容应该继续保留为 Markdown，哪些应该迁移到数据库或图谱？

## 相邻项目参考

GitHub 上已经有 LLM Wiki、Agent Memory、Agent Eval 和 Obsidian MCP 等相邻方向。它们为项目定位和后续工具链提供参考，但 `agent-knowledge-lab` 的核心差异仍然是把真实执行经验转化为 `claim -> decision point -> playbook -> eval -> change proposal`。

详细参考见 [docs/related-projects-and-future-directions.md](docs/related-projects-and-future-directions.md)。
