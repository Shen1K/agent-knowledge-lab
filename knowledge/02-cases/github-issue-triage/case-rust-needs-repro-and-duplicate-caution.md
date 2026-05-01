---
id: case-rust-needs-repro-and-duplicate-caution
type: case_card
title: Rust separates needs-repro from duplicate confidence
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

# Rust separates needs-repro from duplicate confidence

## Summary

Rust's triage guidance distinguishes issues that need reproduction from issues that can be confidently linked to existing root causes. It also warns that duplicate classification requires care, because similar symptoms may not imply the same underlying bug.

## Activity Reconstruction

- Actor: Rust triager or maintainer.
- Goal: make an issue actionable without falsely closing or merging distinct problems.
- Object: compiler issue, regression report, ICE report, or possible duplicate.
- Context: technically complex project where similar error messages can have different causes.
- Constraints: incomplete reproduction and misleading symptom similarity can cause wrong closure.
- Judgment: whether enough reproduction or root-cause evidence exists.
- Action: request reproduction when needed; avoid overconfident duplicate closure without sufficient evidence.
- Tool: GitHub labels such as needs-info or needs-repro, comments, and issue search.
- Result: the issue either becomes actionable or remains blocked until more evidence exists.
- Evaluation signal: whether later maintainer action confirms the classification or reverses it.

## Important Details

- Reproduction is a special form of information sufficiency for bug reports.
- Duplicate judgment is downstream from evidence quality.
- Similar output is not enough if the root cause is uncertain.

## What This Case Might Teach

- Possible pattern: `needs-repro` and `needs-info` should be separate concepts when the project needs that precision.
- Possible exception: a known stack trace or minimized test case can make duplicate matching safer.
- Open question: what evidence threshold should an agent use before suggesting duplicate closure?

## Evidence

- [[raw-github-issue-information-sufficiency-source-notes]]
