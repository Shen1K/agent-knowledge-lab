---
id: dp-github-issue-triage-information-sufficiency
type: decision_point
title: Issue 是否足够 actionable，可以支撑下一步分诊决策？
domain: github_issue_triage
status: hypothesis
schema_version: 0.1
relations:
  depends_on:
    - claim-github-issue-info-sufficiency-before-classification
  supports:
    - playbook-github-issue-info-first-triage
  conflicts_with: []
  derived_from:
    - raw-github-issue-information-sufficiency-source-notes
created: 2026-05-01
updated: 2026-05-01
tags:
  - type/decision-point
  - domain/github-issue-triage
---

# Issue 是否足够 actionable，可以支撑下一步分诊决策？

## Decision Question

这个 issue 是否包含足够信息，可以安全地做出下一步预期分诊决策？

在最终确定更强决策之前，应该先回答这个问题，例如 issue 类型、duplicate 状态、模块归属、优先级、分配或关闭。

## Why This Decision Matters

许多分诊错误都源于信息缺失。Agent 可能通过快速分配标签显得很高效，但如果 issue 本身不可行动，这些标签会制造虚假的确定性，并给维护者带来返工。

## Inputs Needed

- Issue title.
- Issue body.
- Existing labels.
- Existing comments.
- Expected behavior.
- Actual behavior.
- Reproduction steps or minimal reproduction.
- Version and environment.
- Logs, screenshots, stack traces, or error output.
- Related issues or links.
- Project-specific issue template requirements.

## Relevant Claims

- [[claim-github-issue-info-sufficiency-before-classification]]

## Possible Outcomes

- Actionable: 继续做类型分类、duplicate 搜索、路由或优先级判断。
- Needs info: 请求理解 issue 所需的缺失上下文。
- Needs reproduction: 请求复现步骤、最小复现或失败示例。
- Needs private path: 安全或敏感信息不应在公开 issue 评论中处理。
- Unclear: 在更强分类前提出一个窄澄清问题。

## Agent Behavior

Agent 应该：

1. 识别自己试图支撑的下一步决策。
2. 列出已有信息和缺失信息。
3. 判断缺失信息是否阻塞下一步决策。
4. 推荐最小且有用的信息请求。
5. 引用使用过的知识 ID。

Agent 不应该把所有缺失字段都当成阻塞项。只有当某个缺失字段会改变或启用下一步决策时，它才重要。

## Human Review Notes

评审 Agent 的信息请求是否定向且必要。宽泛模板会增加用户摩擦；窄请求更可能推动 issue 前进。

## Evaluation

衡量下游有用性：

- 维护者是否接受信息请求
- 用户是否提供有用后续信息
- 重复澄清是否减少
- 过早分类或 duplicate closure 是否减少
- issue 是否从阻塞状态转为 actionable 状态
