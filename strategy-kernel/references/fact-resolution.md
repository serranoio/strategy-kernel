# Fact Resolution

Use this reference when gathering evidence or deciding whether to ask the user
a question.

## Rule

Before asking the user a question, determine whether the answer is a fact that
can reasonably be found from available context.

If a fact can be found by searching the codebase, reading files, inspecting
tests/configs/docs, or using available tools, resolve it directly instead of
asking the user.

Ask the user only for decisions, preferences, priorities, tradeoffs,
constraints, or facts that are not reasonably discoverable. When asking, make
clear whether the question is a decision the user owns or an unavailable fact
needed to proceed.

## Existing Capability Search

For existing-codebase work, search before proposing new implementation.

Check whether the requested capability already exists as code, tests, config,
docs, scripts, workflows, CLI commands, planning artifacts, or reusable
patterns.

Use targeted searches first:

- User-facing names and domain terms.
- Likely function, class, module, command, route, or artifact names.
- Adjacent concepts, synonyms, and older terminology.
- Existing docs, tests, scripts, configs, and planning artifacts.

Resolve the search into one of four outcomes:

- Reuse existing capability.
- Extend existing capability.
- Replace or consolidate overlapping capability.
- Build new, with a reason the existing candidates are insufficient.

Do not treat "nothing obvious came to mind" as evidence. Search.
