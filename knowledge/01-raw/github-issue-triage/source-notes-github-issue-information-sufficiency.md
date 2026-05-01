---
id: raw-github-issue-information-sufficiency-source-notes
type: raw_source_notes
title: Source notes for GitHub issue information sufficiency
domain: github_issue_triage
schema_version: 0.1
status: collected
created: 2026-05-01
updated: 2026-05-01
tags:
  - type/raw
  - domain/github-issue-triage
---

# Source notes for GitHub issue information sufficiency

These notes collect public sources used to generate the first real knowledge slice for GitHub Issue triage.

## Sources

### github-docs-ai-triage

- URL: https://docs.github.com/en/issues/tracking-your-work-with-issues/administering-issues/triaging-an-issue-with-ai
- Source type: official documentation.
- Observed pattern: GitHub frames AI issue triage around whether a new issue is actionable or needs more information.
- Relevance: supports treating information sufficiency as an early triage decision.

### github-docs-issue-forms

- URL: https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository
- Source type: official documentation.
- Observed pattern: issue forms encourage contributors to provide structured information through specific fields.
- Relevance: supports the idea that issue quality can be improved before triage through structured intake.

### kubernetes-issue-triage

- URL: https://www.kubernetes.dev/docs/guide/issue-triage/
- Source type: project maintainer guide.
- Observed pattern: Kubernetes uses `triage/needs-information` when more information is needed before work can continue. Bugs should be validated by attempting reproduction.
- Relevance: supports separating information gathering from later bug validation, duplicate search, priority, and SIG routing.

### vscode-issues-triaging

- URL: https://github.com/microsoft/vscode/wiki/Issues-Triaging
- Source type: project maintainer guide.
- Observed pattern: VS Code uses `needs more info` when information needed to understand the issue is missing. The label can block type assignment and may lead to closure after a fixed wait.
- Relevance: strongly supports the claim that information sufficiency precedes type classification.

### vscode-automated-issue-triaging

- URL: https://github.com/microsoft/vscode/wiki/Automated-Issue-Triaging
- Source type: project automation guide.
- Observed pattern: VS Code automates commands that add `needs more info`, request specific logs or recordings, and close stale information requests.
- Relevance: supports future Knowledge Agent behavior: targeted requests, labels, comments, and follow-up monitoring.

### rust-forge-issue-triaging

- URL: https://rust-lang.github.io/rust-forge/release/issue-triaging.html
- Source type: project maintainer guide.
- Observed pattern: Rust initial triage checks whether an issue is actionable, whether it needs reproduction, whether it lacks information, and whether duplicate evidence is strong enough.
- Relevance: supports distinguishing `needs-info` from `needs-repro`, and warns against overconfident duplicate closure.

### chatwoot-issue-triage

- URL: https://chatwoot.help/hc/handbook/en/categories/processes
- Source type: company/project handbook.
- Observed pattern: Chatwoot uses `need-more-info` for issues that lack enough information to start work. Bug reports without screenshots or logs should be moved to `need-more-info`.
- Relevance: supports the operational rule that missing diagnostic artifacts should block development pickup.

### stackblitz-bug-reproductions

- URL: https://developer.stackblitz.com/guides/integration/bug-reproductions
- Source type: product/developer guide.
- Observed pattern: minimal reproductions are treated as highly useful for bug reports.
- Relevance: supports the reproduction-specific part of information sufficiency.

## Evidence Strength Notes

- Strongest sources for this claim: GitHub Docs, Kubernetes, VS Code, Rust.
- Medium sources: Chatwoot and StackBlitz.
- Missing evidence: sampled real issue histories and maintainer acceptance data.

## Initial Interpretation

Information sufficiency appears to be a cross-project triage checkpoint. It is not identical across projects: VS Code uses `needs more info`; Kubernetes uses `triage/needs-information`; Rust separates `S-needs-info` and `S-needs-repro`; Chatwoot uses `need-more-info`.

The general pattern is transferable, but label names, timeouts, and required fields are project-specific.
