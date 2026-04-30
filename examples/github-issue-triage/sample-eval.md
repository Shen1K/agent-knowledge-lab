---
id: eval-github-issue-needs-info-followup
type: eval_rule
title: Needs-info request usefulness
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
  - type/eval
  - domain/github-issue-triage
---

# Needs-info request usefulness

## What It Evaluates

Whether an agent's `needs-info` recommendation and reply draft help move an issue forward.

## Metric Or Signal

- Signal: user provides missing details after the reply.
- Measurement: percent of `needs-info` replies followed by useful additional information.
- Desired direction: higher is better.

## Evaluation Method

Sample issues where the agent proposed `needs-info`. Compare follow-up comments and maintainer actions.

## Good Examples

- User provides version, reproduction steps, and actual output after the agent's targeted request.

## Bad Examples

- User does not respond because the request was too broad or irrelevant.

## Limitations

Some users will not respond even when the request is good. This metric should be combined with maintainer acceptance and rewrite rate.

## Related Knowledge

- [[claim-github-issue-missing-repro-needs-info]]
