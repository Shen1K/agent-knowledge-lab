# Agent Knowledge Lab

From raw materials to usable agent knowledge.

Agent Knowledge Lab is an open project for designing a knowledge system that both humans and AI agents can use. It starts as a lightweight skill: a repeatable method for turning documents, data, images, issues, chats, and execution traces into structured knowledge. If the method proves useful, it can grow into a heavier knowledge agent, and later into a collaborative service.

## Why

Most agent projects talk about models, prompts, tools, and memory. The harder problem is knowledge: how an agent learns how humans actually do work, how that knowledge is recorded, and how it improves through feedback.

This project assumes:

- Knowledge is not a pile of documents.
- AI-generated knowledge is a hypothesis until verified.
- Useful agent knowledge must be understandable by humans.
- Knowledge should preserve evidence, boundaries, status, relationships, and change history.
- The first system should be light enough to edit, but structured enough to migrate later.

## Core Idea

In a new domain, do not jump from raw materials directly to SOPs. First reconstruct human activity.

```text
raw materials
  -> activity reconstruction
  -> case cards
  -> knowledge claims
  -> decision points
  -> rules and playbooks
  -> evals and feedback
  -> updated knowledge
```

The smallest unit is a **Knowledge Claim**: a scoped, evidenced, usable, and falsifiable claim that can guide human or agent action.

## Project Shape

```text
skill/        Lightweight skill and templates for knowledge generation.
knowledge/    Obsidian-friendly knowledge workspace.
examples/     Worked examples, starting with GitHub Issue triage.
schemas/      Machine-readable schemas for future tooling.
docs/         Philosophy, design notes, migration path, and self-audit.
notes/        Project thinking notes from ongoing discussions.
```

## Quick Start

1. Open this folder in Obsidian, VS Code, or any Markdown editor.
2. Read [PRINCIPLES.md](PRINCIPLES.md).
3. Read [skill/SKILL.md](skill/SKILL.md).
4. Copy templates from [skill/templates](skill/templates) into the matching `knowledge/` folder.
5. Try the example in [examples/github-issue-triage](examples/github-issue-triage).

## Knowledge Types

- **Raw Material**: Original evidence. Keep it as unchanged as possible.
- **Case Card**: A reconstruction of one human activity episode.
- **Knowledge Claim**: The smallest usable and testable knowledge unit.
- **Decision Point**: A task moment where judgment is required.
- **Rule**: A composed instruction built from one or more claims.
- **Playbook**: A task-level operating guide.
- **Eval Rule**: A way to judge whether knowledge or output works.
- **Change Proposal**: A suggested knowledge update based on evidence or feedback.

## Relationship Model

Knowledge relationships are recorded twice:

- In YAML frontmatter for agents and tools.
- In `[[wiki links]]` for humans using Obsidian.

The first version keeps relation types intentionally small:

```text
depends_on
supports
conflicts_with
generalizes
specializes
derived_from
```

## Current Example

The first validation domain is **GitHub Issue triage**.

This domain is useful because it has cheap continuous input, visible human behavior, and relatively clear feedback signals: labels, maintainer replies, issue closure, duplicate links, and user follow-up.

## Roadmap

See [ROADMAP.md](ROADMAP.md).

Short version:

1. **Skill**: lightweight templates and method.
2. **Knowledge Agent**: proposes case cards, claims, conflicts, and updates.
3. **Service**: collaborative UI, review flow, graph, eval dashboard, and agent API.

## Contributing

This project is designed for discussion and iteration. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).
