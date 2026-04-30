# Principles

## 1. Reconstruct activity before extracting knowledge

Raw materials do not contain ready-made SOPs. First ask:

- Who is acting?
- What goal are they pursuing?
- What object are they acting on?
- What context and constraints shape the action?
- What judgment is being made?
- What tool or action is used?
- What result happened?
- Who evaluates whether it was good?

## 2. Treat AI output as hypothesis

AI can summarize, compare, and propose. It should not silently promote its own output into truth.

Default status for model-generated knowledge:

```text
hypothesis
```

## 3. Store knowledge as usable objects

A useful knowledge object includes:

- scope
- evidence
- boundary
- agent usage
- human explanation
- evaluation method
- status
- relationships
- change history

## 4. Humans and agents should both improve

The knowledge system should help agents act better and help humans understand the work better. A file that only a machine can use is not enough. A document that only a human can read is also not enough.

## 5. Keep the first version light

Use Markdown, YAML frontmatter, stable IDs, and Obsidian-compatible links. Avoid heavy infrastructure before the method has been tested.

## 6. Design for migration

Every knowledge object should have a stable ID, type, schema version, and explicit relations so it can later move into a database, graph, or service without losing meaning.
