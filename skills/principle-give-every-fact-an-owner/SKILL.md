---
name: principle-give-every-fact-an-owner
description: "Apply when writing, keeping, or reviewing a comment, note, or handoff that states a fact. Name what keeps the fact true. If nothing does, move it to an owned place or encode it as a check. Otherwise, delete it."
disable-model-invocation: true
---

# Give Every Fact an Owner

A fact being true is not a reason to keep it. A fact that has no owner and no check goes stale without anyone noticing. Readers then trust it after it stops being true.

This resolves a common tension. A comment can be accurate and still be useless. It might help someone, but nothing will update it.

Before you write or keep a fact, ask two questions:

1. **Who updates it when it changes?** A person, a process, or a generator.
2. **What fails when it is wrong?** A test, a type, a lint, or a validator.

If both answers are "nothing," the fact doesn't belong there. In order of preference:

- **Encode it** as a type, test, lint, name prefix, or provenance field, so a wrong fact fails a check. This is pstack's **Encode Lessons in Structure**.
- **Move it** to a place that has an owner and a source. Examples are a reference doc, a claims ledger, a skill, or an issue. Link to it only if a reader needs it to act.
- **Delete it** if it changes nothing a reader does.

## Signs of an unowned fact

- Version and environment notes: "Observed on 3.12.1, may be absent on older servers." The code already handles both cases, so the note changes nothing. If the fact matters, it belongs in the product's docs, with evidence.
- Provenance notes on test data: "RECORDED from a live server" or "PROVISIONAL, not yet observed." The rule they imply, such as "provisional fixtures assert structure, not wording," should be a test. The provenance itself should be a name prefix or a field that the test can read.
- Blanket exceptions, such as "every exported function gets a doc comment." These keep comments whether or not anyone maintains them. An exception has to name the owner, as with a generated API reference built from those comments.

## What this doesn't cover

- Comments that explain behavior forced by something you can't change, such as a vendor bug, a protocol, or a platform. The reason stays true until that external cause changes. Link to the upstream issue so it has an owner.
- Legal and license headers.
