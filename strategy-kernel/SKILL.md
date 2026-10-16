---
name: strategy-kernel
description: "Use when the user asks to diagnose a situation, clarify a problem, apply Good Strategy Bad Strategy, define a guiding policy, choose among solution approaches, or derive coherent actions. Automatically assesses whether visible Diagnosis, Guiding Policy, or Solution Selection are useful, and goes directly to Coherent Actions when the path is clear."
---

# Strategy Kernel

Use this skill to produce and iteratively update a strategy kernel:

1. Diagnosis
2. Guiding Policy
3. Solution Selection when materially different approaches remain
4. Coherent Actions after an approach is selected

## Choose the Response Path

For every request, do a brief internal diagnosis and resolve factual unknowns from available context before asking the user.

- Show a Diagnosis when material questions remain or when there are meaningfully different approaches whose choice would change the outcome.
- Include a Guiding Policy only when it provides a useful strategic direction or decision rule. Do not force one when it does not fit the request.
- Use Solution Selection when multiple materially different, credible approaches remain. Use the Diagnosis and Guiding Policy, when present, as decision criteria.
- When the goal and path are clear, skip visible Diagnosis and Guiding Policy sections and go directly to Coherent Actions when action guidance is requested or appropriate.
- Keep Diagnosis, Guiding Policy, Solution Selection, and Coherent Actions distinct when included. Consolidate repeated points without collapsing the sections into one another.

## Mandatory Planning Checkpoint

When this skill is active, never immediately implement code, edit files, create commits, push branches, or otherwise apply changes.

The agent may inspect the codebase, gather evidence, diagnose the situation, define a guiding policy, and propose coherent actions. After presenting the plan or strategy kernel, stop and wait for the user to approve, revise, or reject it.

Even if the user asks to implement, patch, code, commit, or apply changes in the same message that triggers this skill, treat that as intent to discuss the implementation plan first. Implementation requires a subsequent explicit approval after the plan has been shown.

## Resolve Facts Before Asking

Before asking the user a question, determine whether the answer is a fact that can reasonably be found from available context.

If a fact can be found by searching the codebase, reading files, inspecting tests/configs/docs, or using available tools, resolve it directly instead of asking the user.

Ask the user only for decisions, preferences, priorities, tradeoffs, constraints, or facts that are not reasonably discoverable. When asking, make clear whether the question is a decision the user owns or an unavailable fact needed to proceed.

## Core Workflow

1. Capture the user's stated goal as internal task framing; do not include it in the visible Diagnosis.
2. Briefly assess whether material uncertainty or consequentially different approaches make a visible Diagnosis useful.
3. Gather relevant evidence and resolve discoverable factual unknowns before asking the user:
   - Search the codebase.
   - Inspect relevant files, tests, configs, and docs.
   - Review related threads, tickets, comments, or prior decisions when available.
4. For a visible Diagnosis, describe the problem and relevant causes, facts, constraints, unknowns, assumptions, scope, and challenges. Do not include a Goal or Success Criteria section.
5. Produce or update a concise, consolidated response. Keep applicable sections distinct, combine overlapping points, and omit empty or unhelpful sections.
6. If multiple materially different, credible solution approaches remain, use `references/solution-selection.md` to compare them and select or recommend one before drafting Coherent Actions. If the choice depends on an unresolved user-owned tradeoff, ask the user.
7. Add Coherent Actions when requested or appropriate, based on the selected approach. Put target outcomes and acceptance criteria there when useful.
8. Before finalizing, use `references/adversarial-review.md` to check that the actions support the selected approach and remain consistent with the Diagnosis and Guiding Policy. Revise the reasoning or actions if a decision-relevant challenge breaks the chain.
9. If implementation seems like the next step, present the plan and stop. Do not change files until the user has reviewed the plan and then explicitly asks you to implement it.

## Operating Rules

- Diagnose before design or implementation.
- Do not expand scope beyond the goal without evidence.
- Keep Diagnosis, Guiding Policy, Solution Selection, and Coherent Actions distinct when included, while consolidating repeated content across the response.
- Keep visible Diagnosis problem-oriented; treat the user's goal as internal framing and put useful target outcomes or acceptance criteria with Coherent Actions.
- Use Diagnosis subsections where they add clarity; avoid repeating the same fact under multiple headings.
- Omit Guiding Policy when no useful direction or decision rule follows from the Diagnosis or request.
- Prefer the simplest viable solution.

## Grill Rule

Use `grill-me` before non-trivial coherent actions or architecture decisions.

When using `grill-me`, resolve each question in this order:

1. If the codebase can answer it, inspect the codebase and answer from evidence.
2. If only the user can answer it, ask the user and include a recommended answer.
3. Use the resolved answer to update the diagnosis, guiding policy, coherent actions, or architecture.

## Reference Files

Read only the files needed for the user's request:

- `references/jaded-architect.md`: Read and apply for every Strategy Kernel use, across all visible sections and the final response.
- `references/diagnosis.md`: Read for every strategy-kernel use.
- `references/guiding-policy.md`: Read when the user asks what should be done next, asks for strategy, or the diagnosis needs a decision rule.
- `references/solution-selection.md`: Read when multiple materially different solution approaches remain and must be compared before Coherent Actions.
- `references/coherent-actions.md`: Read when the user asks for next steps, an implementation plan, sequencing, validation, owners, or handoff-ready actions.
- `references/adversarial-review.md`: Read when comparing solution approaches or drafting/revising Coherent Actions; pressure-test the options before selection and check action coherence.
- `references/architecture.md`: Read when the user requests architecture, or when coherent actions require creating or materially changing architecture.

## Response Format

- Use only applicable sections.
- Omit empty sections.
- Consolidate repeated points while preserving the distinction between Diagnosis, Guiding Policy, Solution Selection, and Coherent Actions.
- When Solution Selection is included, show each credible approach as a separate option with its own pros and cons, then end with a recommendation. Do not substitute a summary sentence or checklist for the comparison.
- Do not include the user's goal or a Success Criteria subsection in Diagnosis; include useful acceptance criteria with Coherent Actions.
- Do not include Guiding Policy solely to complete the kernel sequence; include it only when it adds useful direction or a decision rule.
- Prefer factual bullets.
- Keep actions traceable to the guiding policy.
