---
name: pr-body
description: "Structures pull request descriptions into four fixed sections: What changed, Why, Impact, Verification. Use when writing or revising a PR body, or when the user asks to draft, fill in, or fix up a pull request description."
---

# PR body structure

Write the PR description in these four sections, in this order.
Omit a section only when it's genuinely empty.
A docs-only PR, for example, has no user-facing impact.
Say that under the heading rather than deleting the heading.

## What changed

State facts about the diff.
Leave the reasoning for Why.
Use short bullets or short sentences.
Give each line one change: what you added, removed, renamed, or made behave
differently.

## Why

Explain what drove the change, in a few sentences.
Name the problem, request, bug, or constraint behind it.
Link the issue or ticket when one exists.
Write prose, not a bullet list.
A reader who doesn't know the backstory should be able to follow it.

## Impact

Say who and what the change affects, and how.

- **Users and customers**: state whether behavior, output, or the UI changes for
  them, and whether they can see the change happen.
- **System behavior**: cover performance, error handling, backward
  compatibility, data migrations, and config or environment changes.
- **Neither**: say so directly. Write "No user-facing impact." An internal
  refactor or a test-only change usually lands here.

## Verification

State what you checked, and what the reviewer or CI still should.

- Automated tests you ran: which suites, and whether they're new or existing.
- Manual validation you performed: the steps you took, and what you observed.
- Checks still needed before merge, such as a staging smoke test.

## Rules

- Pull code-change facts from the actual diff and commit history.
  Check workflow-state claims against current PR metadata.
  Don't invent changes, impact, or verification steps that didn't happen.
- Before updating an existing PR, read its current body, title, base, head SHA,
  open or closed state, and draft status. Recheck state claims immediately before
  writing if the artifact could have changed. Preserve user-controlled fields
  outside the requested edit, including draft status. If current metadata is
  unavailable, omit state claims or mark them unverified.
- After an authorized update, reread the PR to verify the saved body and state.
- Keep What changed factual.
  Keep Why explanatory without selling the change.
  Don't blend the two.
- When impact or verification is unknown, write "not yet verified."
  Don't omit the section, and don't guess.
- Match the terse, factual tone the repository already uses in its PR
  conventions.
- If the `docs-skills` plugin is installed,
  apply its `gdd-style` skill's prose rules within each section.
- This skill governs body structure and content only.
  The `open-pr` skill gathers the facts and opens the PR.
