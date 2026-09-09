# jstirnaman-skills

Claude Code skills for writing documentation and pull requests.

## Install

```
/plugin marketplace add git@github.com:jstirnaman/skills.git
/plugin install jstirnaman-skills@jstirnaman
```

To work on the plugin locally instead, point Claude Code at a clone:

```
claude --plugin-dir /path/to/skills
```

## Skills

| Skill | Invocation | What it does |
| --- | --- | --- |
| `gdd` | `/gdd [target]` | Rewrites a file, a selection, or inline text in Google developer documentation style. Edits a named file in place. The one you type most. |
| `gdd-style` | automatic, or `/gdd-style` | The style rules themselves. They govern any prose written for a reader, chat replies included, so typing it once turns the style on for as long as the rules stay in context. Claude also loads them on its own when you ask for documentation. |
| `pr-body` | automatic, or `/pr-body` | Structures a PR description as What changed / Why / Impact / Verification. |
| `open-pr` | `/open-pr [base]` | Reads the branch's diff and commit history, drafts the body with `pr-body`, then opens the PR. Writes `.pr.md` instead when no forge CLI is available. |
| `prr` | `/prr [review file or instructions]` | Writes committable GitHub suggestion comments in `prr` reviews. |

`gdd`, `open-pr`, and `prr` set `disable-model-invocation: true`, so they run
only when you invoke them. `open-pr` pushes and opens a PR, which is visible to
other people, so it confirms before it does either.

## License

MIT. See [LICENSE](LICENSE).
