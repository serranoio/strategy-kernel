# Architecture

Use architecture when the user requests architecture, or when coherent actions require creating or materially changing architecture.

Before defining architecture, follow `grill-rule.md`.

## Resolve

Resolve the architecture decisions needed to support the guiding policy and coherent actions:

- Boundaries and ownership.
- Data flow and control flow.
- Integration points and dependencies.
- Migration or rollout constraints.
- Failure modes and validation.

Keep the architecture as small as the diagnosis allows. Avoid implementation work before the user has reviewed the plan and then explicitly asked to implement, apply, patch, commit, or otherwise perform the change.
