---
id: claim-github-issue-info-sufficiency-before-classification
type: knowledge_claim
title: Issue 分类前应该先检查信息充分性
scope:
  level: domain
  domain: github_issue_triage
status: hypothesis
confidence: 0.72
evidence_strength: medium
transferability: domain
schema_version: 0.1
evidence:
  - raw-github-issue-information-sufficiency-source-notes
  - case-vscode-needs-more-info-loop
  - case-rust-needs-repro-and-duplicate-caution
relations:
  depends_on: []
  supports:
    - dp-github-issue-triage-information-sufficiency
    - playbook-github-issue-info-first-triage
    - eval-github-issue-info-request-usefulness
  conflicts_with: []
  generalizes:
    - claim-github-issue-missing-repro-needs-info
  specializes: []
  derived_from:
    - raw-github-issue-information-sufficiency-source-notes
created: 2026-05-01
updated: 2026-05-01
tags:
  - type/claim
  - status/hypothesis
  - domain/github-issue-triage
---

# Issue 分类前应该先检查信息充分性

## Claim

在 GitHub Issue 分诊中，Agent 或维护者应该先检查 issue 是否包含足够信息来支撑下一步决策，然后再最终确定类型标签、duplicate 状态、模块路由、优先级或关闭。

如果关键资料缺失，更安全的下一步是请求定向信息或复现证据，而不是做出更强分类。

## Applies When

- 新 issue 声称是 bug，但缺少复现步骤。
- expected behavior 和 actual behavior 缺失或不清楚。
- 版本、环境、平台、依赖或配置细节缺失。
- 需要日志、截图、stack trace 或错误输出来理解 issue。
- issue 还不能安全地路由到模块、维护者或团队。
- 怀疑是 duplicate，但根因证据较弱。

## Does Not Apply When

- issue 已包含最小复现、相关版本、环境细节和清晰的实际输出。
- stack trace 或日志明确匹配已知 issue。
- issue 是简单文档错别字，或类似的低上下文修复。
- issue 是 feature request，主要缺失信息是产品价值或范围，而不是复现。
- issue 看起来像安全漏洞，应该进入私有安全流程。
- 维护者拥有公开 issue 中没有的外部上下文。

## Agent Use

在提出最终标签或路由之前，Agent 应抽取并报告以下字段是否存在：

- issue type candidate
- problem description
- expected behavior
- actual behavior
- reproduction steps
- minimal reproduction link
- version
- environment
- logs, screenshots, stack trace, or error output
- related issues
- user impact

如果信息不足，Agent 应输出：

- `needs-info` 或 `needs-repro` 风格建议；如果已知项目实际标签词表，应使用项目词表
- 具体缺失字段
- 一段简洁回复草稿，只询问会改变下一步决策的信息
- confidence 和引用的知识 ID

Agent 应避免：

- 在证据不足时确认 issue 是 bug
- 只基于相似症状标记 duplicate
- 在受影响范围不清楚时分配模块归属
- 发送无视已有信息的泛化请求

## Human Explanation

信息充分性是一个分诊 gate。没有足够信息，维护者就无法可靠地分类、复现、路由、排序或关闭 issue。GitHub Docs、Kubernetes、VS Code、Rust 等项目的公开实践会用标签、模板和自动化，把信息收集与更强的分诊决策分开。

可迁移的知识不是某个具体标签名，而是这个决策模式：

```text
这个 issue 是否已经足够 actionable，可以支撑下一步决策？
```

## Examples

- [[case-vscode-needs-more-info-loop]]
- [[case-rust-needs-repro-and-duplicate-caution]]

## Counterexamples

- 一份崩溃报告没有复现步骤，但包含的 stack trace 精确匹配已确认的已知 bug。
- Feature request 不需要复现，但仍可能需要用户价值、范围、替代方案和设计约束。
- 安全报告不应该在公开 issue 评论中通过 needs-info 处理；如果需要，应进入私有披露流程。

## Evaluation

通过抽样 Agent 建议信息请求的 issue 来评估这条 claim：

- 维护者是否接受或保留该建议？
- 用户是否提供了有用的后续信息？
- 维护者的二次澄清评论是否减少？
- 过早 bug、duplicate 或模块标签是否减少？
- issue 是否从阻塞的信息状态进入 actionable 分诊？

## Evidence Strength

当前证据强度为 `medium`。

理由：

- 多个公开来源收敛到同一模式。
- 多个来源是官方或项目维护的分诊指南。
- 证据还没有基于抽样 issue 历史或可测量的维护者行为。

## Transferability

这条 claim 是领域级知识。

抽象决策可以迁移到 GitHub Issue 分诊场景中，但具体标签名、必填字段、超时策略和自动化命令都是项目特定的。

## Open Questions

- 通用 schema 中是否应该区分 `needs-info` 和 `needs-repro`？
- 系统应该如何表示项目特定标签词表？
- Agent 建议 duplicate closure 前需要达到什么证据阈值？
- 各项目的超时策略不同，应该如何存储？

## Change Log

- 2026-05-01: 基于公开分诊指南和 practice cases，作为 hypothesis 创建。
