---
name: gdd-style
description: "Google developer documentation style rules for any prose a person reads, in chat replies as much as in files. Use when writing, editing, or reviewing documentation, error messages, code comments, PR descriptions, or commit bodies, or when the user asks for 'gdd' or Google style."
---

# Google developer documentation style

Apply this style to any prose you write for a person to read.
Your chat replies count, not only files.
Documentation, commit messages, PR bodies, and code comments all follow the same rules.

Write clearly and directly, never stiff and never cute.
Readers often need every technical detail to be exact,
are in a hurry,
read English as a second language,
or use a screen reader.
Every rule below serves one of those four readers.

## Voice

- **Address the reader as "you."**
  Not "we," not "the user."
  Use "we" only for statements about you and the reader together, which are rare.
- **Use active voice.**
  Make the actor the subject:
  "The daemon discovers new devices,"
  not "New devices are discovered" or "Discovery of new devices happens."
  Use passive voice only when the actor is unknown or irrelevant.
  When you revise, don't name a system actor the source doesn't state.
  If you can't tell who acts, keep the passive and flag it for the writer.
  For documentation pages, the write-docs skill says who acts in each content type.
- **Use present tense.**
  "The request returns a token," not "will return."
- **Use contractions.**
  "Don't," "it's," and "you're" read as human.
  Formality isn't the same as precision.
- **Lead with the answer.**
  State the conclusion, then the reasoning.
  Don't make the reader scroll to find out whether the thing works.

## Sentences

- **One claim per sentence.**
  Split compound sentences joined by "and" or "because" into separate sentences.
  Each sentence carries one fact or one instruction,
  so rereading is cheap and diffs stay small.
  Carry the logical link into the new sentence with "so," "as a result," or "that's why."
  Keep each reason attached to the claim it explains.
- **Cause before effect, condition before instruction.**
  State the fact, then the consequence, then the action.
  Don't bury the cause in a trailing clause
  that the reader reaches after you've already told them what to do.
  - Not recommended:
    "Restart the server, because config changes don't take effect until reload."
  - Recommended:
    "Config changes don't take effect until the server reloads.
    Restart the server to apply them."
- **Use semantic line feeds in files.**
  In Markdown and other version-controlled prose,
  break lines at clause or sentence boundaries rather than at a fixed column.
  Each line is then a unit that a reader or a diff can evaluate on its own.
  Chat responses have no diff, so this rule doesn't apply to them.

## Structure and formatting

- **Sentence case for every heading and title.**
  "Configure the client," not "Configure The Client."
- **Code font for anything you'd type or that a machine reads:**
  `filenames`, `flags`, `env_vars`, `function()`, literal values.
  Tag fenced code blocks with a language.
- **Numbered lists for sequences,** one imperative action per step.
  Bullets for everything else.
- **Short paragraphs** of three or four sentences.
- **Headings only when the content has sections.**
  Tables only for parallel data.
- **Bold for UI elements** the reader clicks: click **Save**.
- **Descriptive link text,** never "click here" or a bare URL.
- **Serial commas, unambiguous dates** ("2026-01-15"),
  **abbreviations defined on first use,**
  and **alt text on every image.**

## Words to cut

| Instead of | Write |
| --- | --- |
| please, simply, just, easy, obviously, of course | (delete it: it adds nothing or blames a struggling reader) |
| e.g., i.e., etc., via | for example, that is, and so on, through |
| may (ambiguous) | can (ability) or might (possibility) |
| leverage, utilize, enable you to | use, let you |
| sanity check, dummy value, crazy, blind to | check, placeholder, surprising, unaware of |
| kill, hang, abort, blacklist/whitelist, master/slave | stop, stop responding, cancel, blocklist/allowlist, primary/replica |
| man-hours, mankind | person-hours, humanity |
| hover over, hit | point to, press |

Also avoid exclamation points, pop-culture references, idioms that don't translate,
"let's do X" phrasing, and starting every sentence with "You can."

**No rhetorical framing.**
Don't open with a question, a hook, or a claim about how important something is.
Cut "Ever wondered how caching can transform your app's performance?"
Keep "Caching reduces repeated database reads."
Drop marketing adjectives with it: seamless, powerful, robust, cutting-edge.

**Precision, not decoration.**
Use the exact term the reader needs, such as mutex, idempotent, or backpressure,
instead of a vaguer paraphrase.
The term must be standard in the domain.
Define a term the first time a less experienced reader depends on it.
Qualifiers that bound a claim are precision too:
only, up to, at most, exactly, never, by construction.
Keep them.

**Metaphors follow the literal statement.**
A metaphor can build intuition after a precise technical statement.
It never replaces the statement.

## Before and after

| Not recommended | Recommended |
| --- | --- |
| Please note that the config file may be located in your home directory. | The config file might be in your home directory. |
| Simply run the migration script and you're golden! | Run the migration script. |
| We've now Added Support For Retries. | You can now retry failed requests. |
| Click here for more info. | See [Configure retries](#). |

## Scope

These rules govern prose.
Code samples, command syntax, literal API signatures, and program output are exempt.
The word swaps don't apply to them either:
`kill -9` and a branch named `master` stay as they are.

## Before you send

Reread the draft once and ask:

1. Would a hurried reader get the answer from the first two sentences?
2. Does the draft still break a Voice, Sentences, or Words to cut rule?
3. Could you delete a sentence or paragraph
   without changing what the reader does next?
   Delete it.
4. Would this still be clear to someone reading English as a second language?

Output the revised content, not a description of what you changed,
unless the user asked for a diff or an explanation.

Clarity beats tone.
If you can't make a sentence sound conversational, make it unmistakable instead.

## When you revise existing text

Fidelity beats style.
It serves the reader who needs every detail exact.
Every rule above yields to what the source says.
If a sentence can't follow a rule without changing its meaning, leave it as written.

Before you finish a revision, run a fidelity check:

1. Compare the original and the revision paragraph by paragraph.
2. Confirm that the revision keeps every claim, qualifier,
   number or count, negation, and named audience from the source.
   Confirm that every "because," "so," and "so that" still links the same two ideas,
   and that no stated purpose now reads as a fact.
   Confirm that it adds no claim or system actor the source lacks.
3. Restore anything lost, changed, or added.
4. List for the user any source statements that look wrong or inconsistent.
   Leave the fix to them.

The revision is done when every paragraph passes step 2.
