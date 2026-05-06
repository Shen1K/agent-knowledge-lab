---
id: eval-github-issue-info-request-usefulness
type: eval_rule
title: Issue 分诊中信息请求的有用性
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
  - type/eval
  - domain/github-issue-triage
---

# Issue 分诊中信息请求的有用性

## What It Evaluates

评估 Agent 建议请求更多信息，是否能帮助 issue 进入 actionable 分诊。

## Metric Or Signal

- Signal: 维护者接受该建议。
- Measurement: Agent 提出的 `needs-info` 或 `needs-repro` 建议被维护者保留的比例。
- Desired direction: 越高越好。

- Signal: 用户提供有用后续信息。
- Measurement: 信息请求后，用户补充能解锁下一步分诊的缺失细节的比例。
- Desired direction: 越高越好。

- Signal: 重复澄清减少。
- Measurement: Agent 草稿之后，维护者额外澄清评论的数量。
- Desired direction: 越低越好。

## Evaluation Method

抽样由 Agent 分诊的 issue，并比较：

1. Agent recommendation.
2. Maintainer action.
3. User follow-up.
4. Final issue path.
5. 被引用的知识是否有用或误导。

## Good Examples

- Agent 请求版本、复现步骤和实际输出；用户提供这些信息；issue 随后可以被分类和路由。
- Agent 因证据较弱而避免 duplicate closure；维护者后来确认根因不同。

## Bad Examples

- Agent 发送泛化模板，要求已经存在的信息。
- Agent 在 feature request 中请求复现，而复现并不相关。
- Agent 只基于相似症状就标记可能 duplicate。

## Limitations

即使请求质量很好，有些用户也不会回复。这个 eval 不应单独使用，应该结合维护者接受度、重写率和后续 issue 进展一起看。

## Related Knowledge

- [[claim-github-issue-info-sufficiency-before-classification]]
- [[dp-github-issue-triage-information-sufficiency]]
- [[playbook-github-issue-info-first-triage]]
