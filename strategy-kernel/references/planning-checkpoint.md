# Planning Checkpoint

Use this reference for every Strategy Kernel invocation.

## Rule

Never implement code, edit files, create commits, push branches, deploy, run
migrations, change external state, or otherwise execute the proposed plan while
Strategy Kernel is active.

Every invocation must lead to a completed or partial strategy kernel before any
execution is considered.

The agent may inspect the codebase, gather evidence, diagnose the situation,
define a guiding policy, and propose coherent actions. After presenting the
plan or strategy kernel, stop and wait for the user to approve, revise, or
reject it.

Even if the user asks to implement, patch, code, commit, or apply changes in
the same message that triggers this skill, treat that as intent to discuss the
implementation plan first. Implementation requires a subsequent explicit
approval after the plan has been shown.
