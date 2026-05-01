---
id: change-github-issue-triage-use-case-design-feedback
type: change_proposal
title: Design feedback from first GitHub Issue triage use case
domain: agent_knowledge_lab
status: proposed
schema_version: 0.1
target:
  - skill/SKILL.md
  - skill/templates/knowledge-claim.md
  - skill/templates/source-notes.md
  - schemas/knowledge-claim.schema.json
evidence:
  - docs/executions/2026-05-01-github-issue-triage-knowledge.md
created: 2026-05-01
updated: 2026-05-01
tags:
  - type/change-proposal
  - domain/agent-knowledge-lab
---

# Design feedback from first GitHub Issue triage use case

## Proposed Change

Add explicit support for source notes, evidence strength, transferability, and example-vs-real-knowledge namespace separation.

## Reason

The GitHub Issue triage use case showed that public sources have different evidence quality. Official docs, project guides, handbooks, sampled issues, and measured feedback should not be treated as equal.

It also showed that examples and real knowledge can accidentally reuse IDs, creating future retrieval and graph ambiguity.

## Evidence

- [[2026-05-01-github-issue-triage-knowledge]]
- [[raw-github-issue-information-sufficiency-source-notes]]

## Impact

- Agent behavior: agents can reason about evidence strength and transferability before applying a claim.
- Human understanding: readers can see whether a claim is public-source-derived, issue-sample-derived, or validated.
- Migration or compatibility: schemas need optional or required fields for evidence strength and transferability.

## Risks

- More metadata can make lightweight authoring feel heavier.
- Evidence strength may create false precision if not explained.
- Transferability categories may need refinement.

## Review Decision

- Accepted: partially implemented during the use case for source notes and knowledge claims.
- Rejected:
- Needs more evidence: namespace strategy for examples and real knowledge.

## Change Log

- 2026-05-01: Proposed from first real use case.
