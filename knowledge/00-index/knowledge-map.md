---
id: knowledge-map
type: index
title: 知识地图
schema_version: 0.1
---

# 知识地图

## 层次

```text
原始证据
  -> 案例卡
  -> 知识主张
  -> 决策点
  -> 规则
  -> playbook
  -> eval
```

## 关系类型

- `depends_on`：这份知识需要另一个知识对象。
- `supports`：这份知识支持另一个对象。
- `conflicts_with`：这份知识与另一个对象冲突。
- `generalizes`：这是另一个对象的更通用版本。
- `specializes`：这是另一个对象的更具体版本。
- `derived_from`：这份知识来自特定证据或案例。

## 领域地图

### GitHub Issue 分诊

- 专题入口：[[github-issue-triage]]
- Cases: `knowledge/02-cases/github-issue-triage`
- Claims: `knowledge/03-claims/github-issue-triage`
- Decision points: `knowledge/04-decision-points/github-issue-triage`
- Rules: `knowledge/05-rules/github-issue-triage`
- Playbooks: `knowledge/06-playbooks/github-issue-triage`
- Evals: `knowledge/07-evals/github-issue-triage`

第一组真实知识切片：

- [[raw-github-issue-information-sufficiency-source-notes]]
- [[case-vscode-needs-more-info-loop]]
- [[case-rust-needs-repro-and-duplicate-caution]]
- [[claim-github-issue-info-sufficiency-before-classification]]
- [[dp-github-issue-triage-information-sufficiency]]
- [[playbook-github-issue-info-first-triage]]
- [[eval-github-issue-info-request-usefulness]]
