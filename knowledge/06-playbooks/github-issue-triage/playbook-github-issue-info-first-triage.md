---
id: playbook-github-issue-info-first-triage
type: playbook
title: 信息先行的 GitHub Issue 分诊
domain: github_issue_triage
status: hypothesis
schema_version: 0.1
relations:
  depends_on:
    - dp-github-issue-triage-information-sufficiency
    - claim-github-issue-info-sufficiency-before-classification
  supports: []
  conflicts_with: []
  derived_from:
    - raw-github-issue-information-sufficiency-source-notes
created: 2026-05-01
updated: 2026-05-01
tags:
  - type/playbook
  - domain/github-issue-triage
---

# 信息先行的 GitHub Issue 分诊

## Purpose

帮助 Agent 执行第一轮 GitHub Issue 分诊，同时避免对信息不足的 issue 过度分类。

## When To Use

- 有新 issue 进入。
- 维护者想要一份分诊草稿。
- issue 可能不完整、模糊或难以复现。

## When Not To Use

- issue 是私有安全报告。
- 项目已有更强的项目特定 playbook，且会覆盖这份通用 playbook。
- Agent 被要求在没有人类评审的情况下做最终维护者决策。

## Steps

1. 阅读标题、正文、已有标签、评论和链接。
2. 识别 Agent 想要做出的下一步分诊决策。
3. 运行 [[dp-github-issue-triage-information-sufficiency]]。
4. 如果信息不足，使用已知项目词表推荐 `needs-info` 或 `needs-repro`。
5. 起草定向回复，只询问能解锁下一步决策的缺失信息。
6. 如果信息充分，继续做类型分类、duplicate 搜索、路由或优先级判断。
7. 输出引用的知识 ID 和 confidence。

## Decision Points

- [[dp-github-issue-triage-information-sufficiency]]

## Required Knowledge

- [[claim-github-issue-info-sufficiency-before-classification]]

## Outputs

- `actionability`: actionable / needs-info / needs-repro / security-path / unclear
- `missing_information`: 重要缺失字段列表
- `recommended_labels`: 已知项目特定标签
- `reply_draft`: 定向维护者评论
- `next_step`: 信息收到后应该发生什么
- `knowledge_used`: Agent 引用的知识 ID
- `confidence`: low / medium / high

## Evaluation

使用 [[eval-github-issue-info-request-usefulness]] 和维护者接受信号评估。

## Change Log

- 2026-05-01: 作为该 use case 的第一份真实 playbook hypothesis 创建。
