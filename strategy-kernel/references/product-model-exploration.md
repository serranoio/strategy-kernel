# Product Model Exploration

Use this subworkflow when the diagnosis shows the technical goal can be
satisfied by multiple product abstractions.

## Purpose

Find the product model that preserves product truth before turning the diagnosis
into guiding policy, architecture, or implementation actions.

## When To Use

Use when the problem involves one or more of:

- operator or user mental models
- lifecycle, status, promotion, readiness, assignment, or ownership semantics
- history, versioning, rollback, snapshots, or stale sibling state
- evidence, provenance, auditability, or metrics attribution
- UI-facing entities where naming determines user understanding
- a backend object that could represent several product concepts

Skip when the task is a narrow bug fix, mechanical refactor, already-approved
implementation, or direct code change with no competing product meaning.

## Workflow

1. Name the competing product models.
   - Use short names.
   - Include the operator-facing meaning of each model.

2. Test each model against concrete scenarios.
   - Prefer 3-5 scenarios.
   - Include edge cases that can expose stale state, misleading UI, or broken
     evidence attribution.
   - If the user needs to understand or choose between scenario behaviors, use
     `interactive-model-grill.md` before selecting the model.

3. Separate layers for each viable model:
   - product object
   - change unit
   - persisted object
   - runtime object
   - evidence or audit object
   - UI object

4. Run an object identity check.
   - Ask: "What is the stable thing the operator thinks they are managing?"
   - If the answer is a DB row, verify that is truly the product object and not
     just an implementation artifact.

5. Run a runtime contract check.
   - Identify which existing runtime behavior must remain boring and unchanged.
   - Do not choose a model that forces runtime complexity unless the product
     need truly requires it.

6. Run a naming pass when terms feel awkward.
   - List candidate names.
   - Prefer the name that matches operator language over the name that merely
     describes storage.

7. Choose the model.
   - State why it beats the alternatives.
   - State what remains out of scope.
   - Feed the chosen model into guiding policy and coherent actions.

## Output Shape

Use this concise structure when useful:

```md
### Product Models
- Model A: ...
- Model B: ...
- Model C: ...

### Scenario Tests
- Scenario: ...
  - Model A: ...
  - Model B: ...

### Chosen Model
...

### Model Layers
- Product object:
- Change unit:
- Persisted object:
- Runtime object:
- Evidence object:
- UI object:
```

Keep this exploratory. Do not turn it into an implementation plan until a model
has been chosen.
