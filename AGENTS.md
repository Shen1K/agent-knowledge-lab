# Codex 使用说明

你正在 `agent-knowledge-lab` 项目中工作。这个项目的目标是把真实数据和执行反馈转化为人类与 Agent 都能使用的知识。

## 必读顺序

1. `README.md`
2. `docs/project-architecture.md`
3. `skill/SKILL.md`
4. `knowledge/00-index/home.md`
5. 与任务相关的专题页，例如 `knowledge/00-index/github-issue-triage.md`

## 项目心智模型

不要把这个仓库当成普通文档仓库。它是一条知识生产链：

```text
source notes -> case cards -> claims -> decision points -> playbooks -> evals -> changes
```

知识不是答案，而是让 Agent 按正确顺序处理问题的判断路径。

## 默认写入位置

长期知识默认写入 Obsidian vault：

```text
/Users/shenkai/Library/Mobile Documents/iCloud~md~obsidian/Documents/knowledge base
```

只有在用户明确要求更新项目本身、模板、schema、说明或示例时，才写入当前 repo。

## 写知识的规则

- 原始来源写入 `knowledge/01-raw/`。
- 真实样本写入 `knowledge/02-cases/`。
- 可证伪结论写入 `knowledge/03-claims/`。
- 执行判断写入 `knowledge/04-decision-points/`。
- 任务流程写入 `knowledge/06-playbooks/`。
- 评估规则或评估报告写入 `knowledge/07-evals/`。
- 修改已有知识的建议写入 `knowledge/08-changes/`。
- 执行过程写入 `docs/executions/`。

## 质量要求

- 使用稳定 `id`。
- 保留 YAML frontmatter。
- 使用 Obsidian `[[wiki links]]` 连接知识。
- AI 生成知识默认 `status: hypothesis`。
- 不要把 project-level knowledge 当成 domain-level knowledge。
- 不要覆盖已验证知识；提出 change proposal。
- 每个 actionable claim 都应有 evaluation。

## GitHub Issue 分诊经验

当前最完整的 reference use case 是 GitHub Issue 分诊。它证明了：

```text
先判断信息是否足够支撑下一步决策，再做分类、路由、duplicate 或关闭。
```

继续相关任务时，优先读取：

- `knowledge/00-index/github-issue-triage.md`
- `knowledge/03-claims/github-issue-triage/claim-github-issue-info-sufficiency-before-classification.md`
- `knowledge/06-playbooks/github-issue-triage/playbook-github-issue-info-first-triage.md`
