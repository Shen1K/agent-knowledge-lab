# Knowledge Generation Skill

Use this skill when turning raw materials into knowledge that can be used by humans and AI agents.

## Goal

Generate structured, falsifiable, and maintainable knowledge from documents, data, images, issues, chats, or execution traces.

Do not jump directly from raw materials to final rules. First reconstruct human activity, then propose knowledge.

## Workflow

1. **Collect raw materials**
   Preserve the original material or a pointer to it. Do not rewrite evidence as knowledge.

   When raw materials come from multiple public sources, create source notes before creating claims. Source notes should record source type, observed pattern, relevance, limitations, and evidence strength.

2. **Reconstruct activity**
   For each relevant episode, identify:
   - actor
   - goal
   - object
   - context
   - constraints
   - judgment
   - action
   - tool
   - result
   - evaluation signal

3. **Create case cards**
   Turn important episodes into case cards. A case card should describe what happened, not what should always happen.

4. **Compare cases**
   Look for repeated judgments, repeated actions, success and failure differences, missing information, exceptions, and expert behavior.

5. **Propose knowledge claims**
   A claim is a scoped, evidenced, usable, and falsifiable statement. AI-generated claims default to `status: hypothesis`.

6. **Attach boundaries**
   For every claim, describe when it applies, when it does not apply, and what counterexamples are known.

7. **Connect knowledge**
   Add relationships such as `depends_on`, `supports`, `conflicts_with`, `generalizes`, `specializes`, and `derived_from`.

8. **Define evaluation**
   Every actionable claim should include how it could be tested or observed in future work.

9. **Generate change proposals**
   When updating existing knowledge, propose changes with reasons and evidence. Do not silently overwrite validated knowledge.

## Output Rules

- Prefer Markdown with YAML frontmatter.
- Use stable IDs.
- Use Obsidian-style `[[wiki links]]` in human-facing sections.
- Keep machine-readable metadata in frontmatter.
- Keep human explanation, examples, and counterexamples in the body.
- Distinguish hypothesis, reviewed, validated, conflicted, and deprecated knowledge.
- Distinguish source types and evidence strength when public guides, issue samples, papers, and maintainer comments are mixed.

## Default Statuses

```text
hypothesis: AI-generated or weakly supported.
reviewed: human has checked the claim for plausibility.
validated: supported by evidence, evaluation, or repeated successful use.
conflicted: contradicted by another claim or case.
deprecated: no longer recommended.
```

## Minimum Knowledge Claim

A minimum claim must include:

- id
- type
- title
- scope
- status
- claim
- evidence
- evidence_strength
- transferability
- applies_when
- does_not_apply_when
- agent_use
- human_explanation
- evaluation

## Anti-Patterns

- Treating summaries as knowledge.
- Promoting model output to truth without evidence.
- Writing rules without boundaries.
- Writing agent-only instructions that humans cannot understand.
- Writing human-only essays that agents cannot use.
- Adding vague `related` links instead of meaningful relation types.
