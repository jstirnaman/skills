---
name: gdd
description: Rewrite a file, a selection, or inline text in Google developer documentation style. Edits a named file in place. Use the gdd-style skill instead to load the rules and apply them to everything written from then on.
argument-hint: "[file, selection, or instructions]"
disable-model-invocation: true
---

Call the Skill tool with "gdd-style",
then apply those rules to the target named in the arguments.

Resolve the target first:

- **A file path**: edit the file in place.
- **Inline text**: rewrite it and output the result.
- **Nothing**: ask what to write or revise.

For a file or inline text,
run the fidelity check in gdd-style's "When you revise existing text" section before you finish.
For a file longer than about 150 lines,
dispatch a subagent to run the check with only the original and the revision.
