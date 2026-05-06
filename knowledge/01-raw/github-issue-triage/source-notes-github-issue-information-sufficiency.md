---
id: raw-github-issue-information-sufficiency-source-notes
type: raw_source_notes
title: GitHub issue 信息充分性的来源笔记
aliases:
  - raw-github-issue-information-sufficiency-source-notes
domain: github_issue_triage
schema_version: 0.1
status: collected
created: 2026-05-01
updated: 2026-05-01
tags:
  - type/raw
  - domain/github-issue-triage
---

# GitHub issue 信息充分性的来源笔记

这些笔记收集了用于生成第一组真实 GitHub Issue 分诊知识切片的公开来源。

## Sources

### github-docs-ai-triage

- URL: https://docs.github.com/en/issues/tracking-your-work-with-issues/administering-issues/triaging-an-issue-with-ai
- Source type: official documentation.
- Observed pattern: GitHub 把 AI issue 分诊放在“新 issue 是否 actionable，或是否需要更多信息”的框架下。
- Relevance: 支持把信息充分性视为早期分诊决策。

### github-docs-issue-forms

- URL: https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository
- Source type: official documentation.
- Observed pattern: issue forms 通过具体字段鼓励贡献者提供结构化信息。
- Relevance: 支持“在分诊前通过结构化入口提升 issue 质量”的观点。

### kubernetes-issue-triage

- URL: https://www.kubernetes.dev/docs/guide/issue-triage/
- Source type: project maintainer guide.
- Observed pattern: Kubernetes 在继续处理前需要更多信息时使用 `triage/needs-information`。Bug 应该通过尝试复现来验证。
- Relevance: 支持把信息收集与后续 bug 验证、重复 issue 搜索、优先级判断和 SIG 路由分开。

### vscode-issues-triaging

- URL: https://github.com/microsoft/vscode/wiki/Issues-Triaging
- Source type: project maintainer guide.
- Observed pattern: VS Code 在缺少理解 issue 所需的信息时使用 `needs more info`。该标签可以阻塞类型分配，并可能在固定等待期后导致关闭。
- Relevance: 强力支持“信息充分性先于类型分类”的 claim。

### vscode-automated-issue-triaging

- URL: https://github.com/microsoft/vscode/wiki/Automated-Issue-Triaging
- Source type: project automation guide.
- Observed pattern: VS Code 自动化命令可以添加 `needs more info`、请求特定日志或录屏，并关闭过期的信息请求。
- Relevance: 支持未来 Knowledge Agent 的行为：定向请求、加标签、评论和后续监控。

### rust-forge-issue-triaging

- URL: https://rust-lang.github.io/rust-forge/release/issue-triaging.html
- Source type: project maintainer guide.
- Observed pattern: Rust 初始分诊会检查 issue 是否 actionable、是否需要复现、是否缺少信息，以及 duplicate 证据是否足够强。
- Relevance: 支持区分 `needs-info` 和 `needs-repro`，并提醒不要过度自信地关闭为 duplicate。

### chatwoot-issue-triage

- URL: https://chatwoot.help/hc/handbook/en/categories/processes
- Source type: company/project handbook.
- Observed pattern: Chatwoot 对缺少足够信息、无法开始工作的 issue 使用 `need-more-info`。没有截图或日志的 bug report 应移动到 `need-more-info`。
- Relevance: 支持“缺少诊断材料应该阻塞开发接手”的操作规则。

### stackblitz-bug-reproductions

- URL: https://developer.stackblitz.com/guides/integration/bug-reproductions
- Source type: product/developer guide.
- Observed pattern: 最小复现被视为 bug report 中非常有用的信息。
- Relevance: 支持信息充分性中与复现相关的部分。

## Evidence Strength Notes

- 这条 claim 最强的来源：GitHub Docs、Kubernetes、VS Code、Rust。
- 中等来源：Chatwoot 和 StackBlitz。
- 缺失证据：抽样真实 issue 历史和维护者接受数据。

## Initial Interpretation

信息充分性看起来是跨项目的分诊检查点。不同项目表达并不完全相同：VS Code 使用 `needs more info`；Kubernetes 使用 `triage/needs-information`；Rust 区分 `S-needs-info` 和 `S-needs-repro`；Chatwoot 使用 `need-more-info`。

通用模式可以迁移，但标签名称、等待时间和必填字段是项目特定的。
