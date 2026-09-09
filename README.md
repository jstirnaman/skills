# jstirnaman-skills

Skills for Claude Code and Codex that help you write documentation and pull
requests.

## Install

```text
/plugin marketplace add git@github.com:jstirnaman/skills.git
/plugin install jstirnaman-skills@jstirnaman
```

To work on the plugin locally instead, point Claude Code at a clone:

```text
claude --plugin-dir /path/to/skills
```

Codex discovers the plugin's skills from the portable `plugin.json` manifest.
The `.codex-plugin/plugin.json` manifest remains as a Codex compatibility
fallback. Install the plugin through a Codex marketplace, then start a new
thread so Codex loads the updated skill inventory.

## Skills

| Skill | Claude Code | Codex | What it does |
| --- | --- | --- | --- |
| `gdd` | `/gdd [target]` | `$jstirnaman-skills:gdd [target]` | Rewrites a file, a selection, or inline text in Google developer documentation style. Edits a named file in place. The one you type most. |
| `gdd-style` | automatic, or `/gdd-style` | automatic, or `$jstirnaman-skills:gdd-style` | The style rules themselves. They govern any prose written for a reader, chat replies included, so typing it once turns the style on for as long as the rules stay in context. The agent also loads them when you ask for documentation. |
| `pr-body` | automatic, or `/pr-body` | automatic, or `$jstirnaman-skills:pr-body` | Structures a PR description as What changed / Why / Impact / Verification. |
| `open-pr` | `/open-pr [base]` | `$jstirnaman-skills:open-pr [base]` | Reads the branch's diff and commit history, drafts the body with `pr-body`, then opens the PR. Writes `.pr.md` instead when no forge CLI is available. |
| `prr` | `/prr [review file or instructions]` | `$jstirnaman-skills:prr [review file or instructions]` | Writes committable GitHub suggestion comments in `prr` reviews. |

`gdd`, `open-pr`, and `prr` set `disable-model-invocation: true`, so the agent
uses them only when you invoke them. In Codex, skills are not slash commands,
so they do not appear in the command list. `open-pr` pushes and opens a PR,
which is visible to other people, so it confirms before it does either.

## License

MIT. See [LICENSE](LICENSE).
