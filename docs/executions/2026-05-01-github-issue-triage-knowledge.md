# GitHub Issue Triage Knowledge Use Case Execution

Date: 2026-05-01

## Purpose

Use Agent Knowledge Lab itself to build a real piece of domain knowledge for GitHub Issue triage.

This is not project documentation only. It is a reference use case that should test whether the current knowledge system can support real knowledge generation.

## Initial Thinking

The project currently has templates, principles, schemas, and a small example. That is still mostly a designed structure. This execution should put pressure on the structure by using public materials and real maintainer practices to produce actual knowledge artifacts.

The first useful knowledge should not be a complete triage SOP. It should focus on a prior decision that many later triage decisions depend on:

> Is the issue information sufficient to make the next triage decision?

## Initial Assumptions

- Public maintainer guides are acceptable first-pass evidence, but weaker than sampled issue histories.
- AI-generated artifacts should remain `status: hypothesis`.
- The first artifact set should include raw source notes, at least one case card, one claim, one decision point, one playbook, and one eval.
- This use case should reveal design feedback for Agent Knowledge Lab itself.
- Completion means the repository contains a coherent knowledge slice, a recorded execution process, and a project-level feedback note.

## Initial Done Criteria

- Evidence sources are recorded with stable IDs and links.
- A real domain claim exists under `knowledge/03-claims/github-issue-triage`.
- The claim is connected to a decision point, playbook, eval, and source notes.
- The knowledge is human-readable in Obsidian and machine-readable through frontmatter.
- The execution records what changed in my assumptions.
- The project self-audit or roadmap records any design feedback discovered during this use case.

## Log

### 2026-05-01 12:55 - Start

I am beginning by writing this execution document before creating knowledge artifacts. This is intentional: the document should capture the live reasoning path, not a polished after-action summary.

Current hypothesis: the information-sufficiency decision is a better first knowledge target than generic issue labeling because it is upstream of bug/feature/duplicate/module routing decisions.

### 2026-05-01 13:05 - Source gathering

I searched public sources from GitHub Docs, Kubernetes, VS Code, Rust, Chatwoot, and StackBlitz.

Feedback from sources:

- The initial hypothesis became stronger. Multiple projects treat missing information as an early triage state.
- The label vocabulary is not universal: examples include `needs more info`, `triage/needs-information`, `S-needs-info`, `S-needs-repro`, and `need-more-info`.
- The transferable knowledge is not the label name. The transferable knowledge is the decision: determine whether the issue is actionable before making stronger classification or routing decisions.
- A hidden schema need appeared: evidence should record `source_type` and rough `evidence_strength`, because official docs, project handbooks, and sampled issue histories should not be treated as equal.

Action taken:

- Created raw source notes: `knowledge/01-raw/github-issue-triage/source-notes-github-issue-information-sufficiency.md`.

### 2026-05-01 13:15 - Case cards

I created two case cards from public project practices:

- `case-vscode-needs-more-info-loop`
- `case-rust-needs-repro-and-duplicate-caution`

Reasoning:

- VS Code is useful because it shows missing information as a workflow-blocking state.
- Rust is useful because it separates reproduction needs from duplicate confidence, which prevents the agent from over-collapsing different issues.

Adjustment:

- The original plan said "case cards" should reconstruct human activity episodes. Public maintainer guides are not single historical episodes, but they still describe repeated human activity patterns. This reveals a design question: should the project distinguish `case_card` from `practice_case`?

Current decision:

- Keep them as `case_card` for now, but record this as project feedback later.

### 2026-05-01 13:30 - Knowledge artifacts

I created the first real knowledge slice:

- Claim: `claim-github-issue-info-sufficiency-before-classification`
- Decision point: `dp-github-issue-triage-information-sufficiency`
- Playbook: `playbook-github-issue-info-first-triage`
- Eval: `eval-github-issue-info-request-usefulness`

Reasoning:

- The claim is the smallest falsifiable statement.
- The decision point is the task moment where the claim is used.
- The playbook is the actionable task wrapper.
- The eval describes how future feedback should judge whether the knowledge is useful.

Adjustment:

- I avoided reusing IDs from `examples/` because duplicate IDs would create graph and retrieval ambiguity. This reveals a project issue: examples and real knowledge need separate ID namespaces or an explicit example prefix.

Current confidence:

- Claim confidence remains `0.72`, not validated. Public guides are enough to form a strong hypothesis, but not enough to prove real-world performance.

### 2026-05-01 13:45 - Project feedback and adjustment

The use case exposed three project-level gaps:

1. There was no source-notes template, even though source normalization was necessary before writing claims.
2. The knowledge claim template did not explicitly record `evidence_strength`.
3. The knowledge claim template did not explicitly record `transferability`, even though the distinction between general, domain, project, and tool knowledge mattered immediately.

Adjustment made during execution:

- Added `skill/templates/source-notes.md`.
- Updated `skill/SKILL.md`.
- Updated `skill/templates/knowledge-claim.md`.
- Updated `schemas/knowledge-claim.schema.json`.
- Updated the new GitHub Issue triage claim with `evidence_strength: medium` and `transferability: domain`.
- Added a change proposal: `knowledge/08-changes/change-github-issue-triage-use-case-design-feedback.md`.

This is the first concrete proof that reference use cases should not only produce domain knowledge; they should also improve the knowledge system itself.

### 2026-05-01 14:00 - Consistency pass

I updated the teaching example claim to include `evidence_strength` and `transferability`, because schema changes should not leave examples behind.

I also updated the knowledge map so a human opening the Obsidian vault can find the first real knowledge slice without browsing folders manually.

Project self-audit now records three new risks:

- source evidence can be flattened
- examples and real knowledge can share IDs
- public practice guides are not the same as individual cases

This reinforces a design principle: reference use cases should create both domain artifacts and method feedback.

### 2026-05-01 14:10 - Validation

Checks performed:

- JSON schemas parse successfully.
- `evidence_strength` and `transferability` appear in the template, schema, real claim, and teaching example.
- The first real knowledge slice is listed in `knowledge/00-index/knowledge-map.md`.
- A simple ID scan did not reveal duplicate IDs among the newly created real knowledge artifacts.

Feedback:

- The repository still lacks a true Markdown/frontmatter validator. Manual checks and grep are enough for this first pass, but not enough once many contributors start adding knowledge.
- A future Knowledge Agent will need an automated validator for:
  - duplicate IDs
  - missing required frontmatter
  - broken `[[wiki links]]`
  - unsupported relation types
  - claims without evaluation sections
  - validated claims without stronger evidence

Updated done-condition assessment:

- Evidence sources recorded: yes.
- Real claim created: yes.
- Claim connected to decision point, playbook, eval, and source notes: yes.
- Human-readable and frontmatter-readable: yes.
- Execution reasoning recorded live: yes.
- Project-level design feedback recorded: yes.
- Remaining limitation: no sampled issue-history validation yet.
