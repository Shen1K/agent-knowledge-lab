# Roadmap

## Phase 1: Lightweight Skill

Goal: make the knowledge generation method explicit, usable, and easy to edit.

Deliverables:

- Skill instructions for transforming raw materials into knowledge.
- Markdown templates for cases, claims, decision points, playbooks, evals, and change proposals.
- Obsidian-compatible folder structure and links.
- GitHub Issue triage example.
- Basic JSON schemas for future validators.

Success criteria:

- A human can read the project and understand the method in 10 minutes.
- A model can follow the skill to create a case card and a knowledge claim.
- Every generated claim has scope, evidence, boundary, status, usage, and evaluation.

## Phase 2: Knowledge Agent

Goal: automate repeated knowledge work while keeping human review in control.

Potential capabilities:

- Ingest raw materials from files, GitHub, websites, or chat exports.
- Generate case cards from raw evidence.
- Propose knowledge claims and decision points.
- Detect conflicts, duplicates, missing evidence, and outdated knowledge.
- Produce change proposals instead of directly rewriting validated knowledge.
- Track which knowledge was used by an agent and how the result performed.

Guardrails:

- AI-generated knowledge defaults to `status: hypothesis`.
- Validated knowledge requires human approval or clear evaluation evidence.
- Every update must preserve provenance and change history.

## Phase 3: Knowledge Service

Goal: turn the system into collaborative infrastructure.

Potential capabilities:

- Web UI for browsing, reviewing, and editing knowledge.
- Knowledge graph and relation explorer.
- Eval dashboard.
- Review workflow and permissions.
- Multi-domain and multi-agent knowledge spaces.
- API for agents to retrieve, cite, and update knowledge proposals.

## Open Questions

- What is the right minimum schema for a knowledge claim?
- How should feedback be attributed to specific knowledge units?
- How should conflicts be resolved across general, domain, project, and tool layers?
- When should a hypothesis be upgraded to validated knowledge?
- What should remain Markdown, and what should move into a database or graph?
