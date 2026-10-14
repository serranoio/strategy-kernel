# Grill Rule

Use this reference before non-trivial coherent actions or architecture
decisions.

## Rule

Run a grill pass before non-trivial coherent actions or architecture decisions.

Resolve each question in this order:

1. If the codebase can answer it, inspect the codebase and answer from evidence.
2. If only the user can answer it, ask the user and include a recommended
   answer.
3. Use the resolved answer to update the diagnosis, guiding policy, coherent
   actions, or architecture.

If the user needs to understand or choose between scenario behaviors, use
`interactive-model-grill.md`.
