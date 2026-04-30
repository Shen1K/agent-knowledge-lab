# Migration Path

The first version is Markdown-first. That is intentional.

Markdown is easy to read, easy to edit, easy to diff, and easy for models to generate. It is not the final storage layer for every future use case.

## Possible Evolution

```text
Markdown files
  -> Markdown with validators
  -> indexed knowledge store
  -> graph database
  -> collaborative service
```

## What Must Stay Stable

- IDs
- types
- schema versions
- evidence references
- relationship semantics
- status lifecycle
- change history

## What Can Change

- storage backend
- retrieval strategy
- UI
- review workflow
- evaluation automation
- graph visualization

## Design Rule

Do not optimize the storage backend before the knowledge method is proven.
