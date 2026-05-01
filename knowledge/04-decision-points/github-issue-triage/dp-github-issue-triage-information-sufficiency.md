---
id: dp-github-issue-triage-information-sufficiency
type: decision_point
title: Is the issue actionable enough for the next triage decision?
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

# Is the issue actionable enough for the next triage decision?

## Decision Question

Does the issue contain enough information to make the next intended triage decision safely?

This question should be answered before finalizing stronger decisions such as issue type, duplicate status, module ownership, priority, assignment, or closure.

## Why This Decision Matters

Many triage mistakes are downstream of missing information. An agent may appear productive by assigning labels quickly, but if the issue is not actionable, those labels create false confidence and maintainer rework.

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

- Actionable: continue with type classification, duplicate search, routing, or priority.
- Needs info: request missing context needed to understand the issue.
- Needs reproduction: request steps, minimal reproduction, or failing example.
- Needs private path: security or sensitive information should not be handled in public issue comments.
- Unclear: ask a narrow clarifying question before stronger classification.

## Agent Behavior

The agent should:

1. Identify the next decision it is trying to support.
2. List present and missing information.
3. Decide whether missing information blocks the next decision.
4. Recommend the smallest useful information request.
5. Cite the knowledge IDs used.

The agent should not treat all missing fields as blockers. A missing field matters when it would change or enable the next decision.

## Human Review Notes

Review whether the agent's information request is targeted and necessary. A broad template can create user friction; a narrow request can move the issue forward.

## Evaluation

Measure downstream usefulness:

- maintainer acceptance of the information request
- useful user follow-up rate
- reduction in repeated clarification
- reduction in premature classification or duplicate closure
- transition from blocked state to actionable state
