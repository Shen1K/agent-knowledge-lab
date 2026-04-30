---
id: playbook-github-issue-basic-triage
type: playbook
title: Basic GitHub Issue Triage
domain: github_issue_triage
status: hypothesis
schema_version: 0.1
relations:
  depends_on:
    - dp-github-issue-information-sufficiency
    - claim-github-issue-missing-repro-needs-info
  supports: []
  conflicts_with: []
  derived_from:
    - case-github-issue-missing-repro-example
created: 2026-04-30
updated: 2026-04-30
tags:
  - type/playbook
  - domain/github-issue-triage
---

# Basic GitHub Issue Triage

## Purpose

Help an agent perform a first-pass triage of a GitHub issue.

## When To Use

- A new issue is opened.
- A maintainer wants a draft classification and reply.

## When Not To Use

- The issue requires private project knowledge that is not present in the knowledge base.
- The agent would need to perform destructive actions.

## Steps

1. Read the title, body, labels, comments, and linked references.
2. Decide whether the issue has enough information for triage.
3. If information is missing, propose `needs-info` and a targeted reply.
4. If information is sufficient, classify the issue type.
5. Search for potential duplicates or related issues.
6. Output labels, reasoning, cited knowledge IDs, and a maintainer reply draft.

## Decision Points

- [[dp-github-issue-information-sufficiency]]

## Required Knowledge

- [[claim-github-issue-missing-repro-needs-info]]

## Outputs

- Proposed labels.
- Missing information list.
- Reply draft.
- Confidence.
- Cited knowledge IDs.

## Evaluation

Track maintainer acceptance, label changes, useful user follow-up, and issue resolution progress.

## Change Log

- 2026-04-30: Created as hypothesis.
