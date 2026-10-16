# Coherent Actions

Use coherent actions to produce the implementation plan that follows from the guiding policy.

Before writing non-trivial coherent actions, use `grill-me` and follow the `Grill Rule` in `SKILL.md`.

## Write The Plan

Write actions as numbered, step-by-step work.

Write Coherent Actions only after a solution has been selected or recommended. Before finalizing the actions, use `adversarial-review.md` to check that they implement the selected solution and remain consistent with the Diagnosis and Guiding Policy. Revise the plan if a decision-relevant challenge breaks that chain. Keep the review concise; show it only when requested or when it changes, qualifies, or blocks the recommendation.

When revising coherent actions, update them in place and reprint the full numbered list every time; do not print only deltas.

Prefer vertically sliced, independent units that can be assigned to subagents or worked in parallel when dependencies allow.

When coherent actions become an implementation plan, derive requirements from user scenarios when they exist. Represent them as a list of user scenarios, each with a nested acceptance-criteria list, and make each action trace back to the relevant scenario criteria.

Include:

- Concrete next steps.
- Sequencing and dependencies.
- Validation for each meaningful slice.
- Owners or handoff boundaries when known.
- Relevant workflow skills present in the repo.

Avoid:

- Disconnected actions.
- Unnecessary complexity.
- Steps that do not trace back to the guiding policy.
- Implementation work before the user has reviewed the plan and then explicitly asked to implement, apply, patch, commit, or otherwise perform the change.
