---
id: dp-github-issue-information-sufficiency
type: decision_point
title: Is the issue information sufficient for triage?
domain: github_issue_triage
status: hypothesis
schema_version: 0.1
relations:
  depends_on:
    - claim-github-issue-missing-repro-needs-info
  supports:
    - playbook-github-issue-basic-triage
  conflicts_with: []
  derived_from:
    - case-github-issue-missing-repro-example
created: 2026-04-30
updated: 2026-04-30
tags:
  - type/decision-point
  - domain/github-issue-triage
---

# Is the issue information sufficient for triage?

## Decision Question

Does this issue contain enough information for a maintainer or agent to classify and route it?

## Why This Decision Matters

If the issue lacks essential information, later labels and routing decisions become unreliable.

## Inputs Needed

- Issue title.
- Issue body.
- Error output or logs.
- Version and environment.
- Reproduction steps.
- Expected and actual behavior.

## Relevant Claims

- [[claim-github-issue-missing-repro-needs-info]]

## Possible Outcomes

- Sufficient: continue classification.
- Insufficient: propose `needs-info`.
- Unclear: ask a narrow follow-up question.

## Agent Behavior

The agent should list which information is present and missing, then decide whether a targeted information request is needed.

## Human Review Notes

Review whether the agent asks for only useful missing details instead of sending a generic template.

## Evaluation

Measure whether the request leads to useful user follow-up and whether maintainers still need to ask clarification questions.
