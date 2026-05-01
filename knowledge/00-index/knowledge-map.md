---
id: knowledge-map
type: index
title: Knowledge Map
schema_version: 0.1
---

# Knowledge Map

## Layers

```text
raw evidence
  -> case cards
  -> knowledge claims
  -> decision points
  -> rules
  -> playbooks
  -> evals
```

## Relation Types

- `depends_on`: this knowledge needs another knowledge object.
- `supports`: this knowledge supports another object.
- `conflicts_with`: this knowledge contradicts another object.
- `generalizes`: this is a broader version of another object.
- `specializes`: this is a narrower version of another object.
- `derived_from`: this came from specific evidence or cases.

## Domain Map

### GitHub Issue Triage

- Cases: `knowledge/02-cases/github-issue-triage`
- Claims: `knowledge/03-claims/github-issue-triage`
- Decision points: `knowledge/04-decision-points/github-issue-triage`
- Rules: `knowledge/05-rules/github-issue-triage`
- Playbooks: `knowledge/06-playbooks/github-issue-triage`
- Evals: `knowledge/07-evals/github-issue-triage`

First real knowledge slice:

- [[raw-github-issue-information-sufficiency-source-notes]]
- [[case-vscode-needs-more-info-loop]]
- [[case-rust-needs-repro-and-duplicate-caution]]
- [[claim-github-issue-info-sufficiency-before-classification]]
- [[dp-github-issue-triage-information-sufficiency]]
- [[playbook-github-issue-info-first-triage]]
- [[eval-github-issue-info-request-usefulness]]
