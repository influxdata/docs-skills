---
name: gdd
description: Rewrite a named file, a selection, or inline text in Google developer documentation style, editing a named file in place. Use only when the user explicitly asks to rewrite or revise something with gdd. To apply the style rules to everything written from then on, use the gdd-style skill instead.
license: MIT
metadata:
  author: influxdata
---

Load the gdd-style skill,
then apply its rules to the target the user names.

Resolve the target first:

- **A file path**: edit the file in place.
- **Inline text**: rewrite it and output the result.
- **Nothing**: ask what to write or revise.

For a file or inline text,
run the fidelity check in gdd-style's "When you revise existing text" section before you finish.
For a file longer than about 150 lines,
run the check in a separate agent or subagent, if your environment supports one,
and give it only the original and the revision.
