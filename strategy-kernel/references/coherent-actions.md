# Coherent Actions

Use coherent actions to propose the implementation plan that follows from the
guiding policy.

Coherent actions are proposed actions only. They are not permission to execute.
Do not implement, apply, patch, commit, push, deploy, or otherwise perform the
actions while Strategy Kernel is active.

Before writing non-trivial coherent actions, follow `grill-rule.md`.

## Evidence Gate

For existing-codebase work, inspect the relevant code paths before drafting
coherent actions. Use available code, tests, configs, docs, and tool output to
answer facts directly. Include an Existing Capability Check before the numbered
plan: name the search terms or paths inspected, existing candidates found, and
the reuse, extend, replace, or build-new decision.

Before the numbered plan, name the observed files, functions, configs, tests, or
runtime evidence that shaped the actions. If a necessary fact cannot be
inspected, mark it as an unknown and explain why.

If building new, explain why the existing candidates are insufficient.

Do not propose implementation steps that depend on uninspected code as if they
were established facts. "Inspect X" is only a valid first action when X is not
available to inspect now or the user explicitly asked for a plan without
inspection.

## Write The Plan

Write actions as numbered, step-by-step work.

When revising coherent actions, update them in place and reprint the full numbered list every time; do not print only deltas.

Prefer vertically sliced, independent units. Mention subagents only when the
user requests them or the selected execution mode requires them.

When coherent actions become an implementation plan, derive requirements from user scenarios when they exist. Represent them as a list of user scenarios, each with a nested acceptance-criteria list, and make each action trace back to the relevant scenario criteria.

Include:

- Evidence observed before drafting the plan.
- Concrete next steps.
- Sequencing and dependencies.
- Validation for each meaningful slice.
- Owners or handoff boundaries when known.
- Relevant workflow skills present in the repo.

Avoid:

- Disconnected actions.
- Unnecessary complexity.
- Unsupported steps that should have been resolved by inspecting available code.
- Steps that do not trace back to the guiding policy.
- Implementation work before the user has reviewed the kernel and then approved
  execution in a later explicit message.
