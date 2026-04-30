# Self-Audit

This file records known risks in the first design.

## Risk: Too many concepts

`case`, `claim`, `decision point`, `rule`, `playbook`, and `eval` may be too much for new users.

Mitigation:

- Keep the README simple.
- Maintain one concrete example.
- Add learning paths before adding more abstractions.

## Risk: Markdown may not scale

Markdown is good for early work but weak for large-scale querying, permissioning, and analytics.

Mitigation:

- Use stable IDs and schema versions.
- Keep machine-readable frontmatter.
- Prepare for migration without starting with a database.

## Risk: Knowledge relationships can become noisy

If every note links to every other note, the graph becomes decorative instead of useful.

Mitigation:

- Keep relation types small.
- Prefer meaningful relations over vague related links.
- Add linting later for orphaned, excessive, or circular relations.

## Risk: AI-generated knowledge may look more reliable than it is

A polished claim can hide weak evidence.

Mitigation:

- Default AI output to `hypothesis`.
- Require evidence and evaluation fields.
- Preserve counterexamples and boundaries.

## Risk: Agent optimization may harm human understanding

Highly compressed machine instructions may be hard for humans to learn from.

Mitigation:

- Require human explanation.
- Include examples and counterexamples.
- Keep Obsidian-friendly navigation.

## Risk: Feedback attribution is hard

When an output fails, it may be unclear whether the problem came from the model, missing data, wrong knowledge, bad retrieval, or tool limitations.

Mitigation:

- Require agents to cite knowledge IDs they used.
- Track output results against cited knowledge.
- Use change proposals rather than silent overwrites.

## Risk: Local rules may be over-generalized

A rule learned from one repository or team may not apply elsewhere.

Mitigation:

- Use scope levels.
- Separate general, domain, project, and tool knowledge.
- Record `does_not_apply_when` and counterexamples.
