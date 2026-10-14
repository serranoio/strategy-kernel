# Execution Modes

Use this reference when the user selects an execution workflow.

Execution modes are post-kernel workflows. Selecting `pr mode` or `local mode`
in the same message that invokes Strategy Kernel does not authorize execution.
First produce the strategy kernel and implementation plan, then stop. Execution
requires a later explicit approval after the kernel has been presented.

## Mode Selection

The user can select a workflow by mentioning one exact phrase:

- `pr mode`: execute through a pull request workflow.
- `local mode`: execute through a local worktree workflow.

If multiple execution modes appear, ask the user to choose one before
proceeding.

## PR Mode

When the user selects `pr mode`:

1. Produce the strategy kernel and implementation plan first.
2. Stop and wait for explicit approval in a later user message after the plan.
3. Create or reuse an appropriate branch.
4. Implement the approved change.
5. Run focused validation.
6. Commit the change.
7. Push the branch and open a pull request.
8. Review the pull request, including comments and failed checks when
   available.
9. Repair issues until the pull request is merge-ready.
10. Merge the pull request after validation passes.

Use repository-specific PR tooling, existing skills, and connected services
when available. Do not skip validation unless the user explicitly requests it
and the residual risk is stated.

## Local Mode

When the user selects `local mode`:

1. Produce the strategy kernel and implementation plan first.
2. Stop and wait for explicit approval in a later user message after the plan.
3. Create a dedicated Git worktree for the approved change.
4. Implement the approved change inside that worktree.
5. Run focused validation inside the worktree.
6. Commit the change in the worktree.
7. Merge the completed branch back into the original working branch locally.
8. Clean up the worktree when it is no longer needed.

Keep unrelated local changes intact. If the original working branch or target
branch has conflicting user changes, stop and explain the conflict before
merging.
