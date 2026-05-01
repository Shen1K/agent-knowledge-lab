---
id: eval-github-issue-info-request-usefulness
type: eval_rule
title: Usefulness of information request in issue triage
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
  - type/eval
  - domain/github-issue-triage
---

# Usefulness of information request in issue triage

## What It Evaluates

Whether an agent's recommendation to request more information helps move an issue toward actionable triage.

## Metric Or Signal

- Signal: maintainer accepts the recommendation.
- Measurement: percentage of agent `needs-info` or `needs-repro` recommendations kept by maintainers.
- Desired direction: higher is better.

- Signal: user provides useful follow-up.
- Measurement: percentage of information requests followed by missing details that unblock the next triage step.
- Desired direction: higher is better.

- Signal: repeated clarification decreases.
- Measurement: number of additional maintainer clarification comments after the agent's draft.
- Desired direction: lower is better.

## Evaluation Method

Sample issues triaged by the agent and compare:

1. Agent recommendation.
2. Maintainer action.
3. User follow-up.
4. Final issue path.
5. Whether the cited knowledge was useful or misleading.

## Good Examples

- The agent asks for version, reproduction steps, and actual output; the user provides them; the issue can then be classified and routed.
- The agent avoids duplicate closure because evidence is weak; a maintainer later confirms the root cause differs.

## Bad Examples

- The agent sends a generic template asking for information already present.
- The agent asks for reproduction on a feature request where reproduction is irrelevant.
- The agent marks a likely duplicate based only on similar symptoms.

## Limitations

Some users will not respond even to good requests. This eval should not be used alone. It should be combined with maintainer acceptance, rewrite rate, and later issue progression.

## Related Knowledge

- [[claim-github-issue-info-sufficiency-before-classification]]
- [[dp-github-issue-triage-information-sufficiency]]
- [[playbook-github-issue-info-first-triage]]
