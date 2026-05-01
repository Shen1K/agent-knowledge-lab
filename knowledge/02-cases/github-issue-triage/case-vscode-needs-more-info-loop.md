---
id: case-vscode-needs-more-info-loop
type: case_card
title: VS Code uses needs more info as a blocking triage state
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

# VS Code uses needs more info as a blocking triage state

## Summary

VS Code's triage practice treats missing information as a state that can block normal classification. When an issue lacks enough information to understand or act on it, maintainers or automation can ask for more information and wait before continuing.

## Activity Reconstruction

- Actor: maintainer or triage automation.
- Goal: determine whether an issue can be understood, classified, and routed.
- Object: newly opened or reviewed GitHub issue.
- Context: high-volume open source issue tracker.
- Constraints: maintainers have limited time and cannot infer missing reproduction details.
- Judgment: whether the issue contains enough information to understand the problem.
- Action: apply a needs-more-info style state and request targeted information.
- Tool: GitHub label, comment, and triage automation commands.
- Result: user may provide information; otherwise the issue can remain blocked or be closed after a wait period.
- Evaluation signal: whether the user provides useful follow-up and whether maintainers can continue triage.

## Important Details

- The state is not merely descriptive. It changes the issue workflow because further classification may be blocked.
- The request should be targeted to the missing information, not a generic demand.
- Automation can help apply labels and follow up, but the underlying decision is still about information sufficiency.

## What This Case Might Teach

- Possible pattern: information sufficiency should be checked before type labels are finalized.
- Possible exception: if a stack trace or linked reproduction already provides enough detail, the issue may skip this state.
- Open question: how long should a project wait before closing stale information requests?

## Evidence

- [[raw-github-issue-information-sufficiency-source-notes]]
