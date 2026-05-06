# Obsidian 指南

这个项目被设计为可以直接作为 Obsidian vault 打开。

## 推荐入口

- `knowledge/00-index/home.md`
- `knowledge/00-index/knowledge-map.md`
- `examples/github-issue-triage/README.md`

## 链接如何工作

在人类阅读的内容中使用 Obsidian 风格的 wiki 链接：

```text
[[claim-github-issue-missing-repro-needs-info]]
```

在 YAML frontmatter 中记录机器可读的关系：

```yaml
relations:
  depends_on:
    - claim-github-issue-missing-repro-needs-info
```

两者都有用：

- Wiki 链接让知识更容易浏览。
- Frontmatter 让知识更容易被 Agent 和工具解析。

## 建议标签

```text
#type/case
#type/claim
#type/decision-point
#type/playbook
#type/eval
#status/hypothesis
#status/validated
#domain/github-issue-triage
```

## 人类阅读路径

1. 先读 playbook。
2. 打开它依赖的决策点。
3. 阅读这些决策背后的知识主张。
4. 查看示例和反例。
5. 审阅 eval 和变更历史。

这条路径刻意不同于 Agent 的检索路径。人类需要叙事和示例；Agent 需要有范围、有引用、有结构的知识。
