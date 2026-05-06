---
id: case-rust-needs-repro-and-duplicate-caution
type: case_card
title: Rust 区分 needs-repro 与 duplicate 置信度
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

# Rust 区分 needs-repro 与 duplicate 置信度

## Summary

Rust 的分诊指南区分“需要复现”的 issue 和“可以有把握关联到已有根因”的 issue。它也提醒 duplicate 分类需要谨慎，因为相似症状不一定意味着相同底层 bug。

## Activity Reconstruction

- Actor: Rust 分诊者或维护者。
- Goal: 让 issue 变得 actionable，同时避免错误关闭或合并不同问题。
- Object: 编译器 issue、回归报告、ICE 报告或可能重复的问题。
- Context: 技术复杂的项目，相似错误信息可能有不同原因。
- Constraints: 复现不完整和症状相似可能导致错误关闭。
- Judgment: 是否有足够复现或根因证据。
- Action: 在需要时请求复现；证据不足时避免过度自信地关闭为 duplicate。
- Tool: GitHub 标签，如 needs-info 或 needs-repro、评论和 issue 搜索。
- Result: issue 要么变得 actionable，要么在获得更多证据前保持阻塞。
- Evaluation signal: 后续维护者行动是否确认或推翻该分类。

## Important Details

- 对 bug report 来说，复现是信息充分性的一种特殊形式。
- Duplicate 判断位于证据质量之后。
- 如果根因不确定，相似输出本身并不够。

## What This Case Might Teach

- 可能的模式：当项目需要这种精度时，`needs-repro` 和 `needs-info` 应该是两个不同概念。
- 可能的例外：已知 stack trace 或最小化测试用例可以让 duplicate 匹配更安全。
- 开放问题：Agent 在建议 duplicate closure 前应该采用什么证据阈值？

## Evidence

- [[raw-github-issue-information-sufficiency-source-notes]]
