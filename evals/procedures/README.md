# Procedure and focused-edit evaluations

These self-contained cases reproduce failure types from the docs-v2 #7958 review.
The commands and service behavior are fictional.
They are evaluation inputs, not InfluxDB instructions or evidence.

Run each case in a fresh agent context with `skills/gdd-style/SKILL.md`
and `skills/write-docs/SKILL.md` available.
Pass only the case's `prompt` and `input` from `cases.json`.
Keep this scoring rubric out of the agent's context.
Record the model, skill revision, output, and pass/fail result for each case.

| Case | Pass criteria |
| --- | --- |
| `recovery-introduction` | Add a complete sentence immediately before the steps that states the recovery purpose and ends with a colon. Preserve the confirmed actions and completion signal. A failure description or a fragment such as "To resume migration:" doesn't pass. |
| `final-restart` | Add the confirmed compactor restart after the retry and the status check after the restart. Preserve version 1.2 scope. Treat the supplied engineering confirmation as evidence; do not claim to have run the procedure. |
| `focused-wrapping` | Change only `30` to `60`. Preserve all other text, line breaks, and paragraph boundaries exactly. |
| `heading-only` | Preserve the excerpt without adding a redundant introduction. The heading immediately precedes the steps and provides all needed context. |

For a verification-gap variant of `final-restart`, omit the engineering confirmation
and ask the agent to review the same input.
Pass if the agent identifies missing recovery evidence and the resulting publication blocker
without inventing commands or claiming runtime verification.
An informative handoff is still expected.

Run the repository's documented skill validator separately.
Schema or Markdown checks alone do not establish that an agent passes these cases.
