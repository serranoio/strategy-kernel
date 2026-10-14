# Naming Pass

Use this subworkflow when a product or architecture concept is clear enough to
name, but the name could distort how users, operators, or implementers
understand it.

## Purpose

Choose terminology that preserves the product model before names are baked into
UI text, CLI commands, API fields, schema names, docs, or implementation plans.

## When To Use

Use when one or more are true:

- the user questions or dislikes a proposed term
- a storage-accurate term is awkward in operator language
- one term could ambiguously refer to several layers
- multiple adjacent concepts need clear distinction
- a name will become visible in UI, CLI, API, schema, docs, or scenarios

Skip when naming is private, local, mechanical, already established by the
codebase, or irrelevant to user understanding.

## Workflow

1. Name the concept in one sentence.
   - State what the thing is responsible for.
   - Avoid using candidate names in the definition.

2. List candidate names.
   - Include at least one plain product-language option.
   - Include the technically accurate option when it differs.

3. Score each name briefly against:
   - operator clarity
   - technical accuracy
   - wrong implications
   - collision with existing repo terms
   - UI sentence fit
   - API/schema fit

4. Test candidates in real sentences.
   - Use expected UI, CLI, docs, and architecture phrases.
   - Reject names that sound natural only in storage but awkward in product use.

5. Choose product name and implementation names.
   - Product/UI name
   - DB/API name
   - Related term names for nearby concepts

6. Record avoided names.
   - State why they should not be used so future implementation does not drift
     back to them.

## Output Shape

Use this concise shape when useful:

```md
### Naming Pass

Concept:
- Stable operator-managed config identity across immutable snapshots.

Candidates:
- Config Series: accurate, but archival.
- Config Lineage: good for history, weak for active operation.
- Config Track: active and understandable for parallel experiments.

Chosen:
- Product/UI: Config Track
- DB/API: config_tracks

Related Terms:
- Config Snapshot: immutable complete row in configs
- Config Patch: scoped JSON Patch change

Avoid:
- Config Series: sounds archival and less operator-active.
- Config: collides with immutable snapshots.
```

Keep the pass short. Its job is to protect the model from bad terminology, not
to reopen all architecture decisions.
