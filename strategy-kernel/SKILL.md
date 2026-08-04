---
name: strategy-kernel
description: "Use when the user asks to diagnose a situation, clarify a goal, apply Good Strategy Bad Strategy, define a guiding policy, or derive coherent actions from a diagnosis. Produces a neutral strategy kernel: diagnosis first, then guiding policy and coherent actions when requested or appropriate."
---

# Strategy Kernel

Use this skill to produce and iteratively update a strategy kernel in order:

1. Diagnosis
2. Guiding Policy
3. Coherent Actions

Default to diagnosis only unless the user asks what to do next, asks for strategy, or the task requires moving from diagnosis into action.

## Mandatory Planning Checkpoint

When this skill is active, never immediately implement code, edit files, create commits, push branches, or otherwise apply changes.

The agent may inspect the codebase, gather evidence, diagnose the situation, define a guiding policy, and propose coherent actions. After presenting the plan or strategy kernel, stop and wait for the user to approve, revise, or reject it.

Even if the user asks to implement, patch, code, commit, or apply changes in the same message that triggers this skill, treat that as intent to discuss the implementation plan first. Implementation requires a subsequent explicit approval after the plan has been shown.

## Resolve Facts Before Asking

Before asking the user a question, determine whether the answer is a fact that can reasonably be found from available context.

If a fact can be found by searching the codebase, reading files, inspecting tests/configs/docs, or using available tools, resolve it directly instead of asking the user.

Ask the user only for decisions, preferences, priorities, tradeoffs, constraints, or facts that are not reasonably discoverable. When asking, make clear whether the question is a decision the user owns or an unavailable fact needed to proceed.

## Core Workflow

1. Capture the user's stated goal.
2. Gather relevant evidence and resolve discoverable factual unknowns before asking the user:
   - Search the codebase.
   - Inspect relevant files, tests, configs, and docs.
   - Review related threads, tickets, comments, or prior decisions when available.
3. Separate facts, assumptions, constraints, unknowns, success criteria, out of scope items, and challenges.
4. Produce or update the concise strategy kernel in the response.
5. Add guiding policy and coherent actions only when requested or appropriate.
6. If implementation seems like the next step, present the plan and stop. Do not change files until the user has reviewed the plan and then explicitly asks you to implement it.

## Operating Rules

- Diagnose before design or implementation.
- Do not expand scope beyond the goal without evidence.
- Keep diagnosis, guiding policy, and coherent actions distinct.
- Prefer the simplest viable solution.

## Grill Rule

Use `grill-me` before non-trivial coherent actions or architecture decisions.

When using `grill-me`, resolve each question in this order:

1. If the codebase can answer it, inspect the codebase and answer from evidence.
2. If only the user can answer it, ask the user and include a recommended answer.
3. Use the resolved answer to update the diagnosis, guiding policy, coherent actions, or architecture.

## Reference Files

Read only the files needed for the user's request:

- `references/diagnosis.md`: Read for every strategy-kernel use.
- `references/guiding-policy.md`: Read when the user asks what should be done next, asks for strategy, or the diagnosis needs a decision rule.
- `references/coherent-actions.md`: Read when the user asks for next steps, an implementation plan, sequencing, validation, owners, or handoff-ready actions.
- `references/architecture.md`: Read when the user requests architecture, or when coherent actions require creating or materially changing architecture.

## Response Format

- Use only applicable sections.
- Omit empty sections.
- Prefer factual bullets.
- Keep actions traceable to the guiding policy.
