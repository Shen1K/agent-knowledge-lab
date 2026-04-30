---
id: claim-github-issue-missing-repro-needs-info
type: knowledge_claim
title: Missing reproduction details should trigger information request
scope:
  level: domain
  domain: github_issue_triage
status: hypothesis
confidence: 0.5
schema_version: 0.1
evidence:
  - case-github-issue-missing-repro-example
relations:
  depends_on: []
  supports:
    - dp-github-issue-information-sufficiency
  conflicts_with: []
  generalizes:
    - claim-information-insufficiency-ask-first
  specializes: []
  derived_from:
    - case-github-issue-missing-repro-example
created: 2026-04-30
updated: 2026-04-30
tags:
  - type/claim
  - status/hypothesis
  - domain/github-issue-triage
---

# Missing reproduction details should trigger information request

## Claim

When an issue claims a bug but lacks reproduction steps, version information, and actual output, maintainers usually should request more information before treating it as a confirmed bug.

## Applies When

- The issue is about a suspected bug.
- The issue lacks reproduction steps.
- The issue lacks version or environment information.
- The issue lacks actual output or error details.

## Does Not Apply When

- A stack trace clearly points to a known bug.
- The issue links to a minimal reproduction repository.
- The maintainer already has enough external context.

## Agent Use

If these missing fields are detected, the agent should propose a `needs-info` label and draft a concise request for reproduction details.

## Human Explanation

Maintainers need enough information to reproduce, localize, and assign the problem. Without that, directly classifying the issue as a bug may waste review time.

## Examples

- [[case-github-issue-missing-repro-example]]

## Counterexamples

- A crash report with a precise stack trace matching an existing known issue.

## Evaluation

Check whether applying this claim increases useful user follow-up and reduces maintainer clarification comments.

## Open Questions

- Which missing fields are mandatory for different project types?

## Change Log

- 2026-04-30: Created as hypothesis.
