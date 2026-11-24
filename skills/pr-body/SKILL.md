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

State the expected benefits and risks, concisely, for users and for the system.
Write one bullet per benefit or risk, and label each one.

- **Benefit**: what gets better, and for whom.
  Users and customers see changed behavior, output, or UI.
  The system gains in performance, error handling, or maintainability.
- **Risk**: what could break or get worse, and for whom.
  Cover backward compatibility, data migrations, config or environment changes,
  added cost or latency, and new failure modes.
- When a change has neither, say so directly, for example
  "No user-facing impact." An internal refactor or a test-only change usually
  lands here.

## Verification

List the checks concisely, in two groups.

- **Performed**: each check you ran and what it showed.
  Name the test suites, and say whether they're new or existing.
  For manual checks, give the steps and what you observed.
- **Still needed**: the checks this PR's scope calls for that haven't run yet,
  such as a staging smoke test or a run of a changed workflow.
  Size the list to the risks in Impact. Each listed risk needs a check in one
  of the two groups.

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
