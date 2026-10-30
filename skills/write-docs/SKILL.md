---
name: write-docs
description: Write or revise a documentation page for its content type, such as a tutorial, how-to guide, reference, or explanation. Use when drafting, restructuring, or reviewing a docs page, or when it's unclear whether the reader or the system should be the actor.
license: MIT
metadata:
  author: influxdata
---

Load the gdd-style skill first.
Its rules apply to every page.
This skill adds the rules that depend on the content type.

## 1. Name the content type

Decide the page's content type before you write or revise it.
If the page mixes types, tell the writer and suggest a split.

| Content type | The reader wants to | Who acts | Voice |
| --- | --- | --- | --- |
| Tutorial | learn by doing | the reader | Imperative steps and "you." One path, no alternatives. |
| How-to guide | finish a task they already understand | the reader | Imperative steps. State each condition before its step. |
| Reference | look up a fact | the system: a server, API, command, or component | Name the component. Passive voice is fine when the actor is unknown or irrelevant. Use "you" only for what the reader supplies or controls. |
| Explanation | understand why something works as it does | the system or the design | Name the component or the decision. Keep reasons and tradeoffs. |

## 2. Make the actor clear

- **When the reader acts, say so.**
  Use the imperative or "you."
  Domain experts often write "the column is added" when the reader adds it.
  In a tutorial or how-to guide, rewrite that as "Add the column."
- **When the system acts, name the part that acts:**
  "The server rejects the write," not "The write is rejected."
- **When you can't tell who acts, keep the passive.**
  Flag the sentence for the writer.
  A technical writer or the page's owner makes that call.

When you revise, gdd-style's fidelity check still applies.
Making the reader the actor of a step the source already describes isn't a new claim.
Naming a system actor the source doesn't state is.

## 3. Verify procedures through completion

For each procedure, trace the reader's actions from the starting condition to the expected result.
Check prerequisites, actors, failure handling, required restarts, and observable completion signals.
A reset or retry command can prepare recovery without completing it.
Check what must happen afterward.

For consequential operations, such as upgrades or recovery,
require runtime verification or explicit engineering confirmation for the applicable product and version.
Record the evidence and any remaining gaps.
If verification is unavailable, provide the correction or finding in the handoff
and identify the gap that blocks publication.
Keep unverified actions and completion signals flagged for confirmation rather than inventing them.

## 4. Check before you finish

The page is done when:

- it has one content type, or you've flagged the mix;
- every step and every system behavior has an actor, or a flag;
- the voice matches the row for its content type;
- lists and procedures satisfy gdd-style's introduction rule;
- procedures cover the path through completion, with evidence or explicit publication blockers;
- focused corrections preserve unrelated wrapping and wording.
