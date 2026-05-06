# Claude Code 使用说明

这个仓库用于研究和维护 Agent Knowledge Lab：一套把真实数据、执行过程和反馈转化为可执行知识的方法。

## 首要目标

帮助人类和 Agent 共同积累知识，而不是只生成总结或 SOP。

核心流程：

```text
raw sources
-> source notes
-> case cards
-> knowledge claims
-> decision points
-> playbooks
-> evals
-> change proposals
```

## 进入仓库后先读

1. `README.md`
2. `docs/project-architecture.md`
3. `skill/SKILL.md`
4. `knowledge/00-index/home.md`

如果任务与 GitHub Issue 分诊相关，继续读：

- `knowledge/00-index/github-issue-triage.md`

## 目录职责

- `knowledge/`：正式知识对象。
- `skill/`：知识生成方法和模板。
- `schemas/`：机器可读结构约束。
- `examples/`：教学样例，不是 live knowledge。
- `docs/`：设计说明、执行文档和项目反思。
- `notes/`：未结构化想法。

## 默认输出位置

长期知识默认写入 Obsidian vault：

```text
/Users/shenkai/Library/Mobile Documents/iCloud~md~obsidian/Documents/knowledge base
```

当前 repo 主要用于维护方法、模板、schema、示例和项目说明。

## 写作约束

- 保留 frontmatter。
- 保留稳定 ID。
- 使用中文正文。
- 保留必要英文机器字段，例如 `id`、`type`、`status`、`relations`。
- 使用 `[[wiki links]]` 连接知识。
- AI 生成知识默认 `hypothesis`。
- 对已有知识的调整优先写 change proposal。

## 判断标准

好的贡献应该让知识更：

- 可追溯
- 可执行
- 可评估
- 可迁移
- 易被人类理解
- 易被 Agent 检索和引用
