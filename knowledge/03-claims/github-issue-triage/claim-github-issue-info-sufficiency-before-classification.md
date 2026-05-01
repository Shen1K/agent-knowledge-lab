---
id: claim-github-issue-info-sufficiency-before-classification
type: knowledge_claim
title: Information sufficiency should be checked before issue classification
scope:
  level: domain
  domain: github_issue_triage
status: hypothesis
confidence: 0.72
evidence_strength: medium
transferability: domain
schema_version: 0.1
evidence:
  - raw-github-issue-information-sufficiency-source-notes
  - case-vscode-needs-more-info-loop
  - case-rust-needs-repro-and-duplicate-caution
relations:
  depends_on: []
  supports:
    - dp-github-issue-triage-information-sufficiency
    - playbook-github-issue-info-first-triage
    - eval-github-issue-info-request-usefulness
  conflicts_with: []
  generalizes:
    - claim-github-issue-missing-repro-needs-info
  specializes: []
  derived_from:
    - raw-github-issue-information-sufficiency-source-notes
created: 2026-05-01
updated: 2026-05-01
tags:
  - type/claim
  - status/hypothesis
  - domain/github-issue-triage
---

# Information sufficiency should be checked before issue classification

## Claim

In GitHub Issue triage, the agent or maintainer should check whether the issue contains enough information to support the next decision before finalizing type labels, duplicate status, module routing, priority, or closure.

If essential information is missing, the safer next action is to request targeted information or reproduction evidence, rather than making a stronger classification.

## Applies When

- A new issue claims a bug but lacks reproduction steps.
- Expected behavior and actual behavior are missing or unclear.
- Version, environment, platform, dependency, or configuration details are missing.
- Logs, screenshots, stack traces, or error output are needed to understand the issue.
- The issue cannot yet be safely routed to a module, maintainer, or team.
- Duplicate status is suspected but root-cause evidence is weak.

## Does Not Apply When

- The issue includes a minimal reproduction, relevant versions, environment details, and clear actual output.
- A stack trace or log clearly matches a known issue.
- The issue is a simple documentation typo or similarly low-context fix.
- The issue is a feature request where the main missing information is product value or scope, not reproduction.
- The issue appears to be a security vulnerability and should move to a private security process.
- Maintainers have external context that is not present in the public issue.

## Agent Use

Before proposing final labels or routing, the agent should extract and report whether these fields are present:

- issue type candidate
- problem description
- expected behavior
- actual behavior
- reproduction steps
- minimal reproduction link
- version
- environment
- logs, screenshots, stack trace, or error output
- related issues
- user impact

If information is insufficient, the agent should output:

- a `needs-info` or `needs-repro` style recommendation, using the project's actual label vocabulary when known
- the specific missing fields
- a concise reply draft asking only for information that would change the next decision
- confidence and cited knowledge IDs

The agent should avoid:

- confirming the issue as a bug without enough evidence
- marking duplicate based only on similar symptoms
- assigning module ownership when the affected area is unclear
- sending a generic request that ignores what is already present

## Human Explanation

Information sufficiency is a triage gate. Without enough information, maintainers cannot reliably classify, reproduce, route, prioritize, or close an issue. Public project practices across GitHub Docs, Kubernetes, VS Code, Rust, and other projects use labels, templates, and automation to separate information gathering from stronger triage decisions.

The transferable knowledge is not a specific label name. The transferable knowledge is the decision pattern:

```text
is this issue actionable enough for the next decision?
```

## Examples

- [[case-vscode-needs-more-info-loop]]
- [[case-rust-needs-repro-and-duplicate-caution]]

## Counterexamples

- A crash report has no reproduction steps but includes a stack trace that precisely matches an already confirmed known bug.
- A feature request does not need reproduction, but it may still need user value, scope, alternatives, and design constraints.
- A security report should not be handled through public needs-info comments if private disclosure is required.

## Evaluation

Evaluate this claim by sampling issues where the agent recommends an information request:

- Did maintainers accept or keep the recommendation?
- Did the user provide useful follow-up information?
- Did maintainer second clarification comments decrease?
- Did premature bug, duplicate, or module labels decrease?
- Did issues move from blocked information state into actionable triage?

## Evidence Strength

Current evidence strength is `medium`.

Reasoning:

- Multiple public sources converge on the same pattern.
- Several sources are official or project-maintained triage guides.
- The evidence is not yet based on sampled issue histories or measured maintainer behavior.

## Transferability

This claim is domain-level.

The abstract decision is transferable across GitHub Issue triage contexts, but the concrete label names, required fields, timeout policies, and automation commands are project-specific.

## Open Questions

- Should `needs-info` and `needs-repro` be separate in the generic schema?
- How should the system represent project-specific label vocabulary?
- What evidence threshold should be required before an agent suggests duplicate closure?
- How should timeout policies be stored, given they vary by project?

## Change Log

- 2026-05-01: Created as a hypothesis from public triage guides and practice cases.
