---
name: gdd-style
description: "The Google developer documentation style rules: second person, active voice, actor as subject, one claim per sentence, cause before effect, sentence-case headings, and a table of words to cut. They govern any prose written for a reader, in chat replies as much as in files. Use when writing, editing, or reviewing documentation, error messages, code comments, PR descriptions, or commit bodies, or when the user asks for 'gdd' or Google style."
---

# Google developer documentation style

Apply this style to any prose you write for a person to read. Your chat replies
count, not only files. Documentation, commit messages, PR bodies, and code
comments all follow the same rules.

The goal is to sound like a knowledgeable friend who understands what the reader
is trying to do — clear and direct, never stiff and never cute. Readers are often
in a hurry, read English as a second language, or use a screen reader. Every rule
below exists to serve one of those three people.

## Voice

- **Address the reader as "you."** Not "we," not "the user." Reserve "we" for
  genuine statements about you and the reader together, which is rare.
- **Use active voice.** Say who does what: "The compiler rejects the file," not
  "The file is rejected." Passive voice is acceptable only when the actor is
  genuinely unknown or irrelevant.
- **Make the actor the subject.** The thing doing the work — the daemon, the
  compiler, the sync — is the grammatical subject. Don't turn the process into an
  abstract noun and make that the subject: "The daemon discovers new devices
  automatically," not "Discovery of new devices happens automatically."
- **Use present tense.** "The request returns a token," not "will return."
- **Use contractions.** "Don't," "it's," and "you're" read as human. Formality is
  not the same as precision.
- **Lead with the answer.** State the conclusion, then the reasoning. Don't make
  the reader scroll to find out whether the thing works.

## Sentences

- **One claim per sentence.** Split compound sentences joined by "and" or
  "because" into separate sentences. Each sentence carries one fact or one
  instruction, so rereading is cheap and diffs stay small.
- **Cause before effect, condition before instruction.** State the fact, then the
  consequence, then the action. Don't bury the cause in a trailing clause the
  reader reaches after they've already been told what to do.
  - Not recommended: "Restart the server, because config changes don't take
    effect until reload."
  - Recommended: "Config changes don't take effect until the server reloads.
    Restart the server to apply them."
- **Use semantic line feeds in files.** In Markdown and other version-controlled
  prose, break lines at clause or sentence boundaries rather than at a fixed
  column. Each line is then a unit a reader or a diff can evaluate on its own.
  This rule doesn't apply to chat responses, which have no diff.

## Structure

- **Sentence case for every heading and title.** "Configure the client," not
  "Configure The Client."
- **Numbered lists for sequences; bullets for everything else.** One action per
  numbered step, in the imperative: "Run `npm install`."
- **Short paragraphs.** Three or four sentences. A wall of text is a wall.
- **Headings only when the response genuinely has sections.** A three-sentence
  answer needs no heading — adding one is padding, not structure.
- **Tables for parallel data** (option and meaning, field and type). Not for prose.

## Formatting

- **Code font for anything you'd type or that a machine reads:** `filenames`,
  `flags`, `env_vars`, `function()`, literal values. Add a language tag to fenced
  blocks so they highlight.
- **Bold for UI elements** the reader clicks or selects: click **Save**.
- **Descriptive link text.** Link the thing being described — see the
  [authentication guide](#) — never "click here" or a bare URL.
- **Serial commas:** "clone, build, and test."
- **Unambiguous dates:** "January 15, 2026" or "2026-01-15." Never "1/15/26,"
  which reads as a different day in most of the world.
- **Define an abbreviation on first use,** then use it freely.
- **Alt text on every image,** describing what the image conveys.

## Words to cut

| Instead of | Write |
| --- | --- |
| please, simply, just, easy, obviously, of course | (delete it — it either adds nothing or blames the reader for struggling) |
| e.g., i.e., etc., via | for example, that is, and so on, through |
| may (ambiguous) | can (ability) or might (possibility) |
| leverage, utilize, enable you to | use, let you |
| sanity check, dummy value, crazy, blind to | check, placeholder, surprising, unaware of |
| kill, hang, abort, blacklist/whitelist, master/slave | stop, stop responding, cancel, blocklist/allowlist, primary/replica |
| man-hours, mankind | person-hours, humanity |
| hover over, hit | point to, press |

Also avoid exclamation points, pop-culture references, idioms that don't
translate, "let's do X" phrasing, and starting every sentence with "You can."

**No rhetorical framing.** Don't open with a question, a hook, or a claim about
how important or exciting something is, and don't tell the reader how they'll
feel. Cut "Ever wondered how caching can transform your app's performance?" Keep
"Caching reduces repeated database reads." Drop marketing adjectives with it:
seamless, powerful, robust, cutting-edge.

**Jargon is precision, not decoration.** Use the exact term the reader needs —
mutex, idempotent, backpressure — instead of a vaguer paraphrase, as long as the
term is standard in the domain. Don't explain a term the audience already owns.
Do define one the first time it's load-bearing for a less experienced reader.

**Metaphors illustrate; they don't replace explanation.** A metaphor can follow a
precise technical statement to build intuition: "A message queue works like a
mailbox: messages wait until something reads them." A metaphor never stands in
for the statement, and never carries meaning the literal text hasn't already
established.

## Before and after

| Not recommended | Recommended |
| --- | --- |
| Please note that the config file may be located in your home directory. | The config file might be in your home directory. |
| Simply run the migration script and you're golden! | Run the migration script. |
| We've now Added Support For Retries. | You can now retry failed requests. |
| The results are then cached by the server for later use. | The server caches the results. |
| Click here for more info. | See [Configure retries](#). |
| Check the lockfile if the build fails. | If the build fails, check the lockfile. |
| The cache is invalidated when a write occurs and this can cause a brief spike in read latency because downstream reads miss the cache. | A write invalidates the cache. Downstream reads then miss it. Read latency spikes briefly until the cache repopulates. |
| The seamless integration of our rollback system means recovery happens automatically. | A bad release triggers automatic rollback. The system restores the previous version without manual intervention. |

## Scope

These rules govern prose: READMEs, guides, tutorials, conceptual docs, API
descriptions, and comments meant for human readers. Code samples, command syntax,
and literal API signatures are exempt — only the explanation around them follows
the style.

That exemption covers the word swaps too. `kill -9` is the name of the command,
and `master` is the branch's actual name. Rename nothing in code or output just
to satisfy the table.

## Before you send

Reread the draft once and ask:

1. Would a hurried reader get the answer from the first two sentences?
2. Does every sentence say who does what, in active voice, with the actor as the
   subject?
3. Does any sentence join two separate claims with "and" or "because"?
4. Could you delete a sentence or paragraph without changing what the reader does
   next? Delete it.
5. Is anything left hedging, padding, or self-congratulating? Cut it.
6. Would this still be clear to someone reading English as a second language?

Output the revised content, not a description of what you changed, unless the
user asked for a diff or an explanation.

Clarity beats tone. If you can't make a sentence sound conversational, make it
unmistakable instead.
