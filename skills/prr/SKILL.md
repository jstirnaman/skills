---
name: prr
description: Write precise, committable GitHub suggestion comments in prr review files. Use when reviewing a pull request with prr or drafting a prr suggestion.
argument-hint: "[review file or instructions]"
disable-model-invocation: true
---

# prr suggestions

A suggestion is an ordinary inline comment whose body contains a GitHub
`suggestion` fenced code block. There is no prr-specific markup: prr uploads
the comment text as-is, and GitHub makes the fence a committable change.

Two things must be right: where the comment is anchored and what goes inside
the fence.

## Anchoring

prr uses blank lines and quoting to decide what a comment attaches to:

- **Inline comment**: Put unquoted text on the line immediately after one
  quoted diff line. The comment attaches to that line.
- **Spanned inline comment**: Put a blank line before the quoted block, then
  put the unquoted comment immediately after its last line. The comment
  attaches to the whole span.

To make a suggestion committable, anchor it to right-side diff lines: added
lines (`+`) or context lines (space). A comment on a removed line (`-`) is on
the old file, so GitHub does not offer **Apply suggestion**.

## Replace one line

Anchor an inline comment to the line to replace. Put the complete replacement,
including indentation, in the fence.

````
> @@ -30,6 +23,11 @@ def handler(req):
>  
> +    timeout = 30
>  

Use the shared constant so this stays in sync with the client.

```suggestion
    timeout = DEFAULT_TIMEOUT
```

>      return call(req, timeout)
````

## Replace several lines

Open a span with a blank line before its quoted block, then close it with the
comment immediately after the block. Put every replacement line in one fence.

````
>  16. Setup

> +asdf
> +asdf
> +asdf

Collapse these into a single call.

```suggestion
    result = do_the_thing()
    return result
```

>  17. Teardown
````

The span covers three lines and the fence contains two, so GitHub replaces the
three with the two.

## Delete lines

An empty fence removes the anchored lines.

````
>  16. Now in order to kill the enemy, our men must be roused to anger.

> +asdf
> +asdf
> +asdf
> +adsf
> +

This text is gibberish. Suggesting removal.

```suggestion
```

>  17. Therefore in chariot fighting, when ten or more chariots have been taken.
````

## Pitfalls

- **Do not quote the fence.** The whole comment, including the fence, stays at
  column 0 with no `> ` prefix. A quoted fence posts but does not render as a
  suggestion.
- **Fence content is literal.** Copy leading whitespace from the diff line,
  excluding the `> ` and the diff-marker column prr adds.
- **Use one fence per comment.** GitHub applies one suggestion per comment;
  write separate comments for separate locations.
- **Snips do not change anchoring.** You can use `[...]` to omit the rest of a
  diff; prr still tracks line positions.

Then submit the review as usual:

```sh
prr submit danobi/prr-test-repo/6
```

The author can apply the suggestion in GitHub or batch it with others.
