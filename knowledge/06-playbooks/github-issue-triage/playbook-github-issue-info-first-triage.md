---
id: playbook-github-issue-info-first-triage
type: playbook
title: Information-first GitHub Issue triage
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

# Information-first GitHub Issue triage

## Purpose

Help an agent perform first-pass GitHub Issue triage without over-classifying issues that lack enough information.

## When To Use

- A new issue arrives.
- A maintainer wants a triage draft.
- The issue may be incomplete, ambiguous, or hard to reproduce.

## When Not To Use

- The issue is a private security report.
- The project has a stronger project-specific playbook that overrides this generic one.
- The agent is being asked to make a final maintainer decision without human review.

## Steps

1. Read the title, body, existing labels, comments, and links.
2. Identify the next triage decision the agent wants to make.
3. Run [[dp-github-issue-triage-information-sufficiency]].
4. If information is insufficient, recommend `needs-info` or `needs-repro` using project vocabulary when known.
5. Draft a targeted reply asking only for missing information that would unblock the next decision.
6. If information is sufficient, continue to type classification, duplicate search, routing, or priority.
7. Output cited knowledge IDs and confidence.

## Decision Points

- [[dp-github-issue-triage-information-sufficiency]]

## Required Knowledge

- [[claim-github-issue-info-sufficiency-before-classification]]

## Outputs

- `actionability`: actionable / needs-info / needs-repro / security-path / unclear
- `missing_information`: list of missing fields that matter
- `recommended_labels`: project-specific labels when available
- `reply_draft`: targeted maintainer comment
- `next_step`: what should happen after information is received
- `knowledge_used`: knowledge IDs cited by the agent
- `confidence`: low / medium / high

## Evaluation

Use [[eval-github-issue-info-request-usefulness]] and maintainer acceptance signals.

## Change Log

- 2026-05-01: Created as first real playbook hypothesis for the use case.
