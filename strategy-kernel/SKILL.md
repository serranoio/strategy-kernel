---
name: strategy-kernel
description: "Use when the user asks to diagnose a situation, clarify a goal, apply Good Strategy Bad Strategy, define a guiding policy, decide what to do next, or derive coherent actions from a diagnosis. Always runs kernel-first: diagnose the situation, force the necessary decisions, form coherent actions, and stop before implementation until the user approves execution in a later turn."
---

# Strategy Kernel

Run the strategy kernel as an active strategy dialogue: diagnose the situation,
force the necessary decisions, and form coherent actions.

Orchestrate a strategy kernel in this order:

1. Diagnosis
2. Guiding Policy
3. Coherent Actions

Use `references/pass-to-subagent.md` as a step-local escape hatch when one
kernel step is too broad for the main context. The subagent returns a handoff;
the main agent keeps ownership of the kernel.

Apply the Jaded Architect tone throughout: direct, consequence-aware, precise,
and allergic to bullshit.

## Invocation Contract

When this skill is invoked, always form the strategy kernel first.

- Every invocation must produce or update a strategy kernel: diagnosis, guiding
  policy, coherent actions, or a partial kernel with the next decision-bearing
  question.
- Do not implement while Strategy Kernel is active.
- Do not edit files, patch code, create commits, push branches, deploy, run
  migrations, change external state, or execute the proposed plan.
- Treat same-message requests to implement, apply, patch, commit, push, or
  execute as intent to discuss the implementation plan, not permission to
  perform it.
- Execution requires a later explicit user approval after the kernel has been
  presented.
- End the turn at the completed or partial kernel. Do not cross into
  implementation.

Default to a discussion that moves toward action. Do not stop at diagnosis
unless the user explicitly asks for diagnosis only, asks for a one-shot
assessment, or implementation-level action would be premature without a user
decision.

## Dialogue Standard

Treat the interaction as a decision-forming conversation, not a static report.

- Start by naming the situation and the decision that must be made.
- Resolve discoverable facts by inspecting available code, tests, configs,
  docs, and tool output before asking the user or drafting coherent actions.
- Ask only decision-bearing questions: questions whose answers change the
  diagnosis, guiding policy, or coherent actions.
- When enough is known, state the diagnosis, propose the guiding policy, and
  draft coherent actions.
- When not enough is known, present the smallest useful partial kernel and the
  specific decision needed to continue.
- Keep pressure on coherence: every action must trace back to the diagnosis and
  guiding policy.

## Core Orchestration

1. Capture the user's stated goal.
2. Resolve discoverable facts by inspecting available code, tests, configs,
   docs, and tool output before asking the user or drafting coherent actions.
   For existing-codebase work, explicitly check whether the requested
   capability, pattern, workflow, or artifact already exists before proposing
   new work.
3. When one step is too broad, use `references/pass-to-subagent.md` for that
   step only, then integrate the handoff before moving to the next kernel layer.
4. Separate facts, assumptions, constraints, unknowns, success criteria, out of
   scope items, and challenges.
5. Route to optional subworkflows when their trigger fits:
   - Product Model Exploration
   - Naming Pass
   - Interactive Model Grill
   - Grill Rule
6. Identify the decision that gates coherent action.
7. Produce or update the concise strategy kernel.
8. Add guiding policy and coherent actions unless explicitly scoped out or
   blocked by a required user decision.
9. Run the final compression pass in `references/response-format.md` on the
   completed or partial kernel.
10. End the turn at the compressed kernel. Do not implement.

## Reference Routing

Read only the files needed for the request:

- `references/tone.md`: Read for every strategy-kernel use.
- `references/diagnosis.md`: Read for every strategy-kernel use.
- `references/fact-resolution.md`: Read when facts, context, or user questions
  need to be resolved before diagnosis.
- `references/pass-to-subagent.md`: Read when one Strategy Kernel step needs a
  bounded subagent handoff to avoid context mixing.
- `references/product-model-exploration.md`: Read when competing product
  abstractions could satisfy the technical goal.
- `references/naming-pass.md`: Read when terminology could distort product
  understanding or become UI/CLI/API/schema/docs.
- `references/interactive-model-grill.md`: Read when the user wants to be
  grilled, needs to understand a proposed system, or must choose between
  user-owned behaviors.
- `references/guiding-policy.md`: Read when the user asks what should be done
  next, asks for strategy, or the dialogue has enough diagnosis to need a
  decision rule.
- `references/coherent-actions.md`: Read when the user asks for next steps, an
  implementation plan, sequencing, validation, owners, handoff-ready actions, or
  when the dialogue has enough guiding policy to form a responsible action
  draft. For existing-codebase plans, pair it with `references/fact-resolution.md`
  and `references/grill-rule.md`.
- `references/architecture.md`: Read when the user requests architecture, or
  when coherent actions require creating or materially changing architecture.
- `references/grill-rule.md`: Read before non-trivial coherent actions or
  architecture decisions.
- `references/execution-modes.md`: Read when the user selects `pr mode` or
  `local mode`.
- `references/planning-checkpoint.md`: Read for every strategy-kernel use to
  enforce the execution boundary.
- `references/response-format.md`: Read for every strategy-kernel use; run its
  final compression pass before sending the response.
