---
id: case-github-issue-missing-repro-example
type: case_card
title: User reports a bug without reproduction details
domain: github_issue_triage
schema_version: 0.1
source:
  - raw-example-github-issue
status: draft
created: 2026-04-30
updated: 2026-04-30
relations:
  derived_from:
    - raw-example-github-issue
  supports:
    - claim-github-issue-missing-repro-needs-info
  conflicts_with: []
tags:
  - type/case
  - domain/github-issue-triage
---

# User reports a bug without reproduction details

## Summary

A user opens an issue saying a command failed, but does not include version, environment, reproduction steps, expected output, or actual output.

## Activity Reconstruction

- Actor: issue author.
- Goal: get help with a failing command.
- Object: a suspected bug.
- Context: open source GitHub repository.
- Constraints: maintainers cannot reproduce the failure.
- Judgment: whether the issue has enough information to triage.
- Action: maintainer asks for missing details before labeling it as a confirmed bug.
- Tool: GitHub comment and `needs-info` label.
- Result: user may provide details, or the issue may become stale.
- Evaluation signal: whether the user provides useful reproduction information.

## What This Case Might Teach

- Possible pattern: missing reproduction details often blocks triage.
- Possible exception: a stack trace may be enough if it points to a known failure.
- Open question: how many missing fields should trigger `needs-info`?

## Evidence

- [[raw-example-github-issue]]
