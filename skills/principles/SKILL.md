---
name: principles
description: "Index of Jason Stirnaman's working principles, layered on pstack's. Read at the start of any multi-step task, and before writing or keeping a comment, note, or handoff that states a fact."
---

# Principles

These principles add to pstack's. They don't replace them.

1. If pstack is installed, read the Principles section of its **poteto-mode** skill. Apply its principles as it says.
2. Then apply the principles below. Each entry says when it applies. Read the leaf skill in full before you apply it.
3. In your reply, name each principle that changed a decision, and the decision it changed.

A repository can add its own layer. Its index names this one as its base, and adds only rules that depend on that repository's systems.

## Personal

- **Give Every Fact an Owner** (`principle-give-every-fact-an-owner`). Applies when you write, keep, or review a comment, note, or handoff that states a fact. A fact that nothing keeps true goes stale. Move it to a place with an owner and a source, or encode it as a check. Otherwise, delete it. Extends pstack's **Encode Lessons in Structure**.

## Adding a principle

- Write a leaf skill named `principle-<title>`, with the title in kebab case. Set `disable-model-invocation: true`. This index loads it.
- State the tension it resolves. A principle that doesn't help you choose between two reasonable options is decoration.
- To sharpen one of pstack's principles, write a new leaf that names the one it extends. Don't edit pstack, which syncs from upstream.
- Add one entry here: the name, when it applies, and the rule in one or two sentences.
