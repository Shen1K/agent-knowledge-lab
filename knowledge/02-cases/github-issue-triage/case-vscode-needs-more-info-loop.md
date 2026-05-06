---
id: case-vscode-needs-more-info-loop
type: case_card
title: VS Code 把 needs more info 当作阻塞分诊状态
domain: github_issue_triage
schema_version: 0.1
source:
  - raw-github-issue-information-sufficiency-source-notes
status: draft
created: 2026-05-01
updated: 2026-05-01
relations:
  derived_from:
    - raw-github-issue-information-sufficiency-source-notes
  supports:
    - claim-github-issue-info-sufficiency-before-classification
  conflicts_with: []
tags:
  - type/case
  - domain/github-issue-triage
---

# VS Code 把 needs more info 当作阻塞分诊状态

## Summary

VS Code 的分诊实践把缺失信息视为一种会阻塞正常分类的状态。当一个 issue 缺少理解或处理所需的信息时，维护者或自动化流程可以要求补充信息，并在继续处理前等待。

## Activity Reconstruction

- Actor: 维护者或分诊自动化。
- Goal: 判断一个 issue 是否能被理解、分类和路由。
- Object: 新打开或正在审阅的 GitHub issue。
- Context: 高流量开源 issue tracker。
- Constraints: 维护者时间有限，不能靠猜测补全缺失的复现细节。
- Judgment: issue 是否包含足够信息来理解问题。
- Action: 应用 needs-more-info 类型状态，并请求定向信息。
- Tool: GitHub 标签、评论和分诊自动化命令。
- Result: 用户可能补充信息；否则 issue 会保持阻塞，或在等待期后被关闭。
- Evaluation signal: 用户是否提供有用补充，以及维护者是否能继续分诊。

## Important Details

- 这个状态不只是描述性的。它会改变 issue 工作流，因为后续分类可能被阻塞。
- 请求应该针对缺失信息，而不是泛泛要求。
- 自动化可以帮助加标签和跟进，但底层决策仍然是信息是否充分。

## What This Case Might Teach

- 可能的模式：在最终确定类型标签前，应该先检查信息充分性。
- 可能的例外：如果 stack trace 或链接复现已经提供足够细节，issue 可以跳过这个状态。
- 开放问题：项目应该等待多久后关闭过期的信息请求？

## Evidence

- [[raw-github-issue-information-sufficiency-source-notes]]
