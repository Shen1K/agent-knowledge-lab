# Obsidian Guide

This project is designed to be opened directly as an Obsidian vault.

## Recommended Entry Points

- `knowledge/00-index/home.md`
- `knowledge/00-index/knowledge-map.md`
- `examples/github-issue-triage/README.md`

## How Links Work

Use Obsidian-style wiki links in human-facing content:

```text
[[claim-github-issue-missing-repro-needs-info]]
```

Use YAML frontmatter for machine-readable relationships:

```yaml
relations:
  depends_on:
    - claim-github-issue-missing-repro-needs-info
```

Both are useful:

- Wiki links make the knowledge easier to browse.
- Frontmatter makes the knowledge easier for agents and tools to parse.

## Suggested Tags

```text
#type/case
#type/claim
#type/decision-point
#type/playbook
#type/eval
#status/hypothesis
#status/validated
#domain/github-issue-triage
```

## Human Reading Path

1. Read a playbook.
2. Open the decision points it depends on.
3. Read the claims behind those decisions.
4. Inspect examples and counterexamples.
5. Review evals and change history.

This path is intentionally different from an agent retrieval path. Humans need narrative and examples; agents need scoped, cited, structured knowledge.
