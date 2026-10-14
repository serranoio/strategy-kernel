# Strategy Kernel

An agent skill for working through a strategy dialogue in three steps:

1. **Diagnosis** — identify the situation, constraints, and central challenge.
2. **Guiding policy** — decide how to address that challenge.
3. **Coherent actions** — form a practical set of actions that follows the policy.

The skill resolves discoverable facts before asking questions, surfaces decisions that matter, and stops before implementation until the user approves execution in a later turn.

## Installation

Clone this repository and copy the entire `strategy-kernel` directory into your agent’s skills directory. Keep `SKILL.md` and `references/` together.

## Usage

Ask your agent to use the Strategy Kernel skill to work through a situation or decision. For example:

> Use strategy-kernel to help me decide what to build next and form a coherent action plan.

### Diagnosis only

For a diagnosis-only assessment, explicitly ask for **“diagnosis only”** or a **“one-shot assessment.”** The skill stops after diagnosis instead of proceeding to guiding policy and coherent actions.

> Use strategy-kernel in diagnosis-only mode to assess why onboarding conversion is low.

See [SKILL.md](strategy-kernel/SKILL.md) for the full workflow and [references/](strategy-kernel/references/) for its supporting instructions.
