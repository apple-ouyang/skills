# Resource Boundaries

Use this guide when deciding what belongs in `SKILL.md` versus bundled resources.

## Principle

`SKILL.md` should be small enough to route and execute clearly, but not so small that the model must read a reference before it knows the job, boundary, workflow, or output contract.

Progressive disclosure only saves context when extra files are loaded conditionally. If every invocation must read the same reference, the split is for maintenance, not context efficiency.

## Keep In `SKILL.md`

Keep content in `SKILL.md` when it is:

- part of the trigger surface or near-neighbor exclusions
- part of the core execution skeleton
- part of the output contract
- necessary for branch selection
- a safety default or irreversible-action guardrail
- a short rule that would cause wrong behavior if missed

## Move To `references/`

Move content to `references/` when it is:

- domain-specific guidance used only for some tasks
- long examples or comparison material
- schemas, templates, rubrics, or policy text
- background doctrine for reviewers or maintainers
- independently maintained detail that changes more often than the skill entrypoint

When a reference file is longer than a quick skim, give it a table of contents or a short opening summary so the model can navigate it reliably.

## Move To `scripts/`

Move content to `scripts/` when it is:

- deterministic
- repetitive across runs
- brittle if rewritten from prose
- easier to validate as code than as instruction text

If multiple eval runs recreate the same helper script, bundle that script and tell `SKILL.md` when to use it.

## Always-Read References

An always-read reference is a design signal.

First ask whether the critical content should be compressed back into `SKILL.md`. This is usually correct when the reference contains the normal workflow, safety rules, routing logic, or output contract.

Keep an always-read reference only when it earns its maintenance cost:

- it is long but stable reference material
- it needs separate review or version control
- it is shared by multiple skills
- it is a contract or schema that should remain canonical outside prose

When keeping one, `SKILL.md` must say exactly when to read it and summarize the non-negotiable rules so a missed read does not silently change the skill's behavior.

## Quick Test

Before moving content out of `SKILL.md`, ask:

1. Can the model still choose the right path without this text?
2. Can the model still produce the right output shape without this text?
3. Is this detail conditional, long, or independently maintained?
4. Does the split reduce current ambiguity, execution burden, route risk, or maintenance risk?

If the answer to the first two questions is no, keep a compressed version in `SKILL.md`.
