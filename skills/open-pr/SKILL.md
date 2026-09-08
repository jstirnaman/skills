---
name: open-pr
description: Draft a structured pull request description from the current branch's actual changes, then open the PR or write a local draft.
argument-hint: "[base branch, issue/ticket, or instructions]"
disable-model-invocation: true
---

Draft and open the pull request for the current branch. The `pr-body` skill
governs what the description says; this skill gathers the facts and performs the
push.

## 1. Gather facts

Run `git status`, `git diff` against the merge-base with the base branch, and
`git log` for the commits on this branch. The base branch comes from the
arguments; default to the repository's main branch when the arguments name none.

Every claim in the drafted body comes from that output.

## 2. Draft the body

Call the Skill tool with "pr-body" and write the description in its four
sections.

## 3. Check whether you can open a PR

A PR is only possible when all three hold:

- The repository has a remote.
- A forge CLI such as `gh` is installed and authenticated.
- The branch can be pushed.

Check all three before attempting anything. If any fails, don't try.

**When you can**: pushing and opening a PR are both visible to other people, so
confirm with the user first. Then push the branch if it has no upstream and open
the PR with the drafted body, following whatever contribution conventions the
repository documents.

**When you can't**: write the drafted body to `.pr.md` at the repository root.
Ask before overwriting an existing `.pr.md`. Tell the user it's a local draft to
paste when they open the PR themselves.
