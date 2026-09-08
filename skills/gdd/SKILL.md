---
name: gdd
description: Rewrite a file, a selection, or inline text in Google developer documentation style. Edits a named file in place. Use the gdd-style skill instead to apply the style to every response for the rest of the session.
argument-hint: "[file, selection, or instructions]"
disable-model-invocation: true
---

Call the Skill tool with "gdd-style", then apply those rules to the target named
in the arguments.

Resolve the target first:

- **A file path**: edit the file in place.
- **Inline text**: rewrite it and output the result.
- **Nothing**: ask what to write or revise.
